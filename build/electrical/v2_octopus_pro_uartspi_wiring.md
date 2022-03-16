---
layout: default
title: "Voron V2 - BTT Octopus Pro V1.0 (in SPI Mode) Wiring"
nav_exclude: true
---

<button class="btn js-toggle-light-mode">Use voron-light color scheme</button>

# Voron V2 - BTT Octopus Pro V1.0 Wiring
{:.no_toc}


## Table of Contents
{:.no_toc}

<details open markdown="block">
  <summary>
    <span class="fs_percent_150">Click, "▼", to Close the Table of Contents</span>
  </summary>
  {: .text-delta }

1. TOC
{:toc}
</details>


## What is the difference between UART mode and SPI mode?
{:.no_toc}

* This stuff refers to the way the hardware communicates. SPI is significantly faster than UART. In some cases, an SPI solution can be three times faster than a UART solution. 

* So, how do you know which mode to pick? It depends on the stepper motor drivers you choose to buy with the Octopus Pro board.  The list below shows which stepper motor drivers are UART mode and which are SPI mode.

<details open markdown="block">

<summary>
        <span class="fs_percent_125">Click, "▼", to Close UART Mode (TMC2208, TMC2209, TMC2225, or TMC2226)</span>
</summary>

{% include_relative /v2_octopus_pro_uart_wiring.md %}

</details>

<div markdown="1">


</div>

---

<details>
 
<summary>
    <span class="fs_percent_125">Click, "►", to Open SPI Mode (TMC2100, TMC2130, TMC5160, or TMC5161)</span>
</summary>

<div markdown="1">
 
{% include_relative /v2_octopus_pro_spi_wiring.md %}
 
</div>

</details>

<script>
const toggleLightMode = document.querySelector('.js-toggle-light-mode');

jtd.addEvent(toggleLightMode, 'click', function(){
  site_color2 = jtd.getTheme();
  if (site_color2 === 'voron_light') {
    jtd.setTheme('voron_dark');
    toggleLightMode.textContent = 'Use voron-light color scheme';
    console.log(" The site_color2 = voron_dark" );
  } else {
    jtd.setTheme('voron_light');
    console.log("The site_color2 = voron_light");
    toggleLightMode.textContent = 'Return to the voron-dark side';
  }
});
</script>
