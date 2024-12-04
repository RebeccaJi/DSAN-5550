# Predicting Urban Heat Island Intensity

### **Description**

This project focuses on predicting Urban Heat Island (UHI) intensity using geospatial and environmental data. It integrates multiple datasets (e.g., land temperature, carbon budget, and population data) and employs machine learning models to make accurate predictions. The project aims to provide insights for sustainable urban planning and climate impact mitigation.

### **Problem Definition**

Urban Heat Islands (UHIs) are areas where urban temperatures are significantly higher than surrounding rural areas. This phenomenon contributes to climate challenges by increasing energy demand, deteriorating air quality, and exacerbating health risks. The project addresses the following objectives:

-   Predict UHI intensity using satellite and meteorological data.

-   Analyze the relationship between UHI intensity and factors such as population, land use, and emissions.

-   Provide actionable insights for urban planning and policy-making.

### **Data Collection and Refinement**

The **Urban Heat Island (UHI) Dataset** was sourced from NASA\'s Socioeconomic Data and Applications Center (SEDAC). This dataset includes geospatial variables such as latitude, longitude, land surface temperature (LST), urban-rural temperature differences (`D_T_DIFF`), and buffer density mean values (`BUF_D_MEAN`). The dataset required significant cleaning, including the removal of rows with missing values in critical columns. Relevant columns were extracted, and a new feature, `Norm_T_Diff`, was engineered by normalizing `D_T_DIFF` with `BUF_D_MEAN`, enabling comparative analysis across regions.

The **Global Carbon Budget Dataset** was obtained from Open Climate Data via GitHub and contains annual carbon emissions, population data, and atmospheric CO₂ growth. This dataset required refinement to remove unnecessary columns and standardize naming conventions, such as renaming `Total_CO2` to `CO2_Emissions` for clarity. Missing data points were addressed using interpolation methods, ensuring temporal continuity, and all units were standardized to enable seamless integration with other datasets.

The **Climate Data** was extracted from MODIS (Moderate Resolution Imaging Spectroradiometer) satellite products, providing high-resolution remote sensing data of global land surface temperatures. The raw file, available in `.xls` format, was converted to `.csv` for efficient processing. Inconsistent column headers were standardized, and irrelevant attributes were removed. The cleaned data was aligned temporally and spatially with other datasets to ensure compatibility during analysis.

The **Flat UI Environmental Data** included auxiliary environmental variables such as population density and land-use patterns. This dataset required integration with the UHI data using geospatial identifiers such as latitude and longitude. Columns were standardized for naming and unit consistency, and any overlapping or redundant data points were resolved. This integration enabled the analysis of the relationship between urban density, land use, and UHI intensity.

### **Implementation**

This project employed machine learning methods to predict Urban Heat Island (UHI) intensity using geospatial and environmental data. The key steps in the implementation process included feature engineering, model selection, and training-validation workflows. Features such as latitude, longitude, normalized temperature differences (`Norm_T_Diff`), population density, and carbon emissions were extracted from the datasets to serve as predictors.

For model selection, four machine learning models were implemented: Random Forest, Gradient Boosting, XGBoost, and Multilayer Perceptron (MLP). These models were chosen for their ability to handle non-linear relationships and complex interactions in the data. Random Forest and Gradient Boosting were employed as ensemble methods known for their robustness and accuracy. XGBoost provided an optimized gradient boosting approach with faster training and improved handling of missing data. The MLP model, a type of neural network, was included to capture intricate patterns in the data. The dataset was split into training (80%) and testing (20%) sets, and hyperparameters were fine-tuned for optimal performance. Cross-validation was used to reduce overfitting and ensure reliable model evaluation.

### **Evaluation**

The success of the models was evaluated using three standard regression metrics:

1.  **Mean Absolute Error (MAE)**:

    -   Measures the average magnitude of prediction errors without considering their direction.

    -   Provides a straightforward interpretation of model performance in the original unit of measurement.

2.  **Root Mean Squared Error (RMSE)**:

    -   Penalizes larger errors more heavily by squaring them before averaging.

    -   Suitable for applications where larger deviations from actual values are more critical.

3.  **R-squared (R²)**:

    -   Indicates the proportion of variance in the target variable that is explained by the model.

    -   Values closer to 1 imply better model performance.

Additionally, visualizations such as scatter plots (actual vs. predicted values) and residual plots were used to assess prediction accuracy and error distributions. The evaluation focused not only on numerical metrics but also on the interpretability and practical relevance of the models, ensuring actionable insights for urban planning and climate change mitigation.
