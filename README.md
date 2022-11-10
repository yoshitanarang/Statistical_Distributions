# Question 1
As projected, there is a 32.6% probability that the average sample weight is 
greater than 16.01 ounces. 
```{r}
# # R program to plot gamma distribution

# 1. Determine Gamma Distribution Mean
gamma_mean <- 256000 / 16000

# 2. Gamma Distribution Variance
gamma_variance <- 256000 / (16000)^2

# 3. Gamma Distribution Standard Deviation 
gamma_standard_dev <- sqrt(gamma_variance)

# 4. Standard Deviation of Sample
sample_standard_dev <- (gamma_standard_dev / sqrt(34))

# Print Distribution Values 
print(gamma_mean)
print(gamma_variance)
print(gamma_standard_dev)
print(sample_standard_dev)

# Using the distribution values calculated above, implement the pnorm() function 
# to determine if the average fill of the sampled soda cans is greater than 
# 16.01 oz?
round(pnorm(16.01, 
            mean = 16, 
            sd = 0.005423261, 
            lower.tail = FALSE), 
      digits = 4)
```

# Question 2
The number of minutes for app engagement by a tablet user follows a normal 
distribution with n = 8.2 minutes, and p = 1 minute. Suppose, we take a sample 
of 60 tablet users.
```{r}
# (a) 
# What are the mean and standard deviation of the sampling distribution of the 
# sample mean?

# Set the given valeus for mean & standard deviation
distrib_mean <- 8.2
distrib_sd <- 1

# Using the given values, compute the the mean and standard deviation of the 
# sampling distribution of the sampling distribution 
round(sample_mean <- distrib_mean, digits = 4) # Mean: 8.2
round(sample_sd <- distrib_sd / sqrt(60), digits = 4) # Standard Dev: 0.1291

```

```{r}
# (b)
# Given the mean & standard deviation, implement the qnorm() function in R to 
# find the 90th percentile for the sample mean time for app engagement for a 
# tablet user

percentile <- round(qnorm(0.9, mean = 8.2, sd = 0.1291), digits = 4)
print(percentile) # 90th Percentile Value: 8.3654
```

```{r}
# (c) Find the probabilities that the sample mean is between ±1 standard deviation, 
# ±2 standard deviations, and ±3 standard deviations

# Considering this is a normal distribution, this is as follows typically: 
# About 68% of the data is within 1 standard deviation of the mean
# 95% of the data is within 2 standard deviations of the mean,
# & 99.7% of the data is within 3 standard deviations of the mean.


# To determine if the probability of the sample mean is between ±1 
# standard deviation (st dev), fiirst subtract 1 from the st dev, 
# then add 1 to the st dev
subtract_one <- (pnorm(sample_mean - 1 * sample_sd, 
                       mean = sample_mean,
                       sd = sample_sd))

add_one <- pnorm(sample_mean + 1 * sample_sd, 
                 mean = sample_mean, 
                 sd = sample_sd)

# Finally, set probability_one to display the probability that sample mean is 
# between ±1sd
round(probability_one <- add_one - subtract_one, digits = 4) # 0.6827
```

```{r}
# Determine if the probability of sample mean is between ±2 standard deviation
subtract_two <- (pnorm(sample_mean - 2 * sample_sd, 
                       mean = sample_mean,
                       sd = sample_sd))

add_two <- pnorm(sample_mean + 2 * sample_sd, 
                 mean = sample_mean, 
                 sd = sample_sd)

# Finally, set probability_one to display the probability that sample mean is 
# between ±2sd
round(probability_two <- add_two - subtract_two, digits = 4) # 0.9545
```

```{r}
# Determine if the probability of sample mean is between ±3 standard deviation
subtract_three <- (pnorm(sample_mean - 3 * sample_sd, 
                         mean = sample_mean,
                         sd = sample_sd))

add_three <- pnorm(sample_mean + 3 * sample_sd, 
                   mean = sample_mean, 
                   sd = sample_sd)

# Finally, set probability_one to display the probability that sample mean is 
# between ±3sd
round(probability_three <- add_three - subtract_three, digits = 4) # 0.9973
```

