# Direct Graph Visualization (Offline D3 v5)

This project demonstrates a **force-directed graph** built with [D3.js v5](https://d3js.org/), running fully offline in a single HTML file (`Direct_Graph.html`). It visualizes relationships extracted between entities (people, organizations, locations, assets) similar to what is used in a Named Entity Recognition (NER) + Relation Extraction pipeline.

---

## How to Run

1. Make sure you have Python installed.
2. Open a terminal in the project root (where `Direct_Graph.html` lives inside `/notebooks/`).  
3. Start a local server:
   ```bash
   python -m http.server 8002
   ```
4. In your browser, go to:
   ```
   http://localhost:8002/Direct_Graph/Direct_Graph.html
   ```

If D3 is not pasted in yet, the page will display a yellow banner with instructions. Paste the full `d3.v5.min.js` into the HTML (as indicated in the file) to make it fully self-contained.

---

## Dataset

The dataset is provided in `relationships_min.csv` (or inlined in the HTML as a fallback).  
It has the following schema:

| Column  | Description |
|---------|-------------|
| source  | Starting entity (person, org, location, or object) |
| target  | Connected entity |
| value   | Relationship confidence flag <br> `0 = high confidence (solid gray edge)` <br> `1 = lower confidence (dashed green edge)` |

Example rows:

```csv
Alice Johnson,Northwind Logistics,0
Bob Smith,Harbor Terminal 7,1
Acme Chemicals,Device ZX-13,0
Device ZX-13,Project Orion,1
```

---

## Output Explanation

When opened in the browser, the force-directed layout produces a dynamic network visualization:

- **Nodes** represent entities such as **people** (`Alice Johnson`), **organizations** (`Northwind Logistics`), **projects** (`Project Orion`), **locations** (`Harbor Terminal 7`), and **objects** (`Device ZX-13`).
- **Edges** represent extracted relationships:
  - **Solid gray lines** (`value=0`): high-confidence relations
  - **Dashed green lines** (`value=1`): lower-confidence relations
- **Node size and color intensity** scale with the **degree** (number of connections).  
  Larger, darker blue nodes are more central with more links.
- **Interactive features**:
  - Dragging a node **pins** it in place (highlighted in **yellow**).
  - Double-clicking a pinned node **unpins** it so it moves freely again.

### Example Views

Initial layout (nodes auto-positioned):  
![Initial Graph Layout](images/initial.png)

After dragging/pinning `Project Orion`:  
![Pinned Graph Layout](images/pinned.png)

In the example above:
- `Project Orion`, `Northwind Logistics`, and `Harbor Terminal 7` appear as **larger, darker nodes** because they have more connections.
- Pinning `Project Orion` (yellow node) fixes its position, making the network easier to interpret.

---

## Use Case

This visualization approach can be used in your NLP/NER + Relation Extraction workflows to:
- Explore connections between entities found in reports.
- Spot **key hubs** (entities with many links).
- Investigate **uncertain relations** (dashed green lines) for manual review.
- Present findings to analysts in an interactive, intuitive graph.

---

## Author

Visualization adapted from CSE 6242 homework, extended for NLP relationship extraction.  
Maintained by Jason Park (`JPARK3146`).
