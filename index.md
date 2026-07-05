---
layout: home
title: Home
---

## Welcome

I'm a MS EE student at CU Boulder, with focus on embedded systems engineering.

I am looking to be a "jack-of-all-trades" kind of engineer (with focus on FPGA). You will see a reflection of this on the topics I am acquainted on this website:

- _Digital Logic Design with HDL (FPGA, CPLD) (Vivado/Quartus/Libero)_
- _FPGA System Design (Nios II, Microblaze) and Timing Analysis (setup/delay/clock/throughput)_
- _Communication Buses/Protocols (SPI, I2C, Memory Timing)_
- _Signal Integrity (PCB, High Speed Digital), Measurement, and Analysis (Oscope/SigGen/VNA)_
- _Embedded Linux (Buildroot), RTOS, Kernel Programming_
- _Microprocessor programming (Bare-metal/Vendor-IDE) and IoT Protocols (Bluetooth/MQTT)_
- _Higher Level Programming (C++/Boost, Python)_

All class-related projects shared on this site either have Instructor approval, or are Individual/Group projects that doesn't reveal Instructor's IP on coursework.

{% assign featured = site.projects | where: "featured", true %}
{% if featured.size > 0 %}
## Featured Articles

<div class="featured-carousel">
  <button class="carousel-btn" id="carousel-prev" onclick="carouselMove(-1)">&#8592;</button>

  <div class="carousel-track">
    {% for item in featured %}
    <a class="carousel-card{% if forloop.first %} active{% endif %}" href="{{ item.url | relative_url }}">
      <h2>{{ item.title }}</h2>
      {% if item.description %}<p class="featured-desc">{{ item.description }}</p>{% endif %}
    </a>
    {% endfor %}
  </div>

  <button class="carousel-btn" id="carousel-next" onclick="carouselMove(1)">&#8594;</button>
</div>

{% if featured.size > 1 %}
<div class="carousel-dots">
  {% for item in featured %}
  <span class="carousel-dot{% if forloop.first %} active{% endif %}" onclick="carouselGoto({{ forloop.index0 }})"></span>
  {% endfor %}
</div>
{% endif %}

<script>
  var current = 0;
  var cards = document.querySelectorAll('.carousel-card');
  var dots = document.querySelectorAll('.carousel-dot');

  function carouselShow(index) {
    cards.forEach(function(c) { c.classList.remove('active'); });
    dots.forEach(function(d) { d.classList.remove('active'); });
    cards[index].classList.add('active');
    if (dots[index]) dots[index].classList.add('active');
    current = index;
  }

  function carouselMove(dir) {
    carouselShow((current + dir + cards.length) % cards.length);
  }

  function carouselGoto(index) {
    carouselShow(index);
  }
</script>
{% endif %}

## Topics

<div class="topic-grid">
  <a class="topic-card" href="{{ '/projects/cu-boulder-embedded/' | relative_url }}">
    <h2>CU Boulder Projects</h2>
    <p>Embedded systems course projects with reports and writeups</p>
  </a>
  <a class="topic-card" href="{{ '/projects/ecen5730-pcb/' | relative_url }}">
    <h2>ECEN5730: PCB Design</h2>
    <p>Schematic capture, layout, routing, and fabrication</p>
  </a>
  <a class="topic-card" href="{{ '/projects/ecen5224-high-speed-digital/' | relative_url }}">
    <h2>ECEN5224: High Speed Digital</h2>
    <p>Signal integrity, transmission lines, EMC</p>
  </a>
  <a class="topic-card" href="{{ '/projects/ecen5863-fpga/' | relative_url }}">
    <h2>ECEN5863: FPGA System Design</h2>
    <p>HDL, synthesis, soft-core CPUs, AXI peripherals</p>
  </a>
  <a class="topic-card" href="{{ '/projects/photography/' | relative_url }}">
    <h2>Photography</h2>
    <p>Landscape, street, and portrait photography</p>
  </a>
  <a class="topic-card" href="{{ '/projects/quantitative-finance/' | relative_url }}">
    <h2>Quantitative Finance</h2>
    <p>Equity research, sector modeling, and derivatives</p>
  </a>
</div>