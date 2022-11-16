_Exploring the world through code!_

[SQL](sql.md) | [Git](git.md) | [GitHub](github.md) | []() | []() | []() | []()

test1:

![[fwindexlogo.jpg]]

test2:

![[glider.svg]]

test3:

<img src="fwindexlogo.jpg" />

test4:

<img src="glider.svg" />

This is some random `x` and `y` and `z`.

Also this is some latex code $\alpha+\beta=\gamma$. Hope all this works.

Also one more thing <tt>int x,y=1,2;</tt>. OK then.

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

_© 2022 Fortunewalla_
