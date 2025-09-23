
---

## Contents

### 1. `Direct_Graph/`
- **Direct_Graph.html**: The main offline HTML file.  
  It visualizes entity relationships in a force-directed network graph.
- **README.md**: Instructions on how to run this graph, dataset format, and example screenshots.

### 2. `data/`
- **relationships_min.csv**: Minimal dataset with `source,target,value`.  
  Used to demonstrate high-confidence vs low-confidence edges (`value=0` → solid gray, `value=1` → dashed green).
- **relationships_extended.csv**: Richer dataset with additional fields (relation type, direction, confidence, evidence counts, etc.).  
  Useful for experimenting with advanced edge styling and filtering.

### 3. `lib/`
- Contains `d3.v5.min.js` (minified version of D3.js v5).  
  This allows the visualizations to run fully offline, without requiring a CDN.

### 4. `images/`
- **initial.png**: Screenshot of the initial auto-positioned graph layout.  
- **pinned.png**: Screenshot showing a pinned node (`Project Orion` fixed in yellow).

---

## How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/jasonpark9001/Visualization.git
   cd Visualization/visualization
