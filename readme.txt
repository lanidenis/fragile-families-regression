All code for this project can be found in the Jupyter notebook "FF_Code_1" that is in this folder.

No code needs to be run, as the notebook already saved the output from my previous runs.

You can simply scroll through the notebook from top to bottom. The code goes through the following steps:

	1. preprocessing 
		a. remove constant variables 
		b. remove sparse columns 
		c. narrow to constructed variables only

	2. cleaning and imputation
		a. convert 'bin' and 'string' types to 'uc', impute with mode
		b. convert missing data to extra'uc' categories, impute with mode
		c. impute 'oc' missing data with mode
		d. impute 'cont' missing data with mean

	3. Separate processed data in 'uc' and 'other' types
		a. min max scale the 'other' (cont/oc) types
		b. convert 'uc' data with one-hot encoding
		c. combine both types of data into final matrix

	4. Fetch training labels
		a. exclude all NA label rows
		b. fetch training samples corressponding with available training label challengeID's
		c. impute missing information in training labels 

	5. Logistic Regresson
		a. perform KFold CV with l1 and l2 regression for each of the binary labels
		b. evaluate with Brier Loss Scores

	6. Linear Regression
		a. perform KFold CV with elastic regression for each of the continuous labels
		b. evaluate with Mean Squared Error

	7. SVM - SVC 
		a. perform SVM classification via GridSearchCV for each of the binary labels
		b. since probabilities are required by leaderboard, and SVM does not naturally provide these, I extrapolate my own probabilities by scaling appropriately the output of the decision_function(), which represents the distance of any sample from the hyperplane
		c. Evalute with Brier Loss Scores

	8. SVM - SVR
		a. perform SVM regression via GridSearchCV for each of the continous labels
		b. evaluate with Mean Squared Error

	9. Print the best results to 'prediction.csv'

	10. Most Important Feature Analysis
		a. analyze features with largest coefficients for linear/logistic regression
		b. determine topics associated with those features from meta-data 

