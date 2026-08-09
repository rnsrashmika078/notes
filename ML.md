# SETPS TO CREATE MACHINE LEARNING PIPELINE

🚀 1. Create Azure ML Workspace
    Go to Azure Portal → Search Azure Machine Learning
    Click Create → New Workspace
    Fill:
    Subscription, Resource Group, Name, Region
    Keep defaults (Storage, Key Vault auto-created)
    Select Public Network Access
    Click Create → Launch Studio
💻 2. Create Compute Resource
    Click + Compute
    Create/select a compute instance (VM)
    Use it to run notebooks or pipelines
📓 3. Use Notebooks
    Open Notebooks
    Upload/run .ipynb files
    Attach compute to execute code
📊 4. Create Dataset
    Go to Data → + Create
    Select Tabular Data
    Choose From Web URL
    Paste dataset link
    Keep default settings → Create

## PIPELINE STARTS FROM HERE

🧹 5. Data Preprocessing ( Component: Clean Missing Data)
    Add Clean Missing Data
    Connect dataset → Clean Missing Data Component
    Choose method: mean / median / mode ( for categorical : mode , for numerical : mean / median) -> use separate Clean Missing Data components

🎯 6. Feature Selection ( Component: Select Columns in Dataset)
    Add Select Columns in Dataset
    Connect cleaned data
    Select required columns (or all)

🔀 7. Split Dataset ( Component: Split Data )
    Add Split Data
    Connect selected dataset
    Set:
        0.7 → Training
        0.3 → Testing
🤖 8. Choose Algorithm
    Add ML algorithm:
        Binary → ( Component: Two-Class Boosted Decision Tree ) ( if target column has only two label = [YES,NO])
        Multiclass → ( Component:  Multiclass Decision Forest ) ( if target column have  more than 2 label)
        Regression → ( Component:  Linear Regression )  ( if target column values are numbers , continues values )
🏋️ 9. Train Model
    Add Train Model ( Component: Train Model )
    Connect:
        Algorithm → Train Model
        Training data → Train Model
    Select target (label) column
📈 10. Score Model ( Component : Score Model )
    Add Score Model
    Connect:
        Trained model
        Test data
📊 11. Evaluate Model ( Component : Evaluate model )
    Add Evaluate Model
    Connect from Score Model
    View metrics:
        Accuracy, Precision, Recall, F1-score
⚙️ 12. Run Pipeline
    Click Submit
    Create/select compute cluster
    Run pipeline
📦 13. Check Results
    Go to Jobs
    Monitor training progress
    Use model for prediction/deployment
🔥 Algorithm Selection (Quick)
    Yes/No → Binary Classification
    Apple/Orange → Multiclass
    Numbers (25.3) → Regression