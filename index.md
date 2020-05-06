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

## 4/May/2020 third example
### A bit about debugging using today's example.

I had an example on how to formatting URL to automatically getting data from website. 
```
url_template = "http://climate.weather.gc.ca/climateData/bulkdata_e.html?format=csv&stationID=5415&Year={year}&Month={month}&timeframe=1&submit=Download+Data"
url = url_template.format(month=3, year=2012)
weather_mar2012 = pd.read_csv(url, skiprows=16, index_col='Date/Time', parse_dates=True, encoding='latin1')
```
It is a weather data from Canadian government.
But the origianl page no longer exists, it seems they have changed the data structure. 

I manually found the relevent data, I need to change the URL. Because I don't know the right URL to use to download the data as the data downloaded through cliking button. I used the URL of the web which presenting and the download button included. It has a similar format with the URL from the example. 
```
https://climate.weather.gc.ca/climate_data/daily_data_e.html?timeframe=2&hlyRange=%7C&dlyRange=1979-06-01%7C2020-01-31&mlyRange=1979-01-01%7C2018-02-01&StationID=5619&Prov=QC&urlExtension=_e.html&searchType=stnProv&optLimit=specDate&StartYear=1840&EndYear=2020&selRowPerPage=25&Line=145&lstProvince=QC&Day=30&Year=2012&Month=3#
```
But there is an error when running the code.

It could be two possible reasons: 
- one is the data wasn't successfully downloaded, it is not the right URL
- the other is the formatting of the dowloaded data somehow caused that.  

To identify the root cause, manually download the data file, save in local computer, pd_csv_read through local path, 
```
weather_mar2012 = pd.read_csv('C:/Users/li116/OneDrive/Desktop/python project/python tutorial/en_climate_daily_QC_7035666_2012_P1D.csv')
weather_mar2012
```
there was no error which means must be the URL not the right one to use.

Therefore, the next step to solve the problem is to find how how to find the URL of clicking downloading button. I did some reasech: so on the page, right click to choose insepct, then choose network and refresh the web page, in bottom of the right hand side, there are URLs that are consists of the page. I found the one with exact format with the example. So it is that! Problem Sloved.

[the page:]（https://climate.weather.gc.ca/climate_data/daily_data_e.html?timeframe=2&hlyRange=%7C&dlyRange=1979-06-01%7C2020-01-31&mlyRange=1979-01-01%7C2018-02-01&StationID=5619&Prov=QC&urlExtension=_e.html&searchType=stnProv&optLimit=specDate&StartYear=1840&EndYear=2020&selRowPerPage=25&Line=145&lstProvince=QC&Day=30&Year=2012&Month=3#&submit=Download+Data）

In conclusion, for a successful debugging, first clearly identify relevent causes, by clearly, means need to be able to articulate the potential cause.（e.g: the data was not successfully downloaded that casued unable to read in data. or, the data had been downloaded but the options of read_csv chosen caused not able to parse data correctly. ) Secondly, exclude theose potentail caused one by one, it is important to exclude those that is independent to other caused first, as sometimes the problem can due to sereral factors. 

Debugging is fun and is also where you learn the most! So when there is a problem, do not be afraid, see it an oppotunity to learn, do not be caught by emotions.

#### another experience is that sometimes error occur due to version updates, the same function in different version might changed options in it. Hence some of the options no longer exists.
