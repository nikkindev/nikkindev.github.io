---
title: Python proverbs
---

*Elementary but enlightening moments during problem-solving summarized as snippets*  
(*Caution: Speed-up could've been problem specific. So, cannot guarantee that it works for all problems*)

- When searching through a dictionary, `not in` > `in`
- Always evaluate variables on the left side in an expression `list[i+1]-list[i] > 0` > `list[i+1] > list[i]`
- Reduce things to **canonical representation** before comparing (strings, fractions, equations,...)
- When itertaing over dictionaries while mutating them simultaneously, use `for k in d.keys()` and not `for k in d`
- Create dics from two lists `d = dict(zip(key_list,value_list))` or with index as keys `d = dict(enumerate(value_list))`
- To create a count dict `for color in colors: d[color] = d.get(color,0) + 1` or  
  `from collections import defaultdict`  
  `d = defaultdict(int)`  
  `for color in colors: d[color] += 1`  
- Grouping with dicts  
  `d = defaultdict(list)`  
  `for name in names:`  
  `....key = len(name)`  
  `....d[key].append(name)`
- Using dict with while loop (Note: Also exhausts the dict)  
  `while d:`  
  `....k,v = d.popitem()`  
  `....print(k,v)`
- Names tuples `TestResults = namedtuple('Results',['failed','attempted'])` prints `Results(failed=0,attempetd=4)`
- Cache decorator (only for pure functions - returns same variable everytime)  
  `@cache`  
  `def web_lookup(url)`  
  `....return urllib.urlopen(url).read()`
- Generator expressions  `sum(i**2 for i in li)` > `sum([i**2 for i in li])`
