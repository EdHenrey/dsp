[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> REPLACE THIS TEXT WITH YOUR RESPONSE

## Chapter 5 Exercise 1

hdf = pd.HDFStore('~/Desktop/coding/aug/ThinkStats2/homeworks/brfss.hdf5',mode='r')
hdf.groups()
hdf.keys()
df1=hdf.get('/brfss')  #not '/DF1' as on youtube 
type(df1) #hopefully pd df
df1.iloc[:10]

df1.info()

men_hts=df1.HTM4[df1.SEX==1].dropna()
men_hts.mean(), men_hts.std()

### METHOD I

def cdfs(list,element):
    count=0
    for i in sorted(list):
        if i<element:
            count+=1
    return (count/len(list))

h1,h2=(5*12+10)*2.54, (6*12+1)*2.54
h1,h2

men_hts_list=sorted(men_hts.values)

cdfs(men_hts, h2), cdfs(men_hts_list, h1)

cdfs(men_hts, h2) - cdfs(men_hts_list, h1)

### METHOD II

from scipy.stats import norm

norm.cdf((h2-178)/7.7), norm.cdf((h1-178)/7.7)

norm.cdf((h2-178)/7.7)-norm.cdf((h1-178)/7.7)

ANSWER: 34% of male poplulation would be between 5’10” and 6’1”