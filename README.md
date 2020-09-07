# twitbot
## Description
Run of the mill Python-based Twitter automation. Uses multi-threading to create as many bots as you have API keys for.

Required flags are `-c CON, --config CON` and `-v VIC, --victim VIC` that are a configuration file and list of targets to reply to respectively.

### Config file
The config file lists the accounts you want to automate:
```
@[user 1]
CONSUMER_KEY	[key]
CONSUMER_SECRET	[secret]
ACCESS_KEY	[key]
ACCESS_SECRET	[secret]
@[user 2]
CONSUMER_KEY	[key]
CONSUMER_SECRET	[secret]
ACCESS_KEY	[key]
ACCESS_SECRET	[secret]
.
.
.
@[user n]
CONSUMER_KEY	[key]
CONSUMER_SECRET	[secret]
ACCESS_KEY	[key]
ACCESS_SECRET	[secret]
```
You can list any number of accounts to automate, as long as the config file is in the above format (make note of the tab separation i.e. CONSUMER_KEY\t[key] and don't include the '[' or ']').
### Victims
You must provide a list of accounts you want to reply to at runtime.  This must be a text file in the following format:
```
@username1
@username2
.
.
.
@usernameN
```
Again, this can be any number of Twitter usernames, but keep in mind that the number of users you're replying to and reply delay directly correlate (i.e. as the number of accounts your targeting increases, so does the time it takes to reply to those accounts).  Keep this in mind if you want to be at the top of someone's mentions.
### Options
## Torment Trump
Using the `-t, --torment-trump` option results in a fresh set of "dirt" being pulled from a list of sites, and a custom word list being built from the results:
```
"https://www.dailykos.com/tags/DonaldTrump",
"https://www.cnn.com/search?q=donald+trump",
"https://impeachdonaldtrumpnow.org/case-for-impeachment/",
"https://www.factcheck.org/person/donald-trump/",
"https://www.vice.com/en_us/search?q=donald%20trump",
"https://www.msnbc.com/search/?q=donald+trump#gsc.tab=0&gsc.q=donald%20trump",
"https://www.npr.org/search?query=donald%20trump",
"https://www.wired.com/search/?q=donald%20trump",
"https://lincolnproject.us/news/",
"https://www.bbc.co.uk/search?q=donald+trump",
"https://www.politifact.com/personalities/donald-trump/",
"https://www.reddit.com/search/?q=donald%20trump"
```
The resulting wordlist will then be used to reply to @realDonaldTrump. It is recommended to refresh this content once a week by killing the bots and rerunning with the `-t, --torment-trump` option for a current wordlist.
## Printout
Using the `-o, --printout` option will print all replys, errors, etc to `stdout` (terminal) so you can keep track of the programs operation.
## Requirements
### Python
```
python3
```
### Platform
```
Windows, Linux, MAC
```
### Installation
Clone repo and install requirements
```
git clone https://github.com/pr0l3/twitbot.git
cd twitbot
python3 -m pip install -r requirements.txt
```
## Usage
### Help menu
```
$ python3 twitbot.py -h
usage: twitbot.py [-h] -c CON -v VIC [-o] [-t]

optional arguments:
  -h, --help            show this help message and exit
  -o, --printout        Print all activity to stdout
  -t, --torment-trump   Fetch dirt on Trump and populate 'words' file with it

required arguments:
  -c CON, --config CON  Path to config file
  -v VIC, --victim VIC  Path to username file
```
### Example usage
`python3 twitbot.py -c config.conf -v victims.txt -o -t`
