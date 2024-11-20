# House Price Prediction Microservice

## Overview

This project is an end-to-end, production-ready microservice for predicting house prices based on property features. It uses RandomForest and exposes a Flask API that enables seamless communication between the user and the model, allowing for real-time price predictions.

The goal of this project is to demonstrate the process of transforming machine learning models into operational microservices that can be easily integrated into a production environment. 

## Key Features

- **Machine Learning Model**: A trained RandomForest model that predicts house prices based on features like area, construction year, number of bedrooms, and more.
- **Flask API**: A simple yet efficient Flask-based web server that accepts GET and POST requests to receive property details and return price predictions.
- **Real-time Prediction**: Users can submit data (via URL query parameters or JSON body) and receive accurate price predictions instantly.
- **Validation**: Inputs are validated using Pydantic, ensuring the data conforms to the expected schema before being processed by the model.

## Technologies Used

- **Flask**: Lightweight web framework for building and serving the API.
- **Pydantic**: Data validation for incoming requests to ensure the integrity of input data.
- **Scikit-Learn 1.3.1**: Python library used to build the machine learning model for price prediction.
- **Python 3.10.15**: The programming language used for implementing the microservice and machine learning model.


## Setup & Installation

Follow these steps to get the project running locally:

### 1. Clone the Repository
```bash
git clone https://github.com/Adeliyio/House-Price-Prediction.git
cd app
2. Set Up a Virtual Environment (Optional but recommended)
bash
Copy code
python -m venv venv
source venv/bin/activate  # For MacOS/Linux
venv\Scripts\activate     # For Windows
3. Install Dependencies
using poetry:

4. Run the Flask Application
Once everything is set up, you can run the Flask app using the following command:

bash
Copy code
python app.py
This will start the Flask server on http://127.0.0.1:5000.

5. Access the API
You can now interact with the prediction API via your browser or a tool like Postman or curl.

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
6. View the Prediction
The API will return a JSON object with the predicted price, for example:

json
Copy code
{
  "prediction": 450000.0
}
API Endpoints
1. GET /pred/
Description: Retrieve a prediction for house price based on the query parameters.
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
Description: Retrieve a prediction for house price based on the provided JSON data.
Request Body: JSON object containing the same fields as the GET request parameters.
Example:
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
This microservice is designed to be easily deployable in any production environment. It can be containerized using Docker and deployed to platforms like AWS, Azure, or Google Cloud. The following steps can be taken to prepare it for production deployment:

Dockerize the Application (Optional):

Create a Dockerfile to package the application.
Build and run the Docker container using docker build and docker run.
Deploy on Cloud:

You can deploy the Flask application to cloud platforms like AWS EC2, Google Cloud Run, or Heroku.
Contributing
If you would like to contribute to this project, feel free to fork the repository, create a branch, and submit a pull request. All contributions are welcome!