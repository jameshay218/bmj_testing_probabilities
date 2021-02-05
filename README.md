Probability of detection under different testing schemes. See the pdf file in this repository for formal notation.
------------
```{r example, message=TRUE,warning=TRUE,eval=TRUE}
ap <- c(0, 0, 0.25, 0.5, 0.9, 0.9, 0.5) ## Probability of detection for individual A
bp <- c(0, 0, 0, 0, 0, 0.25, 0) ## Probability of detection for individual B

# Ct values for individual A were 35, 28, 23, 12, 12, 15, 20
# If we approximate the probability of detection as being 0.9 below a Ct of 15, 0.75 from 15 to 20, 0.5 from 20 to 25, and 0 above 25

# Probability of detection if testing every day
1 - prod(1 - ap)
1 - prod(1 - bp)

# Probability of detection if testing once every 7 days
sum(ap / 7)
sum(bp / 7)

# Probability of detection by day X if testing every day
# X = 3
ap[3]
# X = 4
ap[3] + ap[4] * (1 - ap[3])

# Probability of detection by day X if testing every week
# X = 3
(ap[3] * (1 / 7))
# X = 4
((ap[3] * (1 / 7)) + (ap[4] * (1 / 7)))
```