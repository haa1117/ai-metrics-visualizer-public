# Privacy and Source

## Source availability

The source code (`app.py`, configuration files, and styles) is private. This repository contains portfolio documentation, screenshots and design references only. The analysis directory is not included in the public repository.

## Demo data

All metrics, trends, and comparison data shown in screenshots and dashboards are fictional and generated synthetically:
- Fidelity and compression metrics are hard-coded constants.
- Time-series chart data is drawn from `np.random.normal()` each session.
- No real AI model performance data, user information, or proprietary datasets are included.

Hiring managers and clients can evaluate the UI/UX design, visualization patterns, and technical approach without exposure to sensitive implementation details.

## Third-party assets and licenses

The dashboard uses open-source libraries under standard permissive licenses:
- **Streamlit:** Apache License 2.0
- **Plotly:** MIT License
- **Pandas, NumPy:** BSD-3-Clause License
- **Inter font:** (embedded in CSS; font-family fallback to system sans-serif if unavailable)

Logos, branding, and original artwork are owned by their respective creators. No proprietary assets are redistributed.

## Configuration and secrets

No credentials, API keys, database connection strings, or sensitive environment variables are stored in this repository. The application has no runtime dependencies on external services.

Screenshots use the built-in demo dashboard interface. No personal data, real user information, or third-party integrations appear in any image.
