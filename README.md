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

### **Overview of the Team’s Development Process**

We first registered for NASA Earthdata access and downloaded all twelve 2024 MOD13C2 HDF files.  After setting up a conda environment, we wrote a Python script that extracted each month’s NDVI data, computed country-level averages, matched ISO3 codes, and exported a clean, unified CSV.  Additional cleaning and formatting were finished in Jupyter Notebook, producing the final dataset used in our visualization.

With the data prepared, we built the website structure and implemented the core D3.js components: the world map, color scale, month slider, zoom/pan, and the click-to-view country trend chart. A large portion of the development involved debugging incorrect country matches in the TopoJSON. In the "Challenges & Solutions" section later on, we elaborated in detail on the problems we encountered and how we solved them.

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

