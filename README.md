
Introduction
------------

Event        : Seattle - Unity - QA summit - NOV6-9 2017
Hack project : Using machine learning to detect IAP fraud
Team         : Jeff, Mohammed, Joe, Vikas

Problem Definition
------------------

Player acquires paid game content (ex. conis, gems) without paying money. If that
goes undetected then the purchases are recorded as real. The end result is a
discrepancy between reported reveniew and actual revenue.


IAP Hacking Tools
-----------------

* Most, not all, require rooted/jailbreak
  - LuckyPatch: Achieve fraud by changing the apk file of apps, mainly the 
    AndroidManifest.XML file
  
  - Creehack (does not require root): Achieve fraud by hijacking the process 
    and completes the purchase with its inbuilt card.
  
  - Cydia and Localiapstore (IOS): Cydia jailbreak device as downgrade OS 
    possibilities, Localiapstore bypass the AppStore directly to 
    download/install page

* Potential data we can use:

  - OS version
  - Location – currency consistency
  - App billing format
  - The app/game type (server based or not)

IAP Fraud Prevention
--------------------

* Implement local and/or remote receipt validation
* Implement revenue verification
* Try to detect fraud using data

Note
----

We do not have access to labeled transaction data to build a real ML model so
we decided to build 2 hello world demos (Octave and Python) for the sake of
sharing with the team. 

How ML Works? (in a min)
------------------------

* Given data samples (ex. purchases)
* Predict properties of unknown data. How?
* Build a model from data matrix (do not ask us about the math please)
* Features are the columns
* Samples are the rows
* Result is continuous (regression) or discreet (classification)
* In case of IAP it is going to be valid or fraud
* Supervised: (classicfication ex. OCR or regression ex. house price)
* Unsupervised: no target values, discover similar groups (clustering)
* Training set vs testing set to evaluae the algorithm (cross validation)
* Use scikit-learn Python ML library
* Use different estimators (or models ex. SVM)
* Choosing the parameters of the model (not covered here)

Octave
------

* Think of it like the free Matlab
* Good for prototyping

Scikit-learn
------------

* Open source ML lib in python
* Data standardization and normalization
* Supervised Learning Estimators (Linear reg., SVM, Naive Bayes, KNN)
* Unsupervised Clustering
* Cross-Validation
* Feature extraction and selection
* A lot more visit: http://scikit-learn.org

ML in a container
-----------------

* The demo is checked to github
* Clone it, follow the instructions
* You should have an ML env template ready in 5 mins

# Clone the repo
git clone xxx

# Build docker image
docker build . -t seattle-qa-summit-hack

# Launch container
docker run -p 4444:7777 -d seattle-qa-summit-hack

# Open browser and have fun
http://127.0.0.1:4444/demo/api/v1.0/predict?p1=3.0&p2=2.0&p3=1.0

Thanks all

