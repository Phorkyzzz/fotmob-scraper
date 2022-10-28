import requests
from bs4 import BeautifulSoup
import json

base_url = 'https://www.fotmob.com/match/'
match = str(input('Please enter the match id: '))
url = base_url+match

#Use requests to get the webpage and BeautifulSoup to parse the page
res = requests.get(url)
soup = BeautifulSoup(res.content, 'lxml')
scripts = soup.find_all('script')

#get the last string
strings = scripts[-1].string

#delete the last bit, to get just the usefull infromation
ind_end = strings.index('"page":')
json_data = strings[:ind_end]
repl = "}"
json_data = json_data[:-1] + repl
data = json.loads(json_data)

#create some dataframes, the important ones
df_general = data["props"]["pageProps"]["general"]

df_content = data["props"]["pageProps"]["content"]

df_shots = df_content["shotmap"]["shots"]
