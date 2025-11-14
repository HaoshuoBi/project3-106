# Project 3 Writeup  
**Seasonal Greening: Exploring Global Vegetation Change (MODIS NDVI 2024)**

🔗 **Live Website:**  
https://haoshuobi.github.io/project3-106/  

---

## 1. Visualization Design Rationale

Our goal for this project was to explore how global vegetation greenness (NDVI) changes throughout the year and how seasonal patterns differ across regions. We designed an interactive choropleth world map paired with a small trend chart to allow exploration across both spatial and temporal dimensions.

### **Visual Encodings**
- We used a **sequential green color scale** to encode NDVI values from low (brown-green) to high (bright green). This reflects vegetation density intuitively and matches user expectations for environmental data.
- Each country is represented as a filled polygon. Country borders use subtle strokes to avoid drawing attention away from the NDVI values.
- The line chart on the right encodes monthly NDVI using **position** (y-axis) and **connected lines**, which effectively communicates seasonal trends.

### **Data Transformations**
- We cleaned MODIS MOD13C2 NDVI data and aggregated it to **country-level monthly means**.
- The dataset was transformed into a structure mapping each ISO3 country code to an array of 12 monthly values:  
  `iso3 → [NDVI_Jan, NDVI_Feb, ..., NDVI_Dec]`
- Missing months were kept as `null`, allowing them to be represented as “No data” and appear in gray on the map.
- We also performed name/ISO corrections so each TopoJSON country matched our dataset.

### **Interaction Design**
Our interactions were designed to help users discover patterns that would not be obvious in a static plot:

- **Month Slider:** Allows users to see how NDVI changes around the world month by month.
- **Hover Tooltip:** Provides quick access to the exact NDVI value of a country for the selected month.
- **Click Interaction:** Displays a detailed NDVI trend (Jan–Dec) for the chosen country.
- **Pan & Zoom:** Help users focus on a particular region or compare multiple nearby countries.

We considered alternatives such as using a bar chart for the monthly trend or using a diverging color scale, but the selected design better highlights seasonality and supports exploration.

---

## 2. Development Process

### **Team Contributions**

- **Yidong Shi:** Worked on interactive features and debugging—hover tooltips, click-to-view country trends, the month slider, and fixing major ISO3 matching issues. also refined the UI, improved overall map accuracy, and wrote the project’s README.
- **Haoshuo Bi:** Downloaded the 2024 NDVI dataset from NASA MODIS, wrote scripts to aggregate and clean the data at the country level, and built the core D3.js framework of the website — including the initial version of the interactive world map, month slider, country-level line chart, and the dark-theme UI.
- **Yuntao Shan:** Developed and improved the NDVI trend line chart, contributed to layout refinement and visual styling, and assisted with integrating final interactive features. He also revised our checkpoint slides and participated in creating and presenting the checkpoint video.

### **Challenges & Solutions**
One of the biggest challenges was that the original TopoJSON file did not contain reliable ISO3 codes, resulting in many countries displaying “No data.”  
We fixed this by:

1. Manually mapping alternative country names to ISO3 codes, and  
2. Replacing the TopoJSON with an ISO3-complete version that aligned with our dataset.

We also debugged inconsistent NDVI joins using a custom console logging function to identify unmatched countries.

### **Time Spent**
The team spent approximately **15–20 hours** total across:

- Data cleaning and preprocessing  
- Designing interactions  
- Implementing D3 map + chart  
- Debugging ISO3 mismatches  
- Improving UI/UX and polishing styles  
- Creating checkpoint presentation slides
- Preparing, recording, and presenting the checkpoint video

The majority of time was spent debugging interactions and ensuring that NDVI values correctly matched each country.

---

## 3. Creativity and Originality

Our visualization combines:

- A global interactive choropleth map  
- A month slider for seasonal animation  
- A per-country NDVI trend chart  

This hybrid spatial–temporal design allows users to explore vegetation patterns in a way that static charts cannot. The interactivity encourages discovery, such as contrasting northern vs. southern hemisphere seasonality or finding unexpected trends in arid regions.

---

## 4. Summary

The final visualization is functional, polished, and grounded in clear encoding decisions. It allows users to explore seasonal greening at both a global and country level and provides a meaningful way to interpret MODIS NDVI data across 2024.

