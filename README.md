Council Request Classifier Project for BCIT601

API uses FastAPI, joblib and Scikit-learn. See API/requirements.txt for exact requirements.

#To run:
Run server with "python -m uvicorn main:app" or from API folder; use "py" in place of python if that alias is set.
To shutdown:
Press ctrl+c

#API endpoints.

/health returns "status": "ok" if model is loaded
/categories returns "category_list": [] with list of model categories
/predict is used to submit requests for predictions. Able to perform standard string cleaning.
POST Json {“request_text”:”request”}
Returns{“request_text”:”request”,
        “predicted_category”:”category”,
        “confidence”:confidence,
        “confidence_rank”:”confidence_rank”,
        “needs_review”:bool,
        “review_reason”:null or “review_reason”
        }


#View endpoints
To view API endpoints Open localhost:8000/docs
To view predict endpoint with a browser ensure LOCAL_TESTING is set to true in api\main.py and
open use_predict_api.html


#Automated Testing:
run "python -m pytest -q" in terminal from project root folder

#Model training:
To retrain the model, open training/ModelTraining.py
Ensure model_type is selected and run_final_model_training is True; then run file
Additional parameters can be set, such as new training data. Parameters and defaults are listed
under if run_final_model_training.

Copy vectoriser.joblib and model.joblib files over to model folder and ensure they are named as such.

#Training experimentation:
Machine learning model has been extensively tested in training folder.
Advanced testing runs a LOOCV
Parameter testing produces a .csv with comparative result of common vectoriser parameters.
