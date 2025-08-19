# 🌸 Iris Flower Classification — FastAPI ML Inference

## 📝 Problem Description
The goal of this project is to classify iris flowers into one of three species:
- Setosa  
- Versicolor  
- Virginica  

based on four flower measurements:
- Sepal length (cm)  
- Sepal width (cm)  
- Petal length (cm)  
- Petal width (cm)  

---

## 🤖 Model Choice Justification
We use **Logistic Regression** inside a scikit-learn **Pipeline** with `StandardScaler`:
- Works very well for small, structured datasets like Iris.  
- Simple, fast, and interpretable model.  
- Achieves ~96–97% accuracy on test data.  
- Provides probability estimates (`predict_proba`) so we can report prediction confidence.  

---

## 📡 API Usage Examples

### 1. Health check
`GET /`  

Example response:
```json
{
  "status": "healthy",
  "message": "Iris API running"
}

2. Predict a single flower

POST /predict
request body:

{
  "sepal_length": 5.1,
  "sepal_width": 3.5,
  "petal_length": 1.4,
  "petal_width": 0.2
}
Response:
{
  "prediction": "setosa",
  "confidence": 0.99
}

3. Model info

GET /model-info

Example response:

{
  "model_type": "LogisticRegression (with StandardScaler)",
  "features": ["sepal_length","sepal_width","petal_length","petal_width"],
  "class_names": ["setosa","versicolor","virginica"],
  "metrics": {"accuracy": 0.9667}
}

4. Bonus: Batch prediction

POST /predict-batch

Request:

{
  "items": [
    {"sepal_length": 5.1, "sepal_width": 3.5, "petal_length": 1.4, "petal_width": 0.2},
    {"sepal_length": 6.2, "sepal_width": 3.4, "petal_length": 5.4, "petal_width": 2.3}
  ]
}


Response:

{
  "predictions": [
    {"prediction": "setosa", "confidence": 0.99},
    {"prediction": "virginica", "confidence": 0.97}
  ]
}


