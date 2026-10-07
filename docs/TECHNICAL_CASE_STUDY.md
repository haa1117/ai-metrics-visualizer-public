# Technical Case Study

## Challenge: Present static data as engaging, "live" UI

The core design goal was to create a marketing dashboard that *felt* real-time without backend infrastructure. Metrics had to animate on load, charts had to render smoothly, and the overall aesthetic needed to signal technical sophistication and polish.

## Approach

### Animated counters
Instead of displaying 99.3 instantly, the app increments from 0 to 0.993 in 25 steps over 1.875 seconds. Each step updates a Streamlit placeholder:
```python
for i in range(1, steps + 1):
    current = (value * i) / steps
    placeholder.markdown(f"<div class='metric-card'>{format(current)}</div>", unsafe_allow_html=True)
    time.sleep(0.075)
```
This technique is simple but effective; the visual feedback suggests data is being computed in real time.

### CSS-driven typography
The intro text uses CSS keyframe animations to type out "AI" and "Metrics" sequentially, with a blinking cursor. All timing and positioning is calculated with CSS custom properties and animation delays, avoiding Python logic.

### Dual-axis charting
The performance chart tracks two metrics on different scales (fidelity: 0.97–1.0; compression: 4–11.3). Plotly's `yaxis2` parameter overlays a second y-axis on the right, allowing both trends to render clearly on one chart without normalization.

### Responsive layout
Streamlit columns and `use_container_width=True` ensure the dashboard adapts to desktop and mobile viewport sizes. The Plotly chart automatically reflows; CSS media queries are not needed.

## Outcome

Page load is animated over ~5–8 seconds (counters + progress + CSS animations complete sequentially). The final render is fully interactive: users can pan, zoom, and hover on the chart; the design conveys a polished, production-ready application.

All logic is contained in a single ~430-line file, making it trivial to fork, extend, or repurpose as a template.
