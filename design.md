# Visualization Design: Geographical Map of Episode Activity and Death Distribution

## Goal
To visualize:
1. **The geographical repartition of episode activity** (number of scenes per location).
2. **The death repartition among the places** (number of deaths per location).

The visualization allows users to filter data over time using:
- **GoT Years** (e.g., 298 AC to 305 AC).
- **Season, Episode, Scene** granularity.

---

## 1. Visual Mapping Table (Card & Mackinlay Style)

| **Name**            | **D** | **F**    | **D’** | **X**      | **Y**      | **Z**       | **T**       | **R** | **—** | **[]**             | **CP**                    |
|----------------------|-------|----------|--------|------------|------------|-------------|-------------|-------|-------|--------------------|---------------------------|
| **Location**         | N     | >        |   N     | P   | P   |             |             |       |       |                    | Geographical location on the GoT map. |
| **Number of Scenes** | Q     | >        |    Q    |            |            |            |             |  Size     |       | Tooltip on hover            | Circle size proportional to scene counts.   |
| **Number of Deaths** | Q     | >        |        |            |            |             |            |    C   |       | Tooltip on hover            | Circle color intensity (white → red) proportional to deaths count. |
| **Time Period**      | Q   | sl>      |        |            |            |             |             |       |       | Slider (Granular)  | Two modes: GoT Years or Seasons/Episodes/Scenes. |
| **Details**          | Q/N     | Textual display      |        |            |            |             |             |       |       | Click Tooltip| Location name, total scenes, deaths, notable events. |

---

## 2. Design Rationale

### Global Insights: Scene Activity
- **Circle Size** encodes the number of scenes, providing a clear overview of the most active locations.
- This helps answer: *"What is the geographical repartition of episode's activity?"*

### Subset Comparison: Death Distribution
- **Circle Color** (light → dark red) encodes the number of deaths at each location, allowing comparison of death intensity.
- This addresses: *"What are the death repartition among the places the show takes place in?"*

### Smooth Transition
- The visualization remains unified but provides a shift in focus:  
   - **Global Insights**: Scene activity (circle size).  
   - **Subset Comparison**: Death intensity (circle color).

---

## 3. Interaction Description

### Time Mode Toggle
- A **toggle button** allows switching between:
   - **GoT Years**: Filters data by a continuous range of years (298 AC to 305 AC).  
   - **Season, Episode, Scene**: Filters data by season, episodes within seasons, or specific scenes.

### Time Slider
- **GoT Years Mode**:
   - Slider range: 298 AC → 305 AC.  
   - Filters map data to display activity and deaths within the selected year range.
- **Season Mode**:
   - Granularity levels:  
      - **Seasons** (e.g., S1 → S8).  
      - **Episodes** (e.g., E1, E2).  
      - **Scenes** (specific scenes).  
   - Filters map data to reflect activity and deaths within the chosen season/episode/scene range.

### Map Interactions
1. **Hover**:
   - Displays a tooltip with:
     - Location name.
     - Total number of scenes.
     - Total number of deaths.
     - Notable characters who died (if applicable).
2. **Click**:
   - Highlights the location.
   - Opens a **side panel** with detailed stats:
     - Scene breakdown by episode/season.
     - Death details (e.g., who, when, and how).

### Legend
- **Size Legend**: Represents the scale of scene counts.  
- **Color Legend**: Represents the gradient of death intensity (light → dark red).

---

## 4. Sketch Overview

### Default View (Global Insights)
- A map with:
   - Circle **size** encoding the number of scenes.
   - Circle **color** subtly indicating deaths.
   - **Time slider** at the bottom for filtering.

### Filtered View (Time Selection Applied)
- When a time range is selected:
   - Circle sizes update based on scene counts in the chosen period.
   - Circle colors update to reflect deaths in the chosen period.

### Detailed View (Subset Comparison)
- Clicking a location zooms in and opens a side panel with:
   - Total number of scenes.
   - Total number of deaths.
   - List of episodes and characters associated with the location.

### Time Slider (Mode Switching)
1. **GoT Years Mode**: Continuous range from 298 AC → 305 AC.  
2. **Season Mode**: Granularity adjusts to:
   - **Seasons** (e.g., S1, S2).  
   - **Episodes** (e.g., E1, E2).  
   - **Scenes** (finest granularity).

---

## 5. Tools and Implementation Notes
- **D3.js**: For creating the interactive geographical map and time slider.  
- **Data Files**:
   - `scenes.tsv`: For scenes and locations.  
   - `scenes_characters.tsv`: For character deaths in specific scenes.  
   - `episodes.tsv`: For season, episode, and year mapping.  
- **Slider**: Use a custom slider library (e.g., **d3-simple-slider**) for dynamic range control.  
- **Side Panel**: Built with HTML/CSS to display detailed statistics for selected locations.

---

## 6. Summary
This single interactive visualization:
- Combines **global insights** (scene activity) and **comparisons** (death distribution).
- Allows users to explore data dynamically with two time modes:
   - GoT Years.  
   - Seasons/Episodes/Scenes.
- Provides smooth transitions and rich interactivity to gain insights at multiple levels of detail.

---

