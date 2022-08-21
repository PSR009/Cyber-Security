# OSINT

## Tools
## Twint for Twitter

- An advanced Twitter scraping & OSINT tool written in Python
- Requires no Twitter APIs and no twitter login
- Scrape a user's followers, following, Tweets and more while evading most API limitations.
#### Command-Line Options
  ```
  -u <twitter-handle>
  –limit 20
  -s "<string-search>"
  -o <file>.json -json
  –min-likes 100
  –since 2021-04-28
  –year 2016
  –images
  –near <location>
  –g="<latitude>,<longitude>,<radius-in-km>"
  ```
  
#### Python Scripting

  ```python
  import twint
  from datetime import datetime
  
  # Example 1
  
  search = input("Search: ")
  city = input("Location: ")

  c = twint.Config()
  c.Search = search
  c.Near = city
  c.Limit = 20
  c.Popular_tweets = True

  twint.run.Search(c)

  # Example 2
  
  today = datetime.now().strftime('%Y-%m-%d')
  
  c = twint.Config()
  c.To = "<handle>"
  c.Since = today
  c.Hide_output = True
  c.Store_object = True

  twint.run.Search(c)

  tweets = twint.output.tweets_list

  mypeople = []

  for tweet in tweets:
      mypeople.append(('{}'.format(tweet.username)))

  print(mypeople)

  for user in mypeople:
      c = twint.Config()
      c.Username = user
      c.Limit = 20
      twint.run.Search(c)
  ```
- [For More](https://github.com/twintproject/twint) 
## Osintgram for Instagram

- Dummy account is needed
- Create config directory with username.conf, pw.conf and settings.json
  - With their contents as "username", "password" and "{}"
- [For More](https://github.com/Datalux/Osintgram)

## PhoneInfoga for Phone Numbers

- Get Google Search Dork Requests
  - General footprints
  - Social network footprints
  - Individual footprints
  - Reputation footprints
  - Temporary number providers footprints
- OVH telecom scan

#### Command-Line
```
$ phoneinfoga scan -n <phone-number>
$ docker run -it sundowndev/phoneinfoga scan -n <phone-number>
```
#### Web UI
```
$ phoneinfoga serve -p 8080
$ docker run -it -p 8080:8080 sundowndev/phoneinfoga serve -p 8080
```
- [For More](https://github.com/sundowndev/phoneinfoga)

## Sherlock

- Hunt down social media accounts by username across social networks 

```
$ python3 sherlock --timeout 1 <username>
```
- [For More](https://github.com/sherlock-project/sherlock)


## Google Dorks

- Things that go in the Search Bar
```
intitle:"webcamxp 5"
```

#### References
YouTube
- [Hacker Skills // OSINT (Information Gathering)](https://www.youtube.com/watch?v=SvO_FDa8AIs&list=PLIhvC56v63IJ9SYBtdDsNnORfTNFCXR8_)
