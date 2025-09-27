---
layout: default
---

<div class="hero-section">
  <div class="container">
    <div class="row align-items-center">
      <div class="col-lg-8">
        <h1>Open Data Communities in Scotland</h1>
        <p class="lead">Discover local meetups, conferences, user groups, and organizations promoting open data initiatives across Scotland. Connect with like-minded individuals and contribute to Scotland's open data ecosystem.</p>
        <div class="mt-4">
          <a href="{{ "/communities/" | relative_url }}" class="btn btn-light btn-lg me-3">
            <i class="bi bi-people"></i> Browse Communities
          </a>
          <a href="{{ "/events/" | relative_url }}" class="btn btn-outline-light btn-lg">
            <i class="bi bi-calendar-event"></i> View Events
          </a>
        </div>
      </div>
      <div class="col-lg-4 text-center">
        <i class="bi bi-database" style="font-size: 8rem; opacity: 0.7;"></i>
      </div>
    </div>
  </div>
</div>

<div class="container py-5">
  <div class="row">
    <div class="col-lg-6 mb-5">
      <h2><i class="bi bi-people-fill text-primary"></i> Featured Communities</h2>
      <p>Connect with active open data communities across Scotland.</p>
      
      {% assign featured_communities = site.communities | where: "featured", true | limit: 3 %}
      {% if featured_communities.size > 0 %}
        <div class="row g-3">
          {% for community in featured_communities %}
          <div class="col-12">
            <div class="card">
              <div class="card-body">
                <h5 class="card-title">
                  <a href="{{ community.url | relative_url }}" class="text-decoration-none">{{ community.title }}</a>
                </h5>
                <p class="card-text">{{ community.description | truncate: 100 }}</p>
                {% if community.location %}
                  <small class="text-muted"><i class="bi bi-geo-alt"></i> {{ community.location }}</small>
                {% endif %}
              </div>
            </div>
          </div>
          {% endfor %}
        </div>
      {% else %}
        <div class="card">
          <div class="card-body text-center">
            <p class="card-text">No communities have been added yet. Check back soon!</p>
            <a href="https://github.com/OpenDataScotland/communities.opendata.scot" class="btn btn-outline-primary">
              <i class="bi bi-plus-circle"></i> Add a Community
            </a>
          </div>
        </div>
      {% endif %}
      
      <div class="mt-3">
        <a href="{{ "/communities/" | relative_url }}" class="btn btn-primary">View All Communities</a>
      </div>
    </div>
    
    <div class="col-lg-6 mb-5">
      <h2><i class="bi bi-calendar-event-fill text-primary"></i> Upcoming Events</h2>
      <p>Don't miss these upcoming open data events in Scotland.</p>
      
      {% assign current_date = site.time | date: "%Y-%m-%d" %}
      {% assign upcoming_events = site.events | sort: "date" %}
      {% assign filtered_events = "" | split: "" %}
      {% for event in upcoming_events %}
        {% assign event_date = event.date | date: "%Y-%m-%d" %}
        {% if event_date >= current_date %}
          {% assign filtered_events = filtered_events | push: event %}
        {% endif %}
      {% endfor %}
      {% assign upcoming_events = filtered_events | slice: 0, 3 %}
      {% if upcoming_events.size > 0 %}
        <div class="row g-3">
          {% for event in upcoming_events %}
          <div class="col-12">
            <div class="card">
              <div class="card-body">
                <h5 class="card-title">
                  <a href="{{ event.url | relative_url }}" class="text-decoration-none">{{ event.title }}</a>
                </h5>
                <p class="card-text">{{ event.description | truncate: 100 }}</p>
                <div class="d-flex justify-content-between align-items-center">
                  <small class="text-muted">
                    <i class="bi bi-calendar"></i> {{ event.date | date: "%B %d, %Y" }}
                  </small>
                  {% if event.location %}
                    <small class="text-muted"><i class="bi bi-geo-alt"></i> {{ event.location }}</small>
                  {% endif %}
                </div>
              </div>
            </div>
          </div>
          {% endfor %}
        </div>
      {% else %}
        <div class="card">
          <div class="card-body text-center">
            <p class="card-text">No upcoming events have been added yet. Check back soon!</p>
            <a href="https://github.com/OpenDataScotland/communities.opendata.scot" class="btn btn-outline-primary">
              <i class="bi bi-plus-circle"></i> Add an Event
            </a>
          </div>
        </div>
      {% endif %}
      
      <div class="mt-3">
        <a href="{{ "/events/" | relative_url }}" class="btn btn-primary">View All Events</a>
      </div>
    </div>
  </div>
  
  <div class="row">
    <div class="col-12">
      <div class="text-center py-5">
        <h2>Get Involved</h2>
        <p class="lead">Help us build Scotland's open data community directory</p>
        <div class="row justify-content-center">
          <div class="col-md-4 mb-3">
            <div class="card h-100">
              <div class="card-body text-center">
                <i class="bi bi-plus-circle text-primary" style="font-size: 3rem;"></i>
                <h5 class="card-title mt-3">Add Your Community</h5>
                <p class="card-text">Register your open data community or user group to connect with others.</p>
              </div>
            </div>
          </div>
          <div class="col-md-4 mb-3">
            <div class="card h-100">
              <div class="card-body text-center">
                <i class="bi bi-calendar-plus text-primary" style="font-size: 3rem;"></i>
                <h5 class="card-title mt-3">Submit Events</h5>
                <p class="card-text">Share your open data events, meetups, and conferences with the community.</p>
              </div>
            </div>
          </div>
          <div class="col-md-4 mb-3">
            <div class="card h-100">
              <div class="card-body text-center">
                <i class="bi bi-github text-primary" style="font-size: 3rem;"></i>
                <h5 class="card-title mt-3">Contribute</h5>
                <p class="card-text">Help improve this directory by contributing to the project on GitHub.</p>
              </div>
            </div>
          </div>
        </div>
        <div class="mt-4">
          <a href="https://github.com/OpenDataScotland/communities.opendata.scot" class="btn btn-outline-primary btn-lg">
            <i class="bi bi-github"></i> View on GitHub
          </a>
        </div>
      </div>
    </div>
  </div>
</div>
