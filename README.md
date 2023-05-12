# IBM applied DataScience Capstone project  
 *You can access the PowerPoint slides for this project in either [Capstone projectpdf](Capstone_project.pdf) [powerpoint slide show](Capstone_project.pptx)*  
 
 # Executive summary  
 This capstone project aims to predict the successful landing of the SpaceX Falcon 9 first stage using various machine learning classification algorithms. The project involves several key steps:
 * Data collection, wrangling, and formatting
 * Exploratory data analysis
 * Interactive data visualization
 * Machine learning prediction
 
 According to our graphs, there is a correlation between certain features of rocket launches and their outcomes, whether successful or not. Additionally, it appears that the decision tree algorithm may be the most effective in predicting the successful landing of the Falcon 9 first stage.
 
 # Introduction  
 The goal of this capstone project is to predict whether the Falcon 9 first stage will land successfully. SpaceX offers Falcon 9 rocket launches at a cost of 62 million dollars, as advertised on their website. This is significantly lower than other providers, who charge upwards of 165 million dollars per launch. The cost savings are largely due to SpaceX’s ability to reuse the first stage. By predicting whether the first stage will land successfully, we can determine the cost of a launch. This information could be useful for other companies looking to compete with SpaceX for rocket launches.

It is important to note that most unsuccessful landings are planned. SpaceX sometimes performs controlled landings in the ocean. The main question we aim to answer is whether the first stage of a Falcon 9 rocket will land successfully given a set of features about the launch, such as payload mass, orbit type, and launch site.
# Methodology  
The methodology includes: 
* Data collection, wrangling, and formatting, using:
  * SpaceX API
  * Web scraping
  
* Exploratory data analysis (EDA), using:
  * Pandas and NumPy
  * SQL
  
* Data visualization, using:
  * Matplotlib and Seaborn
  * Folium
  * Dash
* Machine learning prediction, using :
  * Logistic regression
  * Support vector machine (SVM)
  * Decision tree
  * K-nearest neighbors (KNN)

# Data Collection using Web Scraping  
[2Data Collection with Web Scraping.ipynb](2Data-Collection-with-Web-Scraping.ipynb)

