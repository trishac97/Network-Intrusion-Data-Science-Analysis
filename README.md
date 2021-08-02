# Network-Intrusion-Data-Science-Analysis

Network intrusion detection systems are built on blackbox machine learning algorithms which picks features
that are deemed important. It is complex to analyze which feature is the important over the other so that
the model is not overfitted or underfitted. Modeling this problem using random forest is a well traversed
approach, but random forest essentially suffers from feature selection problem. 

According to my high level analysis on network data, I have the following understanding of the selected features:

(1) Duration is an important indicator. A connection that lives in the network for a longer time is indeed
suspicious. Although, training a machine learning model on only duration feature can result into some
false positive malicious packets, i.e., it is evident from the plots I formed that malicious traffic don’t
always have to be in the network for a long duration.

(2) Failed attempt indicator helped in identifying which flavor of “guess password” attack the adversaries
were using. I suspected it to be bruteforce attack, but in reality, adversaries exploited TELNET and
sniffed the password from the network.

(3) Flag indicator is an obvious and important indicator.

(4) From guest login indicator, not all adversaries use guest login to attack the network.

(5) Source byte is an important indicator. Abnormally large size packets for a long duration of time can
bring down a host (unavailable).

Random Forest shows a high accuracy of 99.7% using the features I used. Although, it is worthwhile noting
that KDD CUP 1999 is an old data and the type of attacks has evolved ever since. On the concluding note,
network data is complex. Depending on what type of attack detector we want, machine learning features
needs to be tweaked. Source data byte is important feature for DOS attack, but duration indicator is not.
