---
name: Homework 5
tools: [Python, HTML, vega-lite]
image: assets/pngs/UFO.png
description: This is the Jekyll page for my HW5 submission
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

## Overview

An exploration of 80,000+ UFO sighting reports spanning from the early 1900s to 2014.

<a href="https://raw.githubusercontent.com/L4M315/L4M315.github.io/refs/heads/main/assets/hw/hw5/ufo-scrubbed-geocoded-time-standardized-00.csv" class="btn" style="display:inline-block; padding:8px 16px; background:#4c78a8; color:white; text-decoration:none; border-radius:4px; margin-right:8px;">Data</a>
<a href="https://github.com/L4M315/L4M315.github.io/blob/main/assets/hw/hw5/ufo_analysis.ipynb" class="btn" style="display:inline-block; padding:8px 16px; background:#333; color:white; text-decoration:none; border-radius:4px;">Analysis</a>

---

## First plot, static


I wanted to create something that looks like the 
[Sighting Time, Seasonally plot from this inforgraph](https://www.flerlagetwins.com/2017/02/ufo-sightings-of-2016-recreation-of_99.html).

<vegachart schema-url="{{ site.baseurl }}/assets/hw/hw5/heatmap.json" style="width: 100%"></vegachart>

#### Description

The goal of this heatmap is to show how UFO sightings distribute across hours of the day for each month. 
Each cell represents the percentage of that month's sightings occurring at a given hour. 
A bar chart above summarizes the overall hourly distribution.

#### Design Choices: Encodings

The x-axis encodes the hours of day (0–23), and the y-axis encodes the months.
The bar chart on top uses bar height to encode the total sighting count per hour, 
giving an aggregate view alongside the detailed heatmap.

#### Design Choices: Colormaps

Originally, I wanted this whole page to be in green, because green is linked in my head with aliens. 
Green is not a colorblind-friendly color, so I decided to switch it for blue. 
I also added the percentages inside the cells and had them switch their color between black/white 
based on the color of the cell to improve readability.

#### Transformations

I extracted the hour and month from each datetime, then grouped by month and hour to count reports.
I then normalized each month's counts into percentages (each row sums to 100%), 
which allows for fair comparison across months regardless of how many total sightings each month has.
Without this normalization, summer months would dominate simply due to higher volume, 
hiding the time-of-day pattern.



---

## Second plot, interactive

**Interactivity**: Toggle between the Dot (each sighting as a dot) or the State view. 
Drag the slider to show different decades.

<vegachart schema-url="{{ site.baseurl }}/assets/hw/hw5/us_map.json" style="width: 100%"></vegachart>

#### Description

The interactive map shows the distribution of UFO sightings across the United States, 
with cumulative data by decade. The slider shows how sightings 
accumulated from the 1910s through the 2010s. A dropdown toggles between two views: 
"Dots" shows individual sighting locations as points on a dark map, while "States" 
shows a choropleth where each state is shaded by its total sighting count.

#### Design Choices: Encodings

**In Dots mode,** each circle's position encodes latitude and longitude, 
circle size encodes the number of sightings at that location 
(using a square root scale to prevent large values from dominating), 
and the neon green color was chosen for high contrast against the black map.

**In States mode,** the fill color of each state encodes its cumulative sighting count 
using a sequential blue scale with a square root transform. 

Both modes use tooltips to show exact counts on hover.

#### Design Choices: Colormaps

For the Dots mode, I wanted it to look like the space pictures they take of Earth at night. 
I chose neon green here because green is linked to aliens in my head. For the States mode, I initially went with green here too, but switched it to blue to become 
colorblind-friendly. This color map uses a square root scale to compress the range and 
reveal differences among lower-count states.

#### Transformations

I enriched the original dataset using the `reverse_geocoder` library to fill in 
missing country codes from latitude/longitude coordinates, then filtered to US-only sightings.
I rounded coordinates to one decimal place and aggregated sighting counts, 
reducing 70,000+ individual records to a manageable set of location points. 
I then aggregated sighting counts per state per cumulative 
decade so each state's shading reflects all sightings up to the selected decade.