* The data was obtained by scraping the [List of Falcon9 and Falcon Heavy launches web page.](https://en.wikipedia.org/w/index.php?title=List_of_Falcon_9_and_Falcon_Heavy_launches&oldid=1027686922)
* The website exclusively provides data pertaining to Falcon 9 launches.
* Initially, the Falcon9 Launch Wiki page is retrieved from the URL and a BeautifulSoup object is generated from the response of the requests.get() function.
* Then, the column or variable names are obtained from the HTML table header using the find_all() function of BeautifulSoup.
* A dataframe is subsequently constructed using the extracted column names and populated with launch records obtained from the table rows.
* The resulting dataframe consists of 121 rows, representing instances, and 11 columns, representing features.
# EDA with Pandas and Numpy  
[3EDA.ipynb](3EDA.ipynb)
Functions such as value_counts() from the Pandas and NumPy libraries are utilized to obtain fundamental information about the collected data, including:

* Number of launches on each launch site
* Number of occurrence of each orbit
* Number and occurrence of each mission outcome
# EDA with SQL  
[4EDA with SQL](4EDA-with-SQL.ipynb)

SQL is used to query the data and address multiple questions about it, such as:
* The distinct launch sites involved in the space mission.
* Total payload mass carried by boosters launched by NASA (CRS)
* Average payload mass carried by booster version F9 v1.1
The SQL functions and statements utilized comprise of SELECT, DISTINCT, AS, FROM, WHERE, LIMIT, LIKE, SUM(), AVG(), MIN(), BETWEEN, COUNT(), and YEAR().
# Data Visualization using Matplotlib and Seaborn  
[5EDA Visualization](5EDA-Visualization.ipynb)
Functions from the Matplotlib and Seaborn libraries are employed to represent the data visually using scatterplots, bar charts, and line charts. These plots and charts aid in comprehending the relationships between various features, such as:
* The correlation between the flight number and the launch site.
* The correlation between payload mass and launch site
* The correlation between success rate and orbit type
Functions from the Seaborn library that are utilized in this context include scatterplot(), barplot(), catplot(), and lineplot().

Example: The scatterplot shows the correlation between flight number and launch site
![image](https://github.com/hsalnasi/IBM-applied-DataScience-Capstone-project/assets/89119185/b73727ca-d867-4414-b6f5-5cb0b8b86a8c)
# Data Visualization using Folium  
[Interactive Visual Anaylitcs with Folium](6Interactive-Visual-Analytics-with-Folium-lab.ipynb)
The Folium library is used to create interactive maps to display data visually.
* Mark all launch sites on a map
* Mark the succeeded launches and failed launches for each site on the map
* Mark the distances between a launch site to its proximities such as the nearest city, railway, or highway
Functions such as add_child() and folium plugins like MarkerCluster, MousePosition, and DivIcon are used to create interactive maps with the Folium library.

Example A: A folium map showing the succeeded launches and failed launches for a specific launch site. If we zoom in on one of the launch site, we can see green and red tags. Each green tag represents a successful launch while each red tag represents a failed launch.

![image](https://github.com/hsalnasi/IBM-applied-DataScience-Capstone-project/assets/89119185/4798910b-e6ad-4784-a447-a142db171c55)

# Data Visualization using Dash  
[](7spacex_dash_app.py)
Functions from Dash are used to generate an interactive site where we can toggle the input using a dropdown menu and a range slider. Using a pie chart and a scatterplot, the interactive site shows:

*  total success launches from each launch site
*  The correlation between payload mass and mission outcome (success or failure) for each launch site
  
When the launch site CCAFS LC-40 is selected from the dropdown menu on the website, a pie chart is displayed. In the chart, 0 indicates failed launches and 1 indicates successful launches. According to the chart, 73.1% of launches at CCAFS LC-40 were unsuccessful.

![image](https://github.com/hsalnasi/IBM-applied-DataScience-Capstone-project/assets/89119185/d8610f09-c4a6-4814-b34d-8146def05b12)

In the picture below , When the payload mass range is set between 2000kg and 8000kg, a scatterplot is displayed. In the plot, class 0 indicates failed launches and class 1 indicates successful launches.

![image](https://github.com/hsalnasi/IBM-applied-DataScience-Capstone-project/assets/89119185/274279c8-e0dc-4a69-9684-41f372158b6f)


# Machine Learning Prediction  
(8Macine Learning Prediction.ipynb)
The Scikit-learn library is used to create machine learning models in the prediction phase of the project, which includes several steps.
* 1. The data is standardized using the StandardScaler() function from the preprocessing module of the Scikit-learn library.
* 2. The data is divided into training and test sets using the train_test_split function from the model_selection module of the Scikit-learn library.
* 3. Machine learning models are created, which include several types of models:

* Machine learning models are created, which include several types of models.
* Support vector machine (SVM) using SVC from sklearn.svm
* Decision tree using DecisionTreeClassifier from sklearn.tree
* K nearest neighbors (KNN) using KNeighborsClassifier from sklearn.neighbors

* 4. Fit the models on the training set
* 5. Find the best combination of hyperparameters for each model using GridSearchCV from sklearn.model_selection
* 6. Evaluate the models based on their accuracy scores and confusion matrix using the score() function and confusion_matrix from sklearn.metrics
When the results of all four models are compared, they have the same accuracy score and confusion matrix on the test set. As a result, their GridSearchCV best scores are used to rank them. The models are ranked in order of their GridSearchCV best scores, with the first being the best and the last being the worst.
* Decision tree (GridSearchCV best score: 0.8892857142857142)
* K nearest neighbors, KNN (GridSearchCV best score: 0.8482142857142858)
* Support vector machine, SVM (GridSearchCV best score: 0.8482142857142856)
* Logistic regression (GridSearchCV best score: 0.8464285714285713)

The image below displays the confusion matrix for the Decision Tree model when it is evaluated on the test data.

![image](https://github.com/hsalnasi/IBM-applied-DataScience-Capstone-project/assets/89119185/ac2aa472-76d0-4bd7-8446-9b4a857f5260)

# Discusion  
According to the data visualization section, some features may be correlated with the mission outcome. For instance, for orbit types Polar, LEO, and ISS, the successful landing rate is higher for heavy payloads. However, for GTO orbit type, it is difficult to distinguish between positive and negative landing rates because both successful and unsuccessful missions are present.

Each feature may have a specific influence on the final mission outcome, but it is difficult to determine exactly how each feature affects the outcome. Machine learning algorithms can be used to learn from past data patterns and predict the success of a mission based on the given features.

# Conclusion  
In this project, the goal is to predict whether the first stage of a Falcon 9 launch will land successfully in order to determine the cost of the launch. Each feature of a Falcon 9 launch, such as its payload mass or orbit type, may have an impact on the mission outcome. Several machine learning algorithms are used to learn from past Falcon 9 launch data and create predictive models. The decision tree algorithm produced the best predictive model among the four machine learning algorithms used.

' Date modifed : 12-5-2023'

 
