Every URL that is accessed is categorized by the Phishing Detection Chrome Extension into phished and non-phished categories (on page load), alerting the user to any fraudulent behavior and preventing intrusion.

Steps to install the chrome extension:
1. Google Chrome -> More Tools -> Extensions
2. Click 'Load unpacked extension..'
3. Open the 'Engineering Module' directory
4. Phishing Detection extension ready to monitor all the sites loaded on the Chrome browser

Test URLs(positive tests - phishing detected):
1. ../Engineering Module/Phishing.html (Test phished page created)
2. https://www.phishtank.com/phish_search.php?verified=u&active=y (List of phished sites available)

ML Algorithms:
The data set has been evaluated using ML methods, including SVM, Neural Networks, and Random Forest. The SVM trained persistent model has been sent to the engineering module for phishing detection.

Engineering Modules:
1. manifest.json:
It provides Chrome with the basic information about the extension like name, permissions, associated scripts and files.

2. content.js:
It runs in separate unprivileged javscript environment and has complete access to the DOM.
Here, the trained SVM model(weights calculated in ./ML Algorithm Evaluation/run_algorithms.py) has been used as a persistent model to classify websites.


3. background.js: 
In case, we need access to external extensions or APIs, it is necessary to create means of communication between the content.js and privileged parts of the our extension, and this interaction is termed as message passing. Message passing allows different components of our extension to collabrate. 

NOTE: The extension validates every URL call, i.e. in case of URL redirection, it will assess every intermittent URL hit as well.