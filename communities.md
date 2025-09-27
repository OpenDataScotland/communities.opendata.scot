---
layout: default
title: Communities
permalink: /communities/
---

<div class="container py-5">
  <div class="row">
    <div class="col-12">
      <h1 class="mb-4">Open Data Communities in Scotland</h1>
      <p class="lead">Connect with local open data communities, user groups, and organizations across Scotland.</p>
    </div>
  </div>
  
  <div class="search-filters">
    <div class="row">
      <div class="col-md-8">
        <input type="text" class="form-control" id="communitySearch" placeholder="Search communities...">
      </div>
      <div class="col-md-4">
        <select class="form-select" id="locationFilter">
          <option value="">All Locations</option>
          <option value="Edinburgh">Edinburgh</option>
          <option value="Glasgow">Glasgow</option>
          <option value="Aberdeen">Aberdeen</option>
          <option value="Dundee">Dundee</option>
          <option value="Stirling">Stirling</option>
          <option value="Online">Online</option>
        </select>
      </div>
    </div>
  </div>
  
  <div class="community-grid" id="communityGrid">
    {% for community in site.communities %}
    <div class="community-card" data-location="{{ community.location | default: '' }}" data-title="{{ community.title | downcase }}" data-description="{{ community.description | default: '' | downcase }}">
      <div class="card h-100">
        <div class="card-body">
          <h5 class="card-title">
            <a href="{{ community.url | relative_url }}" class="text-decoration-none">{{ community.title }}</a>
          </h5>
          {% if community.description %}
            <p class="card-text">{{ community.description | truncate: 120 }}</p>
          {% endif %}
          <div class="mb-3">
            {% if community.location %}
              <span class="badge bg-primary"><i class="bi bi-geo-alt"></i> {{ community.location }}</span>
            {% endif %}
            {% if community.tags %}
              {% for tag in community.tags %}
                <span class="badge bg-secondary">{{ tag }}</span>
              {% endfor %}
            {% endif %}
          </div>
        </div>
        <div class="card-footer bg-transparent">
          <div class="d-flex justify-content-between align-items-center">
            <small class="text-muted">
              {% if community.website %}
                <a href="{{ community.website }}" target="_blank" class="text-decoration-none">
                  <i class="bi bi-globe"></i> Website
                </a>
              {% endif %}
            </small>
            <a href="{{ community.url | relative_url }}" class="btn btn-outline-primary btn-sm">Learn More</a>
          </div>
        </div>
      </div>
    </div>
    {% endfor %}
  </div>
  
  {% if site.communities.size == 0 %}
  <div class="row">
    <div class="col-12">
      <div class="card text-center">
        <div class="card-body py-5">
          <i class="bi bi-people" style="font-size: 4rem; color: #6c757d;"></i>
          <h3 class="mt-3">No Communities Added Yet</h3>
          <p class="lead">Be the first to add an open data community to our directory!</p>
          <a href="https://github.com/OpenDataScotland/communities.opendata.scot" class="btn btn-primary">
            <i class="bi bi-plus-circle"></i> Add a Community
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
  const searchInput = document.getElementById('communitySearch');
  const locationFilter = document.getElementById('locationFilter');
  const communityCards = document.querySelectorAll('.community-card');
  
  function filterCommunities() {
    const searchTerm = searchInput.value.toLowerCase();
    const selectedLocation = locationFilter.value;
    
    communityCards.forEach(card => {
      const title = card.dataset.title;
      const description = card.dataset.description;
      const location = card.dataset.location;
      
      const matchesSearch = !searchTerm || title.includes(searchTerm) || description.includes(searchTerm);
      const matchesLocation = !selectedLocation || location === selectedLocation;
      
      card.style.display = matchesSearch && matchesLocation ? 'block' : 'none';
    });
  }
  
  searchInput.addEventListener('input', filterCommunities);
  locationFilter.addEventListener('change', filterCommunities);
});
</script>