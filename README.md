# FIFA21
In this project, I have chosen the FIFA21 database as the dataset for analysis.
FIFA21 is a popular video game that simulates professional soccer,
and its database contains various attributes and statistics of soccer players from around the world.

## 1. Objective
The goal is to clean and preprocess the data to predict the market value,
in addition to analyzing different insights.

## 2. Data
The DataFrame has 17,125 rows and 107 columns. It contains a combination of numerical data (float64 and int64) and object data (text strings)
/Users/iagogarrido/Documents/ironhack/data_mid_bootcamp_project_FIFA_MoneyBall/images
<img src="./images/data.png" width=600>

Each column name is the abbreviation of one 

- **ID:** Unique identifier for each player in the FIFA 21 database.
- **Name:** Player's name.
- **Age:** Player's age.
- **OVA:** Overall rating of the player in the FIFA 21 game.
- **Nationality:** Player's nationality.
- **Club:** Club to which the player belongs in the FIFA 21 game.
- **BOV:** Best overall rating of the player in the FIFA 21 game.
- **BP:** Best position preferred by the player on the field.
- **Position:** Player's primary position on the field.
- **Player Photo:** Photograph of the player.
- **Club Logo:** Logo of the club to which the player belongs.
- **Flag Photo:** Photograph of the player's national flag.
- **POT:** Player's maximum potential rating in the FIFA 21 game.
- **Team & Contract:** Player's current team and contract details.
- **Height:** Player's height.
- **Weight:** Player's weight.
- **Foot:** Player's dominant foot (Right or Left).
- **Growth:** Potential growth of the player.
- **Joined:** Date when the player joined the current club.
- **Loan Date End:** Date when the player's loan ends (if applicable).
- **Value:** Market value of the player.
- **Wage:** Player's salary.
- **Release Clause:** Contract release clause of the player.
- **Contract:** Remaining duration of the player's contract.
- **Attacking:** Statistics related to the player's attacking abilities.
- **Defending:** Statistics related to the player's defending abilities.
- **Goalkeeping:** Statistics related to the player's goalkeeping abilities.
- **Total Stats:** Total statistics of the player.
- **Base Stats:** Base statistics of the player.
- **W/F:** Weak foot/strong foot rating.
- **SM:** Skill Moves rating (special movement skills).
- **A/W:** Attack Work Rate.
- **D/W:** Defense Work Rate.
- **IR:** International Reputation index.
- **PAC:** Pace rating of the player.
- **SHO:** Shooting ability rating of the player.
- **PAS:** Passing ability rating of the player.
- **DRI:** Dribbling ability rating of the player.
- **DEF:** Defensive ability rating of the player.
- **PHY:** Physicality rating of the player.
- **Hits:** Popularity or relevance rating of the player in the FIFA 21 game.
- **LS:** Player's position on the field (Left Striker).
- **ST:** Player's position on the field (Striker).
- **RS:** Player's position on the field (Right Striker).
- **LW:** Player's position on the field (Left Winger).
- **LF:** Player's position on the field (Left Forward).
- **CF:** Player's position on the field (Center Forward).
- **RF:** Player's position on the field (Right Forward).
- **RW:** Player's position on the field (Right Winger).
- **LAM:** Player's position on the field (Left Attacking Midfielder).
- **CAM:** Player's position on the field (Center Attacking Midfielder).
- **RAM:** Player's position on the field (Right Attacking Midfielder).
- **LM:** Player's position on the field (Left Midfielder).
- **LCM:** Player's position on the field (Left Center Midfielder).
- **CM:** Player's position on the field (Center Midfielder).
- **RCM:** Player's position on the field (Right Center Midfielder).
- **RM:** Player's position on the field (Right Midfielder).
- **LWB:** Player's position on the field (Left Wing Back).
- **LDM:** Player's position on the field (Left Defensive Midfielder).
- **CDM:** Player's position on the field (Center Defensive Midfielder).
- **RDM:** Player's position on the field (Right Defensive Midfielder).
- **RWB:** Player's position on the field (Right Wing Back).
- **LB:** Player's position on the field (Left Back).
- **LCB:** Player's position on the field (Left Center Back).
- **CB:** Player's position on the field (Center Back).
- **RCB:** Player's position on the field (Right Center Back).
- **RB:** Player's position on the field (Right Back).
- **GK:** Player's position on the field (Goalkeeper).
- **Gender:** Player's gender (Male or Female).

