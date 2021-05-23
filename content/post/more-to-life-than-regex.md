+++
title = "There's more to life than regex"
date = 2021-05-23T19:29:52Z
author = "Shane Nolan"
keywords = ["", ""]
cover = "/images/avatar.png"
summary = "Sometimes the most fun answer is not always the right answer"

+++

## Intro
Thanks to the combination of a pandemic and the Irish weather, I have a little bit of time to tell you all a tale today. In 1966 Abraham Maslow proposed a theory in his work `The Psychology of Science`, the theory known as `Maslow's hammer` is popularly phrased as **`if all you have is a hammer, everything looks like a nail`** and is one of the phrases I am constantly reminded of when I see people play with regular expressions (myself included). 

## Hang on! A Regular Wha?
A regular expression (regex) is a sequence of characters that specifies a search pattern. Usually used for input validation or by string-searching algorithms for `find` or `find and replace` functionality. This sequence of characters, commonly referred to as a pattern can vary dramatically in complexity, incorporating one to one matching, or more intelligent matching with built in logic - for example the pattern `^[a-fA-F]{1,2}(?=t)` would match any letter or pair of letters between a and f (or A and F) that is at the start of a line and followed immediately by a t. The intricacies of regex and pattern matching is outside the scope of this blog, but I would highly recommend doing some independent learning, it is an amazingly powerful and useful skill to have.

## Get to the point
Alright, so I'm often asked to help out with regex problems and thats not a complaint, on the contrary, I love helping out with pattern matching puzzles. However this week a friend of mine asked for help writing a pattern to add to their bash script which would pull out string values from a simple JSON object.

Given the following pattern
```
[{"Name":"America","Value":"dallas-texas"},{"Name":"Europe","Value":"paris-france"}]
```
We want to print
```
dallas-texas
paris-france
```

## Can it be done with a regex - YES
If you like your solutions quick and dirty (emphasis on the dirty), then we can do the following.

 - echo our json
 - pipe the output to a grep command
 - use greps -o flag to print only the matched (non-empty) parts of a matching line, with each such part on a separate output line
 - use a capture group with a repeating character sequence to pull out the values which contain lower case letters and hyphens `([a-z-]*)`
 - sort the results and output the unique values

```bash
echo [{"Name":"America","Value":"dallas-texas"},{"Name":"Europe","Value":"paris-france"}] | grep -o 'Value:\([a-z-]*\)' | cut -d: -f 2 | sort | uniq
```
I warned you it was dirty. Time to take a shower and try another approach.

## Should it be done with a regex - NO
I'll take this use case to introduce you all to a friend of mine called [jq](https://stedolan.github.io/jq/), a lightweight json parser that can do incredibly cool shit with json data. Cool here being a subjective term, if you're the kind of person who enjoys free soloing blindfolded up K2 then you might not get the same buzz off of jq that I do. But onwards with the blog post, once you've installed jq you can achieve the exact same result as before, but using much more simple logic.

 - echo our json
 - pipe the output to a jq command
 - use jqs -r flag to write directly to standard output rather than formatting results as JSON strings (with quotes)
 - specify the items you wish to capture using a jsonpath-esque pattern (so root followed by the Value key for each array item) `.[].Value`

```bash
echo '[{"Name":"America","Value":"dallas-texas"},{"Name":"Europe","Value":"paris-france"}]' | jq -r ".[].Value"
```
Beautiful. I'll add jq to the list of things I'd love to go into in more detail in a future blog. I just wanted to introduce it here as a lesson in why regex is not always the right answer.

## Conclusion
Enjoy your life while you're young, go out and have fun, use as many dirty regular expressions as you like. But when it's time to settle down and really evaluate your life, start thinking about what else is out there. My friend jq is only one of the hidden gems you'll find on the internet. In fact, maybe the language you're using already has libraries that will do what you need without needing pattern matching at all. If you've ever pretended to read the Art of War by Sun Tzo you might remember the proverb `A clever fighter is one who not only wins, but excels in winning with ease.`