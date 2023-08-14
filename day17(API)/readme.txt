

How to Fetch data Using API 

Visit https://www.themoviedb.org/ and make a account and go to setting and get the API Key

click on Deveolper option and find the Top rated movie url 
https://api.themoviedb.org/3/movie/top_rated

View json format data by using "online Json viewer" and paste there and click on viewer

this is TMBD dataset of top rated Popular movies 
Total page   =  39234
Total result =  784675

Open Vscode 

import pandas as pd
import requests

##copy the API from TMBD website ,and paste in url after?paste API key with api_key
response = requests.get('https://api.themoviedb.org/3/movie/popular?api_key=809f378f7f805f9e86bbf92f7a9c30d5')

response.json()
df = pd.DataFrame(response.json()['results'])[['id','original_title','release_date','vote_average']]

df.head()

# only 500 pages data are extracted just for learning poupose it take 145seconds to complete
for i in range(1,500):
    response = requests.get('https://api.themoviedb.org/3/movie/popular?api_key=809f378f7f805f9e86bbf92f7a9c30d5&page={}'.format(i))
    df_t = pd.DataFrame(response.json()['results'])[['id','original_title','release_date','vote_average']]
    df = df.append(df_t,ignore_index=True)

df.shape
(9980,4)

