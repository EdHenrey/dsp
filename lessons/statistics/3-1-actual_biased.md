[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>> REPLACE THIS TEXT WITH YOUR RESPONSE


d_child=dict(resp.numkdhh.value_counts())
d_child

pmf_child= thinkstats2.Pmf(d_child, label='actual')
tot_child=resp.numkdhh.value_counts().sum()
pmf_child_norm=pmf_child/tot_child
tot_child, pmf_child_norm

def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf

biased_pmf_child=BiasPmf(pmf_child_norm, label='observed')

biased_pmf_child

thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf_child, biased_pmf_child])
thinkplot.Config(xlabel='Children per fam', ylabel='PMF')