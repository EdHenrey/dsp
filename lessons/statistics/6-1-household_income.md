[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)



import matplotlib.pyplot as plt

import hinc

df=hinc.ReadData()

import hinc2

hincarray=hinc2.InterpolateSample(df, log_upper=6.0)

np.median(hincarray), hincarray.mean() #stats for log

(4.7094983556124745, 4.657585735892018)

_=plt.hist(hincarray)

_=plt.hist(10**hincarray)

_=plt.plot((hincarray), range(len(hincarray)))

_=plt.plot(10**hincarray, range(len(hincarray)))

inc=10**hincarray

np.median(inc), inc.mean()  # (51226.93306562372, 74278.7075311872)

(51226.93306562372, 74278.7075311872)

Skewness(inc)  # 4.949920244429583

4.949920244429583

PearsonMedianSkewness(inc) # = 0.7361258019141782  (LOWER!)

0.7361258019141782

def CDFpercentile(data, x):

    counter=0

    for i in data:

        if i < x:

            counter+=1

        else:

            return 100*counter/len(data)        

CDFpercentile(inc, inc.mean()) # 66% of population below the mean due to the exponenetial nature of incomw.We gave a million dollars a year to the highest earner during interpolation.