## 3. Data cleaning

- Checking for missing values
- Handling missing numerical values: For the columns 'Volleys', 'Curve', 'Agility', 'Balance', 'Jumping', 'Vision', 'Sliding Tackle', 'Composure', 'Interceptions', and 'Positioning', the missing values are filled using the mean or median of the respective columns. The code calculates the mean for 'Volleys', 'Curve', 'Sliding Tackle', 'Composure', and 'Interceptions' using the mean() function, and the median for 'Agility', 'Balance', 'Jumping', 'Vision', and 'Positioning' using the median() function. The fillna() function is used to fill the missing values in these columns with the calculated mean or median
- Handling missing categorical values: The missing values in the 'Club' column are filled with the string 'WITHOUT A CLUB', indicating that the player doesn't belong to any club. The missing values in the 'Position' column are filled with the values from the 'BP' (Best Position) column, assuming the best position is the same as the primary position.
- Handling missing values in other columns: The missing values in the 'A/W' (Attack Work Rate), 'D/W' (Defense Work Rate), and 'Joined' columns are filled with the values 'MEDIUM', 'MEDIUM', and 'Dec 31, 2020' respectively. These values are chosen as reasonable defaults.
- Dropping unnecessary columns: The code drops the columns 'Player Photo', 'Club Logo', 'Flag Photo', and 'Loan Date End' using the drop() function with axis=1 to remove those columns from the DataFrame.
- Data type conversion: The code performs data type conversions for certain columns. It removes the Euro symbol '€' from the 'Value', 'Wage', and 'Release Clause' columns using the str.replace() function. It replaces 'M' with 'e6' and 'K' with 'e3' to represent millions and thousands respectively. Then it converts the columns to float data type using the astype() function.

## 4. Exploratory Data Analysis (EDA) Visualizations

- Market value distribution
<img src="./images/market_value_distribution.png" width=600>
- Correlation matrix
<img src="./images/correlation_matrix.png" width=600>
- Most influential features in market value
<img src="./images/influential_features.png" width=600>


## 5. Machine Learning: Prediction of Player Market Value using Linear Regression

- Features and Target Variable Selection:

    - The selected features for the model are 'Age', 'OVA' (Overall Rating), 'POT' (Potential), 'BOV' (Best Overall Rating), 'Release Clause', and 'Wage'.
    - The target variable is 'Value', representing the market value of players

- Data Splitting:

    - The dataset is split into training and testing sets using an 80:20 ratio.
    - The random_state parameter is set to 42 for reproducibility.

- Linear Regression Model Training:

    - A linear regression model is created and trained using the training data.
    - The LinearRegression() function is used to instantiate the model.
    - The fit() function is then called to train the model using the training data.

- Prediction and Evaluation:

    - Predictions are made on the test set using the trained model.
    - The mean squared error (MSE) and coefficient of determination (R^2) are calculated to evaluate the model's performance.

- Visualization:

    - A scatter plot is created to visualize the actual values versus the predicted values.
    - The plot includes a red dashed line representing the ideal scenario where the actual and predicted values are identical.
<img src="./images/predicted_value.png" width=600>

## 6. Analysis and Visualization of Football Players' Data

- Distribution of players by nationality
<img src="./images/distribution_by_nationality.png" width=600>

- Age vs. Value of players
<img src="./images/agevsvalue.png" width=600>

- Comparison of Skills between Players from Different Clubs
<img src="./images/agevsvalue.png" width=600>

- Comparison of Speed and Overall Rating
<img src="./images/speedvsova.png" width=600>


## conclusions:


- Most influential features on market value: According to the correlation matrix, the most influential features on a player's market value are age, current overall rating (OVA), potential (POT), peak overall rating (BOV), and release clause.

- Linear regression model: A linear regression model has been used to predict the market value of players. The model shows a good fit, with a coefficient of determination (R^2) of approximately 0.962, indicating that 96.2% of the variability in market value can be explained by the features used in the model.

- Prediction accuracy: The mean squared error (MSE) is calculated to be approximately 1.22 billion euros. While this may seem high in absolute terms, it is important to consider the range of player market values, which span from a few thousand euros to over 100 million euros. In that context, the MSE indicates a reasonable level of prediction accuracy.

- In summary, we can conclude that age, current overall rating, potential, peak overall rating, and release clause are important factors in determining the market value of a football player. The linear regression model used provides good predictions, although there is room for improving accuracy


