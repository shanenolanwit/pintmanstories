+++
title = "Whats the story with NLP"
date = 2021-02-01T23:31:09Z
author = "Shane Nolan"
keywords = ["", ""]
cover = "/images/avatar.png"
summary = "An introduction to Natural Language Processing (NLP) and an exercise in using regular expressions (regex) to build a simple knowledge extraction system"

+++
## Once upon a time . . 
Back in the days when you could go into a shop with a pound and come out with a bag of monster munch, a can of coke,
and still have a few pence left in your back pocket, most text mining applications relied on a technique known as bag-of-words.
This technique basically took all the words in a given piece of text, disregarding their order, not caring about their context and used 
each words frequency in order to classify the entire document using predefined classes, or just clustering them using natural groupings.

This worked great for simple tasks like spam filtering - does my bag contain viagra or a Nigerian prince? If so, you've got yourself a big ol bag of spam, 
time to chuck it in the bin. (Top tip: If you have recently bought viagra from a Nigerian website and received no confirmation email - try checking your spam box).
The problem with this is that order and structure are actually really important when trying to form a true understanding of any given text.
There was an [academic paper](https://www.researchgate.net/publication/228341727_Knowledge_extraction_for_clinical_question_answering_Preliminary_results) 
published in 2005, where the researchers used a bag of words approach as a baseline approach to interpreting medical documents for 
knowledge extraction, they simply asked the question - does this document contain an answer to a given question, 
they found that this bag-of-words approach gave them the correct answer 53% of the time. If you were thinking of implementing this system yourself, 
perhaps a better investment would be a coin that you can flip and base your decision on the outcome.

This is where Natural language processing (NLP)​ comes in, a field of artificial intelligence (AI)
and computational linguistics that converts human language into numeric data, this formalised data can then be consumed, 
manipulated and interpreted programmatically. To extract relevant knowledge (novel and useful patterns and relationships) from text it needs to overcome challenges such as word disambiguation (same word different meaning) and syntactic ambiguity (different sentence same meaning), in order to tag/classify each word based on the context in which it was used. Algorithms and mathematics play an important part, but one of the most widely used and crucial components of NLP is [WordNet](https://wordnet.princeton.edu/) - a hand-coded database of English words, their definitions, sets of synonyms, antonyms and the relationship between those sets. Not only 
does WordNet allow us to determine context, it enables us to detect sentiment. Sentiment analysis answers the question “how does someone feel about a given topic”.
It typically does this in one of two ways, explicit analysis, where a piece of text directly expresses an opinion ("I love ice cream"), and implicit, where the text simply implies an opinion (“This beer is warm”). Historically, explicit analysis has been the basis for most sentiment detection algorithms. however current trends attempt to consider both implicit and explicit rules. 

## Build Your Own WordNet - Regex Fun
So lets forget about WordNet and go back to basics with some simple examples of knowledge extraction using a context aware approach versus a no context (bag-of-word) type approach. In this first example,  we'll use a simple rule that identifies nouns by extracting words beginning with capital letters.
```javascript
const sentence = "Shane went to Prague last Monday";
const nounRegex = /\b([A-Z][a-z]+)\b/g;
const matches = sentence.match(nounRegex);
console.log(matches)
```
this prints
```
[ 'Shane', 'Prague', 'Monday' ]
```
awesome, we identified the major players, but what about this next example where the `place` is not referenced directly
```javascript
const sentence = "Anna went to the big city last Friday";
const nounRegex = /\b([A-Z][a-z]+)\b/g;
const matches = sentence.match(nounRegex);
console.log(matches)
```
this prints
```
[ 'Anna', 'Friday' ]
```
Well that was ok, we know about `who` and `when` but missed out on the `where`. This is because we are relying on single words, 
whereas a better approach would be to use some other tricks to identify the nouns. One such trick is finding descriptive adjectives and taking whatever 
word comes next. In this next example we use a simple dictionary - `big|old` and a `positive lookbehind` to find our nouns 
```javascript
const sentence = "my old friend went to the big city last Friday";
const adjectives = ["old", "big"]
const nounRegex = new RegExp(`(?<=(${adjectives.join('|')})\\s)([a-z]+)|\\b([A-Z][a-z]+)\\b`, 'g');
const matches = sentence.match(nounRegex);
console.log(matches)
```
this prints
```
[ 'friend', 'city', 'Friday' ]
```
Alright, excellent, combining our capital letter and adjective rules we have extracted information about the major entities being discussed in the text. The 
next addition to our rule set extends the dictionary approach to allow us to identify nouns, without requiring capital letters or pre-pended adjectives.

```javascript
const sentence = "Anna took a plane to the big city on Friday";
const adjectives = ["old", "big"]
const knownNouns = ["car", "bus", "plane", "train"]
const nounRegex = new RegExp(`(?<=(${adjectives.join('|')})\\s)([a-z]+)|\\b([A-Z][a-z]+)\\b|(${knownNouns.join('|')})`, 'g');
const matches = sentence.match(nounRegex);
console.log(matches)
```
prints
```
[ 'Anna', 'plane', 'city', 'Friday' ]
```
Alright so we have the ability to extract entities, but how do we turn this into **knowledge**? The answer is determining the `context` of the 
question being asked. In the following example we first determine what type of question is being asked and using a rule that matches the type. 
The interesting rule here is if the question is asking `what`, which requires a second layer of rules.
```javascript
const knownNames = ["anna", "shane"]
const knownPlaces = ['paris', 'mcdonalds']
const knownTimes = ['monday', 'friday']
const context = {
    who: (question, text) => text.match(new RegExp(`${knownNames.join('|')}|^[a-z]+`))[0],
    where: (question, text) => text.match(new RegExp(`${knownPlaces.join('|')}`))[0],
    when: (question, text) => text.match(new RegExp(`${knownTimes.join('|')}`))[0],
    what: (question, text) => {
       const entity = question.match(new RegExp('(?<=(what)\\s)([a-z]+)'))[0];
       if(['city', 'country', 'place', 'restaurant'].includes(entity)) {
            return text.match(new RegExp(`${knownPlaces.join('|')}`))[0];
       } else if(['time','day'].includes(entity)){
           return text.match(new RegExp(`${knownTimes.join('|')}`))[0];
       } else {
           return 'dunno'
       }
    }
}
const clean = (text) => text.toLowerCase().replace("'", "");
const answerQuestion = (q, t) => {
    console.log('======================');
    console.log(`Question: ${q}`);
    console.log(context[clean(q).split(' ')[0]](clean(q),clean(t)))
}
console.log("Shanes Wonderful Question Answering Regex Machine")
const textOne = "Anna went to Paris on Friday";
const textTwo = "joe took a spin to mc'donalds";
answerQuestion('who went to paris?', textOne);
answerQuestion('where did anna go on monday', textOne);
answerQuestion('when did anna go to paris', textOne);
answerQuestion('what city did anna visit', textOne);
answerQuestion('what day did anna go to paris', textOne);
answerQuestion('what restaurant did joe visit', textTwo);
answerQuestion('who bought all this mcdonalds?', textTwo);
answerQuestion('what car did joe take', textTwo);
```
that will output this
```
Shanes Wonderful Question Answering Regex Machine
======================
Question: who went to paris?
anna
======================
Question: where did anna go on friday
paris
======================
Question: when did anna go to paris
friday
======================
Question: what city did anna visit
paris
======================
Question: what day did anna go to paris
friday
======================
Question: what restaurant did joe visit
mcdonalds
======================
Question: who bought all this mcdonalds?
joe
======================
Question: what car did joe take
dunno
```
Amazing. A small and simple example but highlights how context can be incorporated into our entity detection to extract knowledge. 
Next we'll look at some examples of sentiment analysis - `context` v `no context`. This first example has a bag of positive words and a 
bag of negative words. Given a piece of text, we count does the text contain more words from the positive bag or the negative one, and use  
this result to determine the sentiment.
```javascript
const positive = ["good", "great"]
const negative = ["bad", "awful"]
const detectSentiment = (text) => {
    console.log('======================')
    console.log(text)
    const positiveMatches = text.match(new RegExp(`${positive.join('|')}`, 'g'))
    const negativeMatches = text.match(new RegExp(`${negative.join('|')}`, 'g'))
    const pCount = positiveMatches ? positiveMatches.length : 0
    const nCount = negativeMatches ? negativeMatches.length : 0
    if(pCount > nCount){
        console.log('positive')
    } else {
        console.log('negative')
    }
}
```
this script will output the following
```
Shanes Wonderful Sentiment Analysis Regex Machine
======================
overall good experience
positive
======================
the food was good, the staff were great, even the bed was good
positive
======================
the food was not good, the staff were not great, but the bed was not bad
positive
======================
everything about this place was awful
negative
======================
this place was not good
positive
```
Well that was a disaster, the code sees the word good and assumes it is positive, we need some context here - positive and negative words actually mean the 
opposite when pre-pended by the word `not`. Lets add this one simple `negative lookbehind` rule and run our test set again.

```javascript
const positive = ["good", "great"]
const negative = ["bad", "awful"]
const detectSentiment = (text) => {
    console.log('======================')
    console.log(text)
    const positiveMatches = text.match(new RegExp(`(?<!not\\s)(${positive.join('|')})|(?<=not\\s)(${negative.join('|')})`, 'g'))
    const negativeMatches = text.match(new RegExp(`(?<!not\\s)(${negative.join('|')})|(?<=not\\s)(${positive.join('|')})`, 'g'))
    const pCount = positiveMatches ? positiveMatches.length : 0
    const nCount = negativeMatches ? negativeMatches.length : 0
    if(pCount > nCount){
        console.log('positive')
    } else {
        console.log('negative')
    }
}

console.log("Shanes Wonderful Sentiment Analysis Regex Machine")
detectSentiment("overall good experience");
detectSentiment("the food was good, the staff were great, even the bed was good");
detectSentiment("the food was not good, the staff were not great, but the bed was not bad");
detectSentiment("everything about this place was awful");
detectSentiment("this place was not good");
```
this prints
```
Shanes Wonderful Sentiment Analysis Regex Machine
======================
overall good experience
positive
======================
the food was good, the staff were great, even the bed was good
positive
======================
the food was not good, the staff were not great, but the bed was not bad
negative
======================
everything about this place was awful
negative
======================
this place was not good
negative
```
Success! Using some simple rules and patterns we have shown how context can empower our language interpretation and knowledge extraction.  

##  Conclusion
Natural Language Processing (NLP) essentially, aims to turn text into data for analysis and knowledge extraction. It achieves this using a variety of text mining techniques including text categorization, intent detection, entity extraction, sentiment analysis, document summarization, and entity relation modeling. These techniques involve studying word frequency distributions, pattern recognition, information extraction, association analysis, visualization, and predictive analytics.
This blog post introduced some simple counting and pattern recognition for entity extraction and sentiment analysis. Future blogs will expand on these techniques but this is the end of the story for now. Go forth and regex.