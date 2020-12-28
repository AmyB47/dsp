[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

***Exercise 5.1*** In the BRFSS (see Section 5.4), the distribution of heights is roughly normal with parameters μ = 178 cm and σ = 7.7 cm for men, and μ = 163 cm and σ = 7.3 cm for women.

In order to join Blue Man Group, you have to be male between 5’10” and 6’1” (see http://bluemancasting.com). What percentage of the U.S. male population is in this range? Hint: use scipy.stats.norm.cdf.



**Approach**

I used scipy.stats.norm to create a normal distribution for male heights with a mean of 178 cm and a standard deviation of 7.7 cm.

```python
import scipy.stats
male_hgt_mean = 178 #cm
male_hgt_std = 7.7 #cm

male_hgt_dist = scipy.stats.norm(loc=male_hgt_mean, scale=male_hgt_std)
```

Since the height requirements for Blue Man Group are given in feet and inches, I converted the minimum and maximum heights to centimeters. 

```python
blue_min_hgt = 5*12*2.54 + 10*2.54
blue_max_hgt = 6*12*2.54 + 1*2.54
```

I used scipy.stats.norm.cdf to find the percent of males at or below each of these heights.  The difference between these percents gives the percentage of the U.S. male population in this range. 

```python
answer = male_hgt_dist.cdf(blue_max_hgt) - male_hgt_dist.cdf(blue_min_hgt)
print(round(answer*100,2),'%')
```



**Solution**

34.2% of the U.S. male population is between 5’10” and 6’1”.