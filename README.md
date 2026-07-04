# 🏎️ British GP Predictor: Mission Control

A professional-grade, F1-inspired predictive analytics dashboard designed to forecast the outcomes of the British Grand Prix. 

Built with **FastAPI**, **XGBoost**, and **FastF1**, this project features a high-performance "Mission Control" data visualization system that prioritizes clarity, role-aware information architecture, and actionable storytelling.

## ✨ Features

- **Mission Control Dashboard**: A custom-designed, night-race themed UI featuring glassmorphism, dynamic telemetry load states, and micro-animations.
- **80/20 Rule UX**: Highlights only the top 20% podium favorites to reduce cognitive load while maintaining a high-density data table for deeper engineering analysis.
- **Advanced Machine Learning**: Uses `XGBoost` for both classification (podium finish probability) and regression (estimated grid finish).
- **Model Persistence**: Implements an efficient `joblib`-based caching system that trains the model once and reloads it instantly on subsequent runs, bypassing heavy data fetching.
- **Docker-Ready**: Comes fully containerized with an optimized `Dockerfile` for easy PaaS deployment.

## 🚀 Quick Start (Local)

### Prerequisites
- Python 3.11+
- Git

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/priyanshi-100506/british-f1-race-predictor.git
   cd british-f1-race-predictor
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Start the FastAPI server:
   ```bash
   uvicorn main:app --reload
   ```

4. Open your browser and navigate to `http://127.0.0.1:8000`.

*(Note: The very first time the server starts, it will download historical F1 telemetry via FastF1 and train the ML models. This may take 15-30 seconds. Subsequent requests and restarts will be near-instant thanks to model persistence!)*

## 🐳 Deployment (Docker)

This application is ready to be deployed to any containerized platform (like Render, Railway, AWS, or GCP) out-of-the-box.

1. Build the Docker image:
   ```bash
   docker build -t f1-predictor .
   ```
2. Run the container:
   ```bash
   docker run -p 8000:8000 f1-predictor
   ```

## 🧠 Model Validation

If you want to manually validate the model's performance metrics or force a retraining outside of the web server:

```bash
# Validate the currently cached model
python validate.py

# Force retrain the models with fresh telemetry
python validate.py --retrain
```
