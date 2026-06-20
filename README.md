# Data Science Project - Wine Quality Prediction

## 📋 Overview

This is an **end-to-end Data Science project** that implements a complete Machine Learning pipeline with cloud deployment capabilities. The project predicts wine quality based on physicochemical features using a supervised learning approach with a web-based user interface.

**Primary Use Case**: Wine Quality Classification  
**Target Variable**: Quality Score (0-10)  
**Deployment**: Flask-based REST API with HTML web interface

---

## 📊 Project Architecture

### Tech Stack
- **Languages**: Python (22.7%), Jupyter Notebook (73.8%), HTML (3.5%)
- **ML/Data Processing**: scikit-learn, pandas, numpy, matplotlib
- **Experiment Tracking**: MLflow, DagsHub
- **Web Framework**: Flask, Flask-Cors
- **Configuration Management**: PyYAML, python-box
- **Serialization**: joblib

### Project Structure

```
datascienceproject/
├── src/datascience/              # Main source code directory
│   ├── pipeline/
│   │   ├── data_ingestion_pipeline.py
│   │   ├── data_validation_pipeline.py
│   │   ├── data_transformation_pipeline.py
│   │   ├── model_trainer_pipeline.py
│   │   ├── model_evaluation_pipeline.py
│   │   └── prediction_pipeline.py
│   └── ...
├── config/                        # Configuration files
├── research/                      # Jupyter notebooks for experimentation
├── templates/                     # HTML templates for Flask web app
├── app.py                         # Flask application
├── main.py                        # ML pipeline execution
├── requirements.txt               # Python dependencies
├── schema.yaml                    # Data schema definition
├── params.yaml                    # Model hyperparameters
├── config.yaml                    # Pipeline configuration
├── Dockerfile                     # Container configuration
└── template.py                    # Project structure generator
```

---

## 🔄 ML Pipeline Workflow

The project follows a modular, production-ready ML pipeline architecture:

### 1. **Data Ingestion**
   - Loads raw wine quality dataset
   - Data source integration
   - Initial data exploration

### 2. **Data Validation**
   - Schema validation against `schema.yaml`
   - Data type checking
   - Missing value detection
   - Quality assurance checks

### 3. **Data Transformation**
   - Feature Engineering
   - Data Preprocessing
   - Scaling/Normalization
   - Train-test split

### 4. **Model Training**
   - Supervised learning model training
   - Hyperparameter configuration via `params.yaml`
   - Cross-validation
   - Model persistence with joblib

### 5. **Model Evaluation**
   - Performance metrics calculation
   - MLflow experiment tracking
   - DagsHub integration for reproducibility
   - Model versioning

---

## 📈 Dataset Features

The model predicts wine quality based on **11 physicochemical features**:

| Feature | Type | Description |
|---------|------|-------------|
| fixed acidity | float64 | Fixed acids in wine |
| volatile acidity | float64 | Volatile acids (acetic acid) |
| citric acid | float64 | Citric acid content |
| residual sugar | float64 | Sugar remaining after fermentation |
| chlorides | float64 | Salt content |
| free sulfur dioxide | float64 | Free SO₂ concentration |
| total sulfur dioxide | float64 | Total SO₂ concentration |
| density | float64 | Wine density |
| pH | float64 | Acidity level |
| sulphates | float64 | Sulfates concentration |
| alcohol | float64 | Alcohol content (%) |

**Target Variable**: `quality` (int64) - Quality score of the wine

---

## 🚀 How to Use

### Prerequisites
- Python 3.8+
- pip or conda package manager

### Installation

```bash
# Clone the repository
git clone https://github.com/KirankumarDhanireddy/datascienceproject.git
cd datascienceproject

# Install dependencies
pip install -r requirements.txt
```

### Configuration

Before running the pipeline, update these YAML files:

1. **config.yaml** - Pipeline configuration
2. **schema.yaml** - Data schema definition
3. **params.yaml** - Model hyperparameters

```bash
# Update configuration files
nano config.yaml
nano schema.yaml
nano params.yaml
```

### Training the Model

```bash
# Execute the complete ML pipeline
python main.py
```

This runs all 5 stages sequentially:
- Data Ingestion → Data Validation → Data Transformation → Model Training → Model Evaluation

### Running the Web Application

```bash
# Start the Flask application
python app.py
```

The application will be available at: `http://0.0.0.0:8080`

**Web Interface Routes**:
- `/` - Home page
- `/train` - Trigger model training
- `/predict` - Wine quality prediction form

### Making Predictions

The prediction pipeline accepts 11 input features:
- Input: Array of 11 physicochemical measurements
- Output: Predicted quality score
- Processing: Automatic preprocessing and scaling

```python
from src.datascience.pipeline.prediction_pipeline import PredictionPipeline

# Create prediction object
predictor = PredictionPipeline()

# Make prediction (11 features)
data = [[7.4, 0.7, 0.0, 1.9, 0.076, 11.0, 34.0, 0.9978, 3.51, 0.56, 9.4]]
prediction = predictor.predict(data)
print(f"Predicted Quality: {prediction}")
```

---

## 🔧 Development Workflow

For adding new features or improvements:

1. **Update config.yaml** - Define new configuration parameters
2. **Update schema.yaml** - Add new features/validation rules if needed
3. **Update params.yaml** - Modify hyperparameters
4. **Update entity** - Add new data structures in the entity layer
5. **Update configuration manager** - Add new config managers in `src/config/`
6. **Update components** - Implement feature-specific logic
7. **Update pipeline** - Integrate components into the pipeline
8. **Update main.py** - Add new pipeline stages if needed

---

## 📊 Experiment Tracking

This project integrates **MLflow** and **DagsHub** for:
- Experiment tracking and comparison
- Hyperparameter logging
- Metrics visualization
- Model versioning and registry
- Reproducibility and collaboration

```bash
# View MLflow experiments
mlflow ui
```

---

## 🐳 Containerization

Deploy the application using Docker:

```bash
# Build the Docker image
docker build -t wine-quality-predictor .

# Run the container
docker run -p 8080:8080 wine-quality-predictor
```

---

## 📝 Dependencies

Key Python packages:
- `pandas` - Data manipulation and analysis
- `numpy` - Numerical computing
- `scikit-learn` - Machine learning algorithms
- `matplotlib` - Data visualization
- `mlflow` - Experiment tracking
- `Flask` - Web framework
- `PyYAML` - YAML configuration handling
- `joblib` - Model persistence
- `notebook` - Jupyter support

See `requirements.txt` for complete list.

---

## 🤝 Contributing

To contribute improvements:

1. Create a feature branch
2. Make your changes
3. Test thoroughly with the validation stage
4. Update configuration files if needed
5. Submit a pull request

---

## 📄 License

This project is open source and available under the appropriate license. See LICENSE file for details.

---

## 👤 Author

**Kiran Kumar Dhanireddy**

GitHub: [@KirankumarDhanireddy](https://github.com/KirankumarDhanireddy)

---

## 🎯 Future Enhancements

- [ ] Add more dataset sources
- [ ] Implement advanced feature engineering techniques
- [ ] Multi-model ensemble approach
- [ ] Real-time prediction API
- [ ] Automated model retraining pipeline
- [ ] CI/CD integration
- [ ] Kubernetes deployment configuration
- [ ] Advanced monitoring and alerting

---

## 📞 Support

For issues, feature requests, or questions, please open an issue on GitHub.

