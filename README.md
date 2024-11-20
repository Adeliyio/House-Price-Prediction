# House Price Prediction Production Ready Microservice

## Overview

This project implements an end-to-end, production-ready microservice for predicting house prices based on property features. It uses a trained **RandomForest** model and exposes a **Flask API** that enables users to input property details and receive real-time price predictions.

The purpose of this project is to demonstrate the process of transforming machine learning models into operational microservices that can be easily integrated into production environments.

## Key Features

- **Machine Learning Model**: A RandomForest model trained to predict house prices based on features such as area, construction year, number of bedrooms, and more.
- **Flask API**: A lightweight web server built using Flask that supports both **GET** and **POST** requests to receive property details and return price predictions.
- **Real-time Prediction**: Users can submit property details via URL query parameters or JSON body and receive price predictions instantly.
- **Data Validation**: Inputs are validated using **Pydantic** to ensure that the data conforms to the expected schema before being passed to the model.

## Technologies Used

- **Flask**: A micro web framework for building and serving the API.
- **Pydantic**: A data validation library used to ensure data integrity for incoming requests.
- **Scikit-Learn (v1.3.1)**: A Python library used to build the machine learning model.
- **Python 3.10.15**: The programming language used to implement both the microservice and the machine learning model.

## Setup & Installation

Follow these steps to run the project locally:

### 1. Clone the Repository
Clone the repository and navigate to the app directory:
```bash
git clone https://github.com/Adeliyio/House-Price-Prediction.git
cd House-Price-Prediction/app
```
### 2. Set Up a Virtual Environment (Optional but recommended)
```
Create a virtual environment and activate it:
python -m venv venv
source venv/bin/activate  # For MacOS/Linux
venv\Scripts\activate     # For Windows
```
### 3. Install Dependencies
If you're using Poetry to manage dependencies, run the following:
```
poetry install
```
### 4. Run the Flask Application
Start the Flask server:
```
python run.py

This will start the server at http://127.0.0.1:5000.
```
### 5. Access the API
You can now interact with the prediction API via a browser or a tool like Postman or cURL.
```
GET Request Example:
bash
Copy code
http://127.0.0.1:5000/pred/?area=1200&construction_year=2000&bedrooms=3&garden_area=50&balcony_present=1&parking_present=1&furnished=1&garage_present=0&storage_present=1
POST Request Example:
bash
Copy code
curl -X POST http://127.0.0.1:5000/pred/ -H "Content-Type: application/json" -d '{
  "area": 1200,
  "construction_year": 2000,
  "bedrooms": 3,
  "garden_area": 50,
  "balcony_present": 1,
  "parking_present": 1,
  "furnished": 1,
  "garage_present": 0,
  "storage_present": 1
}'
```
### 6. View the Prediction
The API will return a JSON object with the predicted price:
```
json
Copy code
{
  "prediction": 450000.0
}
API Endpoints
1. GET /pred/
Retrieve a house price prediction based on query parameters.

Request Parameters:
area: int (e.g., 1200)
construction_year: int (e.g., 2000)
bedrooms: int (e.g., 3)
garden_area: int (e.g., 50)
balcony_present: int (1 or 0)
parking_present: int (1 or 0)
furnished: int (1 or 0)
garage_present: int (1 or 0)
storage_present: int (1 or 0)
2. POST /pred/
Retrieve a house price prediction based on JSON data provided in the body of the request.

Request Body:
json
Copy code
{
  "area": 1200,
  "construction_year": 2000,
  "bedrooms": 3,
  "garden_area": 50,
  "balcony_present": 1,
  "parking_present": 1,
  "furnished": 1,
  "garage_present": 0,
  "storage_present": 1
}
Running the Model in Production
This microservice is designed to be easily deployable in production environments. Here are the steps to prepare the service for deployment:
```

## Prediction Result

Here is an example of the prediction result:

![Prediction Result](https://github.com/Adeliyio/House-Price-Prediction/raw/main/prediction.jpg)

### 7. Dockerize the Application (Optional)
To containerize the application:
```
Create a Dockerfile in the root directory.
Build the Docker image:
bash
Copy code
docker build -t house-price-prediction .
Run the Docker container:
bash
Copy code
docker run -p 5000:5000 house-price-prediction
Deploy on Cloud
You can deploy this application to cloud platforms such as:

AWS EC2
Google Cloud Run
Heroku
Contributing
If you'd like to contribute to this project:
```

All contributions are welcome!
