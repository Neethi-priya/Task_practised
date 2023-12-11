# Question 1 :

`
import requests
class Priya:
    def __init__(self,url):
        self.url = url
    
    def get_json_data(self):
        response = requests.get(self.url)
        return response.json()
    
    def fetch_data(self):
        for data in self.get_json_data():
            print(data)

    def get_names(self):
        for data in self.get_json_data():
            name_1 = data.get('name').get('common')
            currency = data.get('currencies')
            if currency:
                print("Country:",name_1)
                
                for c,currency_info in currency.items():
                    currency_name = currency_info.get('name')
                    currency_symbol = currency_info.get('symbol')
                    print("currency name :",currency_name)
                    print("currency symbol:",currency_symbol)
                    
    def get_euro_country(self):
        for data in self.get_json_data():
            name_1 = data.get('name').get('common')
            currency = data.get('currencies')
            if currency:
                for currency_1,currency_info in currency.items():
                    if currency_1.lower() == 'eur':
                        print("country_with_euro:",name_1)
        print("\n")
    
    def get_dollar_country(self):
        for data in self.get_json_data():
            name_1 = data.get('name').get('common')
            currency = data.get('currencies')
            if currency:
                for currency_1,currency_info in currency.items():
                    if currency_1.lower() == 'usd':
                        print("country_with_dollar:",name_1)
                
url = "https://restcountries.com/v3.1/all"
json_data = Priya(url)
json_data.get_euro_country()
json_data.get_dollar_country()



`
# question no 2:

`
import requests
class Priya:
    def __init__(self,url,states):
        self.url = url
        self.states = states
    
    def get_json_data(self):
        response = requests.get(self.url)
        return response.json()

    def get_brewery_name(self):
        for state in self.states:
            print("Breweries in", state)
            for data in self.get_json_data():
                brewery_name = data.get('name')
                print("-",brewery_name)
                      
     
                
url = "https://api.openbrewerydb.org/breweries"
states = ['Alaska','Maine','New York']
json_data = Priya(url,states)
json_data.count_breweries()
`

`
def get_json_data(url,states):
        response = requests.get(url)
        return response.json()

def count_breweries(url,states):
        for state in states:
            data = get_json_data(url,states)
            if data:
                count = len(data)
                print("count_breweries_in",state, ":",count)
        

url = "https://api.openbrewerydb.org/breweries"
states = ['Alaska','Maine','New York']
count_breweries(url,states)

`

#types
`
import requests
def fetch_breweries(url, state):
    response = requests.get(url,params={'by_state': state})
    # print("Status_code:", response)
    json_data = response.json()
    return json_data

def brewery_by_type(url, state):
    breweries_data = fetch_breweries(url, state)

    if breweries_data:
        cities_data = {}
        
        for brewery in breweries_data:
            brewery_city = brewery.get('city', 'N/A')
            brewery_type = brewery.get('brewery_type', 'N/A')

            if brewery_city not in cities_data:
                cities_data[brewery_city] = set()

            cities_data[brewery_city].add(brewery_type)

        for brewery_city, brewery_types in cities_data.items():
            print("City: ",brewery_city)
            print("Number of Brewery Types: ",len(brewery_types))
            print("Brewery Types:",', '.join(brewery_types))
            print("\n")               
                            
    else:
        print("Failed to fetch data.")  

url = "https://api.openbrewerydb.org/breweries"
state = ['Alaska', 'Maine', 'New York']
brewery_by_type(url, state)


` 

# websites
`
import requests
def fetch_breweries(url, state):
    response = requests.get(url,params={'by_state': state})
    # print("Status_code:", response)
    json_data = response.json()
    return json_data

def brewery_by_website(url, states):
    for state in states:
        breweries_data = fetch_breweries(url, state)

        if breweries_data:
            breweries_with_websites = [brewery for brewery in breweries_data if 'website_url' in brewery]
            print("Number of breweries with websites in" ,state,":", len(breweries_with_websites))
            print("Breweries with websites in", state)
            
            for brewery in breweries_with_websites: 
                brewery_name = brewery.get('name')
                brewery_website = brewery.get('website_url', 'N/A')             
                print(" - ",brewery_name,":",brewery_website)
            print("\n")               
                                
        else:
            print("Failed to fetch data.")  

url = "https://api.openbrewerydb.org/breweries"
states = ['Alaska', 'Maine', 'New York']
brewery_by_website(url, states)



"""import requests

def fetch_breweries_by_state(url, state):
    try:
        response = requests.get(url, params={'by_state': state})
        response.raise_for_status()
        json_data = response.json()
        return json_data

    except requests.exceptions.RequestException as e:
        print(f"Error fetching data: {e}")
        return None

def count_breweries_by_states(url, states):
    for state in states:
        breweries_data = fetch_breweries_by_state(url, state)

        if breweries_data:
            brewery_count = len(breweries_data)
            print(f"Number of breweries in {state}: {brewery_count}")
        else:
            print(f"Failed to fetch data for {state}.")
url = "https://api.openbrewerydb.org/breweries"
states_of_interest = ['Alaska', 'Maine', 'New York']
count_breweries_by_states(url, states_of_interest) 

#LIST OF THE BREWERIES PRESENT IN THE ALASKA ,MAINE,NEWYORK
import requests

def fetch_breweries_by_state(url, state):
    try:
        response = requests.get(url, params={'by_state': state})
        response.raise_for_status()
        json_data = response.json()
        return json_data

    except requests.exceptions.RequestException as e:
        print(f"Error fetching data: {e}")
        return None

def list_brewery_names_by_states(url, states):
    for state in states:
        print(f"Breweries in {state}:")
        breweries_data = fetch_breweries_by_state(url, state)

        if breweries_data:
            for brewery in breweries_data:
                brewery_name = brewery.get('name', 'N/A')
                print(f"-{brewery_name}")
        else:
            print("Failed to fetch data.")

        print("\n")
url = "https://api.openbrewerydb.org/breweries"
states_of_interest = ['Alaska', 'Maine', 'New York']
list_brewery_names_by_states(url, states_of_interest) 

`