---
layout: default
title: Events
permalink: /events/
---

<div class="container py-5">
  <div class="row">
    <div class="col-12">
      <h1 class="mb-4">Open Data Events in Scotland</h1>
      <p class="lead">Discover upcoming meetups, conferences, workshops, and other open data events happening across Scotland.</p>
    </div>
  </div>
  
  <div class="search-filters">
    <div class="row">
      <div class="col-md-6">
        <input type="text" class="form-control" id="eventSearch" placeholder="Search events...">
      </div>
      <div class="col-md-3">
        <select class="form-select" id="typeFilter">
          <option value="">All Types</option>
          <option value="meetup">Meetup</option>
          <option value="conference">Conference</option>
          <option value="workshop">Workshop</option>
          <option value="hackathon">Hackathon</option>
          <option value="webinar">Webinar</option>
        </select>
      </div>
      <div class="col-md-3">
        <select class="form-select" id="statusFilter">
          <option value="">All Events</option>
          <option value="upcoming">Upcoming</option>
          <option value="past">Past</option>
        </select>
      </div>
    </div>
  </div>
  
  <div class="event-grid" id="eventGrid">
    {% assign sorted_events = site.events | sort: 'date' | reverse %}
    {% for event in sorted_events %}
    {% assign current_date = site.time | date: "%Y-%m-%d" %}
    {% assign event_date = event.date | date: "%Y-%m-%d" %}
    {% if event_date >= current_date %}
      {% assign is_upcoming = true %}
    {% else %}
      {% assign is_upcoming = false %}
    {% endif %}
    <div class="event-card" data-type="{{ event.event_type | default: '' }}" data-status="{% if is_upcoming %}upcoming{% else %}past{% endif %}" data-title="{{ event.title | downcase }}" data-description="{{ event.description | default: '' | downcase }}">
      <div class="card h-100">
        <div class="card-body">
          <div class="d-flex justify-content-between align-items-start mb-2">
            <h5 class="card-title">
              <a href="{{ event.url | relative_url }}" class="text-decoration-none">{{ event.title }}</a>
            </h5>
            {% if is_upcoming %}
              <span class="badge bg-success">Upcoming</span>
            {% else %}
              <span class="badge bg-secondary">Past</span>
            {% endif %}
          </div>
          
          {% if event.description %}
            <p class="card-text">{{ event.description | truncate: 120 }}</p>
          {% endif %}
          
          <div class="mb-3">
            {% if event.date %}
              <div class="text-muted mb-1">
                <i class="bi bi-calendar"></i> {{ event.date | date: "%B %d, %Y" }}
                {% if event.time %}
                  at {{ event.time }}
                {% endif %}
              </div>
            {% endif %}
            {% if event.location %}
              <div class="text-muted mb-2">
                <i class="bi bi-geo-alt"></i> {{ event.location }}
              </div>
            {% endif %}
            
            {% if event.event_type %}
              <span class="badge bg-primary">{{ event.event_type }}</span>
            {% endif %}
            {% if event.tags %}
              {% for tag in event.tags %}
                <span class="badge bg-secondary">{{ tag }}</span>
              {% endfor %}
            {% endif %}
          </div>
        </div>
        <div class="card-footer bg-transparent">
          <div class="d-flex justify-content-between align-items-center">
            <small class="text-muted">
              {% if event.organizer %}
                By {{ event.organizer }}
              {% endif %}
            </small>
            <div>
              {% if event.registration_url and is_upcoming %}
                <a href="{{ event.registration_url }}" target="_blank" class="btn btn-primary btn-sm me-2">
                  <i class="bi bi-person-plus"></i> Register
                </a>
              {% endif %}
              <a href="{{ event.url | relative_url }}" class="btn btn-outline-primary btn-sm">Details</a>
            </div>
          </div>
        </div>
      </div>
    </div>
    {% endfor %}
  </div>
  
  {% if site.events.size == 0 %}
  <div class="row">
    <div class="col-12">
      <div class="card text-center">
        <div class="card-body py-5">
          <i class="bi bi-calendar-event" style="font-size: 4rem; color: #6c757d;"></i>
          <h3 class="mt-3">No Events Added Yet</h3>
          <p class="lead">Be the first to add an open data event to our directory!</p>
          <a href="https://github.com/OpenDataScotland/communities.opendata.scot" class="btn btn-primary">
            <i class="bi bi-plus-circle"></i> Add an Event
          </a>
        </div>
      </div>
    </div>
  </div>
  {% endif %}
</div>

<script>
// Simple search and filter functionality
document.addEventListener('DOMContentLoaded', function() {
  const searchInput = document.getElementById('eventSearch');
  const typeFilter = document.getElementById('typeFilter');
  const statusFilter = document.getElementById('statusFilter');
  const eventCards = document.querySelectorAll('.event-card');
  
  function filterEvents() {
    const searchTerm = searchInput.value.toLowerCase();
    const selectedType = typeFilter.value;
    const selectedStatus = statusFilter.value;
    
    eventCards.forEach(card => {
      const title = card.dataset.title;
      const description = card.dataset.description;
      const type = card.dataset.type;
      const status = card.dataset.status;
      
      const matchesSearch = !searchTerm || title.includes(searchTerm) || description.includes(searchTerm);
      const matchesType = !selectedType || type === selectedType;
      const matchesStatus = !selectedStatus || status === selectedStatus;
      
      card.style.display = matchesSearch && matchesType && matchesStatus ? 'block' : 'none';
    });
  }
  
  searchInput.addEventListener('input', filterEvents);
  typeFilter.addEventListener('change', filterEvents);
  statusFilter.addEventListener('change', filterEvents);
});
</script>