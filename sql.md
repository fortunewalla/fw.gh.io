### sql notes

SO let us try some sql notes.

```
select a.id, a.name 
from employees as a 
group by a.id 
having a.id > 100;
```
