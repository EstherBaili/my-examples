## Examples for new pandas users summary

#### I find after learn from the examples, making yourown user case is very helpful to check understanding and see if you are really able to use them solve problems. Learning by doing is a very effective way. Let us start with an example I made:
use function random.randin and for loop based on certain lists you basically can create a dtaset as large, time is a normal index especailly in time serises data so creating date with pd.date_range is also useful. Assigning data, index and columns respectively, a dataset is made. Then, other functions can be used to practice abstracting subdataset, manipulating date to answer questions.

I first created a dataset with dates as index, name, age, nationality etc as columns. I asked myself to answer "an odd" question: "Does the popularity of different names chage with time? " This is a classic question to practice abstract subdataset. I first used df.sort_index() to make the date index in desending order. after that I used df.reset_index().groupby().sum() to first divide dataset by Names, second by year, then sum up the number of each group, question answered. Basically three lines of code.

You can try to answer "Are there more female migrants than male migrants from different country?"

Remember that you will encounter problems that seems very simple and easy but you just do not know where went wrong! Be patient with yourself, nothing wring with you, the language of machine is dull and picky, you have to first follow its rules, second do not be afraid of trying, make every possible changes to see what happen, start from simple version. Even many times your problem isnt solved but you learn something.  
