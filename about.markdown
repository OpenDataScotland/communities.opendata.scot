---
layout: default
title: About
permalink: /about/
---

<div class="container py-5">
  <div class="row">
    <div class="col-lg-8">
      <h1>About Open Data Scotland Communities</h1>
      
      <p class="lead">Welcome to the central directory for open data communities and events across Scotland. Our mission is to connect like-minded individuals, organizations, and groups who are passionate about open data and its potential to drive innovation, transparency, and positive change.</p>
      
      <h2>What We Do</h2>
      
      <p>This platform serves as a comprehensive directory where you can:</p>
      
      <ul>
        <li><strong>Discover Local Communities:</strong> Find open data user groups, meetups, and organizations in your area</li>
        <li><strong>Stay Updated on Events:</strong> Keep track of upcoming conferences, workshops, hackathons, and networking events</li>
        <li><strong>Connect with Peers:</strong> Meet fellow data enthusiasts, researchers, developers, and civic tech advocates</li>
        <li><strong>Share Your Events:</strong> Promote your own open data initiatives and gatherings</li>
      </ul>
      
      <h2>Our Vision</h2>
      
      <p>We envision a thriving open data ecosystem in Scotland where:</p>
      
      <div class="row mt-4">
        <div class="col-md-6">
          <div class="card h-100">
            <div class="card-body">
              <h5 class="card-title"><i class="bi bi-lightbulb text-primary"></i> Innovation Flourishes</h5>
              <p class="card-text">Open data drives innovation across sectors, from startups to established organizations.</p>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <div class="card h-100">
            <div class="card-body">
              <h5 class="card-title"><i class="bi bi-people text-primary"></i> Communities Thrive</h5>
              <p class="card-text">Active, inclusive communities share knowledge and collaborate on open data projects.</p>
            </div>
          </div>
        </div>
      </div>
      
      <div class="row mt-3 mb-4">
        <div class="col-md-6">
          <div class="card h-100">
            <div class="card-body">
              <h5 class="card-title"><i class="bi bi-graph-up text-primary"></i> Skills Develop</h5>
              <p class="card-text">Regular events and workshops help build data literacy and technical skills.</p>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <div class="card h-100">
            <div class="card-body">
              <h5 class="card-title"><i class="bi bi-shield-check text-primary"></i> Transparency Increases</h5>
              <p class="card-text">Public and private organizations embrace open data principles for greater accountability.</p>
            </div>
          </div>
        </div>
      </div>
      
      <h2>Get Involved</h2>
      
      <p>We're always looking for ways to grow and improve this directory. Here's how you can contribute:</p>
      
      <div class="row mt-3">
        <div class="col-md-4">
          <div class="text-center">
            <i class="bi bi-plus-circle text-primary" style="font-size: 3rem;"></i>
            <h5 class="mt-2">Add Your Community</h5>
            <p>Help others discover your open data community or user group.</p>
          </div>
        </div>
        <div class="col-md-4">
          <div class="text-center">
            <i class="bi bi-calendar-plus text-primary" style="font-size: 3rem;"></i>
            <h5 class="mt-2">Share Events</h5>
            <p>Promote your meetups, conferences, and workshops to reach a wider audience.</p>
          </div>
        </div>
        <div class="col-md-4">
          <div class="text-center">
            <i class="bi bi-github text-primary" style="font-size: 3rem;"></i>
            <h5 class="mt-2">Contribute Code</h5>
            <p>Help improve this website by contributing to our open source project.</p>
          </div>
        </div>
      </div>
      
      <div class="mt-4">
        <a href="https://github.com/OpenDataScotland/communities.opendata.scot" class="btn btn-primary me-3">
          <i class="bi bi-github"></i> View on GitHub
        </a>
        <a href="https://github.com/OpenDataScotland/communities.opendata.scot/issues/new" class="btn btn-outline-primary">
          <i class="bi bi-plus-circle"></i> Suggest Improvements
        </a>
      </div>
    </div>
    
    <div class="col-lg-4">
      <div class="card">
        <div class="card-header">
          <h5 class="card-title mb-0">Quick Stats</h5>
        </div>
        <div class="card-body">
          <div class="row text-center">
            <div class="col-6">
              <h3 class="text-primary">{{ site.communities.size }}</h3>
              <small class="text-muted">Communities</small>
            </div>
            <div class="col-6">
              <h3 class="text-primary">{{ site.events.size }}</h3>
              <small class="text-muted">Events</small>
            </div>
          </div>
        </div>
      </div>
      
      <div class="card mt-4">
        <div class="card-header">
          <h5 class="card-title mb-0">Contact Us</h5>
        </div>
        <div class="card-body">
          <p>Have questions or suggestions? We'd love to hear from you!</p>
          <ul class="list-unstyled">
            <li><i class="bi bi-envelope"></i> <a href="mailto:{{ site.email }}" class="text-decoration-none">{{ site.email }}</a></li>
            <li><i class="bi bi-github"></i> <a href="https://github.com/{{ site.github_username }}" class="text-decoration-none">@{{ site.github_username }}</a></li>
            <li><i class="bi bi-twitter"></i> <a href="https://twitter.com/{{ site.twitter_username }}" class="text-decoration-none">@{{ site.twitter_username }}</a></li>
          </ul>
        </div>
      </div>
      
      <div class="card mt-4">
        <div class="card-header">
          <h5 class="card-title mb-0">Open Source</h5>
        </div>
        <div class="card-body">
          <p>This website is built with:</p>
          <ul class="list-unstyled">
            <li><i class="bi bi-gem text-danger"></i> Jekyll</li>
            <li><i class="bi bi-bootstrap text-primary"></i> Bootstrap 5</li>
            <li><i class="bi bi-github text-dark"></i> GitHub Pages</li>
          </ul>
          <p>All code is available under the MIT license.</p>
        </div>
      </div>
    </div>
  </div>
</div>