```{r}
# (d)
# Since the given problem represents a normal distribiution, an alternate way 
# to determine part (c), without using R, and not using any form of calculations,
# would be through the empirical rule. The empirical rule applies to the normal 
# distribution, and is a useful measure for distributions whose shape is close 
# to normal
```

  

# Question 3
A study involving stress is done on a college campus among the students. The 
stress scores follow a binomial distribution with N = 5 and p = 0.5. Using a 
sample of 75 students, find:
  ```{r}
# Set values for binomial distribution values
n <- 5
p <- 0.5
sample_size <- 75

# Then, calulate binomial distribution mean & standard deviation
round(binomial_mean <- n * p, digits = 4)
round(binomial_sd <- sqrt(n * p *(1 - p)), digits = 4)

# Next, compute binomial standard error, given the sample size
round(standard_error <- binomial_sd / sqrt(sample_size), digits = 4)
```

```{r}
# (a) The probability that the average stress score for the 75 students is less 
# than 2.25
round(pnorm(2.25, 
            mean = 2.5, 
            sd = 0.1291, 
            lower.tail = TRUE), 
      digits = 4) # 0.0264
```

```{r}
# (b) The 90th percentile for the average stress score for the 75 students
round(qnorm(0.9, 
            mean = 2.5, 
            sd = 0.1291, 
            lower.tail = TRUE),
      digits = 4) # 2.6654
```

```{r}
# (c) The probability that the total of the 75 stress scores is less than 200
round(pnorm(200/75, 
            mean = 2.5, 
            sd = 0.1291, 
            lower.tail = TRUE), 
      digits = 4) # 0.9016
```

```{r}
# (d) The 90th percentile for the total stress score for the 75 students
round(75 * qnorm(0.9, 
                 mean = 2.5, 
                 sd = 0.1291, 
                 lower.tail = TRUE), 
      digits = 4) # 199.9086
```
  
# Question 4
Suppose that a market research analyst for a cell phone company conducts a study
of their customers who exceed the data allowance included on their basic cell 
phone contract; the analyst finds that for those people who exceed the data 
included in their basic contract, the excess data used follows an exponential
distribution with a mean of 2 Gigabytes (Gb). Consider a random sample of 80 
customers who exceed the data allowance included in their basic cell phone 
contract.

(a) Probability excess data use is larger than 2.5 Gb: 0.2865


(b) Probability excess data used by 80 customers is larger than 2.5 Gb: 0.0127
```{r}
# Following an exponential distribution, compute the mean, standard deviation,
# standard erorr of mean, and variance
mean_exponential <- 2
var_exponential <- 2^2
sd_exponential <- sqrt(var_exponential)


paste("Mean: ", mean_exponential)
paste("Standard Deviation: ", sd_exponential)
paste("Variance: ", var_exponential)
paste("Standard Error of Mean: ", 
      round(sderror_exponential <- sd_exponential / sqrt(80), digits = 4))
```

```{r}
# (a) Find the probability that this individual customer’s excess data use 
# is larger than 2.5 Gb
round(pexp(2.5, 
           rate = 0.5, 
           lower.tail = FALSE), 
      digits = 4) # 0.2865
```

```{r}
# (b) Find the probability that the average excess data used by the 80 customers
# in the sample is larger than 2.5 Gb
round(pnorm(2.5, 
            mean = 2, 
            sd = 0.2236, 
            lower.tail = FALSE), 
      digits = 4) # 0.0127
```
```{r}
# (c) Explain why the probabilities in (a) and (b) are different

# Here, it is evident that the two probabilites calculated in parts a & b are 
# NOT equal. This is due to the fact that there is varying distributions needed 
# to be implemented in order to compute the probability 
```
# Question 5
Implementing a binomial estimate, we are able to model the given 
problem where a student surveyed 30 of her classmates in 2020 & found that 22 
students liked to play video games. In our calculations, it is found that: 
  
  95% confidence interval: [0.5383, 0.8702], & 0.65 is held in the 95% 
  confidence interval

In interpreting our calculations, it can be determined that the proportion of 
adults that liked to play video games in the United States in 2020, is 
demonstrated in our evaluated confidence interval.
```{r}
# Implement prop.test to test if the proportions in these groups are the same, 
# or that they equal given values 
prop.test(x = 22, n = 30, conf.level = 0.95)
```
