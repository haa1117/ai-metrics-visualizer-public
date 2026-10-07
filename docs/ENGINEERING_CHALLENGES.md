# Engineering Challenges

## Python version compatibility

**Problem:** The original `requirements.txt` pinned outdated versions:
- `streamlit==1.32` (released early 2024)
- `pandas<2` and `numpy<1.25`

These constraints fail on Python 3.13+, which was released in October 2024. Users on modern Python interpreters encounter unresolved dependency errors during environment setup.

**Mitigation:** The code is forward-compatible and runs unmodified on Streamlit 1.45+, Plotly 5.24+, and current NumPy/Pandas. Setting up a venv with Python 3.12 and `pip install streamlit pandas numpy plotly` works immediately. Long-term, pinned versions should be updated or removed.

## Synthetic data regeneration

**Problem:** The trend chart uses `np.random.normal()` to generate daily fidelity and compression data. On each page load or rerun, new random values generate, creating inconsistent chart state that may confuse users expecting persistence.

**Mitigation:** For a portfolio demo, this is acceptable; the chart always renders visually similar trends. For production use, seed the random generator or load historical data from a database.

## Animation timing and perception

**Problem:** A 5–8 second load animation may feel slow on mobile or slow networks. The metric counter animation uses `time.sleep()` in a tight loop, blocking Streamlit's rendering until complete.

**Mitigation:** Streamlit's `@st.cache_resource` could defer the animation to a single run, but the app remains demo-focused. For production, Streamlit's session state can track animation state and render incrementally without blocking.

## CSS coverage

The dashboard uses vendor-prefixed CSS (`-webkit-background-clip`, `-webkit-text-fill-color`) for compatibility with WebKit browsers (Chrome, Safari, Edge). Firefox support is present but gradient text may render less smoothly. This is a known limitation of CSS gradients on text.

## Deprecation warning

Streamlit 1.36+ deprecated the `use_container_width` parameter on `st.plotly_chart()`. The app logs a harmless warning but continues to function. Future refactors should use the `use_container_width` option in chart config instead.
