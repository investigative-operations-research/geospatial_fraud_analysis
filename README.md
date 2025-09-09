# geospatial_fraud_analysis

This relates to the sales journey of the retail channel analysis in terms of developing a range of features to identify likely cases of fraud and or abuse via purchasing behaviour - this example is a set of features based on the geographical location of sales.

 

It is also a good example of why solutions need to be flexible to change over time, in this case these features were very flexible so they could be changed as behaviours changed. This is important because the adversary here is a human who changes their behaviour according to feedback, so our metrics had to be flexible with the aim of making the loop-holes more expensive to exploit to encourage bad actors to move on. For those that adapted behaviours, it is a real-life case study in Goodhart's law that states "When a measure becomes a target, it ceases to be a good measure" so our systems had to be able to adapt as adversaries did.

 

PROOF OF CONCEPT:

I started with a few example cases from the fraud investigations team of purchases that were linked to fraudulent activity, such as stolen credit cards for example, and was asked to do some analysis across the data sets available to see if we could find any patterns.

 

One idea I had was to find the store locations of these purchases and see if there were any patterns that stood out. I quickly found a few small clusters where a string of purchases were made in the same day quite close by to each other.

 

This is a totally ficticious example I just did on Google maps now for demonstration purposes and deliberately has no relation at all to any of the actual investigations ---

 

 

What I found was that the majority of locations were spread randomly around the country typically, but a few small clusters like this were enough to end up in my sample list here.

 

TESTING THE CONCEPT WITH SOME SAMPLE CASES OF MY OWN FOR REVIEW

Once I had these examples tested out I went back with some counter examples to expand the list and was told that my expanded list was 95% accurate with finding a number of sales that had since come through in the days since starting the investigation - and a few that even the credit card merchants had missed that were to be cleaned up.

 

SCALING THIS APPROACH ACROSS THOUSANDS OF RETAIL OUTLET LOCATIONS WITH PYTHON

To then scale this approach across several thousand retail outlets across Australia, I could not manually check and cross check them all. At first I tried getting the business addresses and checking against opensource business GPS (lattitude and longitude) coordinates but found that about 35% addresses from our sales partner base was not aligning with the Auspost addresses for data matching purposes.

 

To overcome this I then developed a script to call the Google API to feed the addresses through and get map coordinates which enabled coverage to rise to about 99.5% of stores with usable coordinates we could have confidence in for this purpose.

 

 BRINGING IT ALL TOGETHER

From here I took the GPS data and created a feature store in AWS - the idea being that we could automate taking in new sales cases and cross-reference those sales with this coordinate feature store to calculate proximity values that could adjust as needed over time as trends changed.

 

This then became the input to dashboards in Power BI and Splunk for the relevant teams to provide a look-around tool along the lines of a search nearby function, say looking for cafes within 300m of your current location, for the fraud investigation team to be able to use as a search tool for reviewing any suspicious cases - rather than assuming guilt or innocence classifications by AI tools alone.

 
