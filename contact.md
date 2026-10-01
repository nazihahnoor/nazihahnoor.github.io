---
layout: page
title: Contact
subtitle: The best ways to reach me.
permalink: /contact/
---

I'm happy to hear from fellow researchers, journalists, students, and anyone whose work touches on health, inequality, or policy. The best channels are listed below. I try to reply within a week.

<ul class="contact-list">
  <li>
    <span class="contact-label">Email</span>
    <span class="contact-value"><a href="mailto:{{ site.email }}">{{ site.email }}</a></span>
  </li>
  {% if site.linkedin %}
  <li>
    <span class="contact-label">LinkedIn</span>
    <span class="contact-value"><a href="{{ site.linkedin }}">{{ site.linkedin | remove: 'https://' | remove: 'http://' }}</a></span>
  </li>
  {% endif %}
  {% if site.google_scholar %}
  <li>
    <span class="contact-label">Google Scholar</span>
    <span class="contact-value"><a href="{{ site.google_scholar }}">Profile</a></span>
  </li>
  {% endif %}
  {% if site.orcid %}
  <li>
    <span class="contact-label">ORCID</span>
    <span class="contact-value"><a href="{{ site.orcid }}">{{ site.orcid | remove: 'https://orcid.org/' }}</a></span>
  </li>
  {% endif %}
  <li>
    <span class="contact-label">Affiliation</span>
    <span class="contact-value">Department of Community Health, University of Fribourg, Switzerland</span>
  </li>
</ul>
