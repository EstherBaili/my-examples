## Examples for new pandas users summary

#### After learning from tutorial, making your own use case is very helpful in terms of checking understanding and see if you are really able to use what you leant to solve problems. Learning by doing is a very effective way. Let us start with an example I made:
use function random.randin and for loop based on certain lists you basically can create a dataset as large as you wish. Time is used to be index quite often especailly in time serises data, so creating date with pd.date_range is also often used when comes to make time series. Assigning data, index and columns respectively, a dataset can be easily made. Then, other functions can be used to practice abstracting subdataset, manipulating date to answer questions.

I first created a dataset with dates as index, name, age, nationality etc as columns. Please see code from repository. I asked myself to answer an "odd" question: "Does the popularity of different names change over time? " This is a classic question to practice abstracting to a subdataset. I first used df.sort_index() to make the date in desending order, after that I used df.reset_index().groupby().sum() to first divide dataset by Names, second by year, then sum up the number of each group, question answered. Basically three lines of code.

You can try to answer "Are there more female migrants than male migrants from different country?"

Remember that you will encounter problems that seems very simple and easy but you just have no idea where went wrong! Be patient with yourself, it is not that you are not smart enough, but because the language of machine is dull and picky, you have to first follow its rules strictly, second do not be afraid of trying. Make every possible changes to see what happen, start from simple version. Even many times your problem isn't solved but you learn something which is more valuable.

Keep doing.
