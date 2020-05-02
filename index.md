#### After learning from tutorial, making your own use case is very helpful in terms of checking understanding and see if you are really able to use what you leant to solve problems. Learning by doing is a very effective way. Let us start with an example I made:
use function random.randin and for loop based on certain lists you basically can create a dataset as large as you wish. Time is used to be index quite often especailly in time serises data, so creating date with pd.date_range is also often used when comes to make time series. Assigning data, index and columns respectively, a dataset can be easily made. Then, other functions can be used to practice abstracting subdataset, manipulating date to answer questions.

I first created a dataset with dates as index, name, age, nationality etc as columns. Please see code from repository. I asked myself to answer an "odd" question: "Does the popularity of different names change over time? " This is a classic question to practice abstracting to a subdataset. I first used df.sort_index() to make the date in desending order, after that I used df.reset_index().groupby().sum() to first divide dataset by Names, second by year, then sum up the number of each group, question answered. Basically three lines of code.

You can try to answer "Are there more female migrants than male migrants from different country?"

Remember that you will encounter problems that seems very simple and easy but you just have no idea where went wrong! Be patient with yourself, it is not that you are not smart enough, but because the language of machine is dull and picky, you have to first follow its rules strictly, second do not be afraid of trying. Make every possible changes to see what happen, start from simple version. Even many times your problem isn't solved but you learn something which is more valuable.

Keep doing.

### In second example, I asked a more comples question
- First I want to look at trend of health over time among different countries. Group the dataset based on nationality first, then years. Use label based indexing to select from the multi-indexed dataset. I found this way is easy to answer the question. Sometimes you need to explore the best way to manipulate data.

- To practice combining lambda function, we calculte then show if the age is an outlier within one counry. I found "reset_index"is not really a necessary command here, the "groupby" has done the job to make a multi-index. 
Coming to the calculation: 
> select the column to do the operation:
```
df_age['Age']
```
> use tranform which is on self producing a DataFrame with transformed value
```
df_age['mean'] = df_age['Age'].transform(lambda x: abs(x - x.mean()))
```
> I had a problem when calculate 1.96 standard diviation:
```
df_age['1.96*std'] = df_age['Age'].transform(lambda x: 1.96*x.std())
```
However there is error: transforms cannot produce aggregated results. I did some test finding the reason is: the result from the lambda function is a single number, the tranform function supposed to return a dataframe whihc has the same length with the age column, but I don't knbow why it failed to do that.....I spent at least one hour debugging on it, still not able to fix it.

So when you have done your best to trail and error, read docs ask for help, put the problem in stack overflow, wait for help, and let go, do not stuck there forever.

[Question posted here:]
(https://stackoverflow.com/questions/61558919/transforms-cannot-produce-aggregated-results-with-lambda-function-that-produced)
