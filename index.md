### Fortune Walla

_Exploring the world through code & data!_

Articles & notes on a variety of technical, business & cultural topics. 

![]("fwindexlogo.jpg")

<img src="fwindexlogo.jpg"/>

### Notes

[SQL](sql.md) | [R](r.md) | []() | []() | []() | []() | []() | []() 

### Testing Section

Using backticks \` to test variables `x` and `y` and `z`.

\$\alpha+\beta=\gamma\$ latex code $\alpha+\beta=\gamma$.

< tt > tag testing <tt>int x,y=1,2;</tt>. OK 


Code block:
```
import requests
import re
 
while True:
    url = input("Enter the URL: ")
 
    if url == "":
        print("Invalid URL")
        continue
    break
 
html = requests.get(url).text
 
links = re.findall('"(https?://.*?)"', html)
 
for link in links:
    print(link)
```

This website is built using [mmpt](https://github.com/fortunewalla/mmpt/) template.

_© 2022 Fortunewalla_
