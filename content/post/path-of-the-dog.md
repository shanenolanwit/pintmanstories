+++
title = "Machine Learning 101 - The Path of the Dog"
date = 2021-08-24T18:22:50Z
author = "Shane Nolan"
keywords = ["", ""]
cover = "/images/avatar.png"
summary = "You must not stray from the path of the dog - ML 101"

+++

## Introduction
In a previous life the possibility of getting to design and build an identity management system was always on my horizon. I recently revisited the idea as I believe it poses lots of interesting challenges that I did not fully appreciate at the time. One of the challenges involved in managing a 
system where users are constantly joining, moving and leaving, is correctly allocating roles to users who have a wide variety of permissions but no explicitly defined role. Traditional rule based logic may fail to correctly allocate roles if user permissions are not uniform. However, machine learning can help us group users into clusters based on their permissions, or we can use classification techniques to recommend suitable roles. 
One of the techniques we can use to determine how to classify a user is calculating the similarity of a user 
and a prototypical user of each available class. Similarity can be measured in a variety of ways, most notably, euclidean distance and/or cosine distance.

## Dimensional Chaos
Don't listen to your friends when they tell you there is a single best way to calculate the distance between points in n-dimensional space.
Using a simple example of document comparison, lets say we have a datastore of documents, some documents are about dogs, and some are about cats. When a new document 
is uploaded, we want to automatically determine which kind of document this is. We either don't have the time to read it, or there are no pictures of dogs, so we're just 
not interested in reading it. Instead we run it through some program which extracts the text and calculates the word frequency to determine which type of document it is. If it has more mentions of `dog` then its a doggy doc, if it has more mentions of `cat` then its a kitty cat doc.
```
Document one contains no occurrences of dog, and no occurrences of cat
Document two contains 10 occurrences of dog, and 2 occurrences of cat
Document three contains 4 occurrences of dog, and 1 occurrences of cat
Document four contains 5 occurrences of dog, and 25 occurrences of cat
Document five contains 8 occurrences of dog, and 60 occurrences of cat
```
So the simple solution is whichever number is greater determines the type of doc? Sounds good in this document, but this is a 2 dimensional solution and can not scale. 
As simple humans we observe the world in 3 dimensional space, but in reality we encounter a lot of n-dimensional problems. Think of the last time you played Top Trumps - you can't judge a dinosaur by its *killer rating* alone, you need to factor in things like height, weight, length, intelligence and age. To plot these points on a graph you would need a 6 dimensional graph. We can do the maths but we simply can not display 6 dimensions in a 3 dimensional world. 
![toptrumps](/images/toptrumps.jpeg)

If you say so Shane . . 


## So what is the solution
As we mentioned before, we can't visualize n-dimensional space but we can still conceptualize it and perform mathematical operations that scale to meet the number of dimensions. Which brings us back to Euclidean and Cosine distances. Lets use some simple pictures in a dimension we can draw to show how these calculations work and why one can be better than the other. We'll then show how the calculations can easily be adapted to n-dimensions and then we'll all go get some rest.
I'm not a mathematician, in fact, I had to use autocorrect to even spell mathematician so my definitions may not be textbook, but they might help you understand enough to go 
research and understand the grown up definition.

**Euclidean distance** is the `as the crow flies` distance between two points in space. If you grabbed your rule and pencil, and connected two points, the distance of that connecting line is your euclidean distance.

**Cosine distance** measures the cosine of the angle between lines drawn from two given points to a common origin, or more simply put - given an origin how far do you have to stray from the path to one point to get to the other. It is the great equalizer when the magnitude of a points values are not important.

![euccos](/images/euccos.png)

The above is a visual representation of euclidean distance (d) and cosine distance (θ). While cosine looks at the angle difference between two points from a common origin, euclidean distance measures the physical distance between the points themselves.

Alright, forget about the dinosaurs, lets jump back to the cats and dogs. Lets plot some data. The python snippets use matplotlib to graph our data points.
```
import matplotlib.pyplot as plt

x = [0, 10, 4, 5, 8]
y = [0, 2, 1, 25, 60]

plt.xlabel('dog')
plt.ylabel('cat')

plt.scatter(x, y)
```
![catdogs1](/images/catdogs1.png)

In the diagram above we have a document at (4,1) which represents a document about a dog (4 mentions of a dog, 1 mention of a cat), we also have a document at (8,60) which represents a document about a cat (8 mentions of a dog, 60 mentions of a cat). So lets take a look at the document at (5,25) . . thats 5 mentions of a dog, 25 mentions of a cat. Our intuition tells us this is a document about a cat, but if we judge a documents class by the euclidean distance to its prototypical document, we actually get the opposite answer.

```
x = [0, 10, 4, 5, 8]
y = [0, 2, 1, 25, 60]

plt.xlabel('dog')
plt.ylabel('cat')

plt.scatter(x, y)
plt.plot([4,5], [1,25], color="blue",  label="distance to dog")
plt.plot([5,8], [25,60], color="red", label="distance to cat")

dist1 = euclidean((4,5), (1,25)) 
dist2 = euclidean((5,8), (25,60))

print(f"distance to dog {dist1}")
print(f"distance to cat {dist2}")

plt.legend()
plt.show()
```

![catdogs2](/images/catdogs2.png)

While it may be true that the word frequency values of the `x` document are closer to that of the `dog` document, the length of the document should not determine its context, , thus, highlighting the weakness in using Euclidean distance. We need to forget about the magnitude of the words, so we switch to cosine distance - if we observe the path from the origin to the dog document, how far must we stray from the path of the dog to reach the point `x`, similarly how far must we stray from the path of the cat to get to `x`. Lets plots these paths and observe the results.

```
x = [0, 10, 4, 5, 8]
y = [0, 2, 1, 25, 60]

plt.xlabel('dog')
plt.ylabel('cat')

plt.scatter(x, y)
plt.plot([0,4], [0,1], color="blue",  label="dog")
plt.plot([0,5], [0,25], color="black", linestyle='--', label="x")
plt.plot([0,8], [0,60], color="red", label="cat")

plt.legend()
plt.show()

dist1 = cosine((4,5), (1,25))
dist2 = cosine((5,8), (25,60))

print(f"distance to dog {dist1}")
print(f"distance to cat {dist2}")
```

![catdogs3](/images/catdogs3.png)

This is more like it. If you were standing at the origin and looking down the path to `x` you would have to turn much further to the right to follow the path of the dog, than you would have to turn left to follow the path of the cat. This observation results in `x` being correctly classified as cat.

## How did we end up here
Ok so we've discussed invisible dimensions, dinosaurs, cats and dogs, back to our unknown user being added to our identity management system, we use their permissions to build an n dimensional matrix, and use the cosine difference between them and the prototypical employees of each department to determine which role they should be assigned. These users have a very small number of properties so could probably be determined by eye, but the basic design concept is built with scaling in mind.

This snippet is a simple NodeJS representation of the cosine distance
```
module.exports = (A,B) => {
    let dotproduct = 0;
    let mA = 0;
    let mB = 0;
    for(i = 0; i < A.length; i++){ 
        dotproduct += (A[i] * B[i]);
        mA += (A[i]*A[i]);
        mB += (B[i]*B[i]);
    }
    mA = Math.sqrt(mA);
    mB = Math.sqrt(mB);
    const similarity = (dotproduct)/((mA)*(mB))
    return 1 - similarity;
}
```

Proof of concept Identity class
```
module.exports = class Identity {
    constructor(config){
        this.config = config;
    }

    get(prop){
        return this.config[prop] ? 1 : 0
    }

    buildMatrix(){
        return [
            this.get('mysql_read'),
            this.get('mysql_write'),
            this.get('mysql_admin'),
            this.get('ddb_read'),
            this.get('ddb_write'),
            this.get('ddb_admin'),
            this.get('hubspot_read'),
            this.get('hubspot_write'),
            this.get('hubspot_admin'),
            this.get('sales_dept'),
            this.get('tech_dept'),
            this.get('hr_dept'),
        ]
    }
}
```

Running some comparisons
```
const diff = require('./cosineDistance');
const Identity = require('./Identity')

const hubspotUser = new Identity({
    hubspot_read: 1, hubspot_write: 1, sales_dept: 1
})

const hubspotAdmin = new Identity({
    hubspot_read: 1, hubspot_write: 1, hubspot_admin: 1, sales_dept: 1
})

const techGuy = new Identity({
    mysql_read: 1, mysql_write: 1, ddb_read: 1, ddb_write: 1, tech_dept: 1 
})

const techAdmin = new Identity({
    mysql_read: 1, mysql_write: 1, ddb_read: 1, ddb_write: 1, mysql_admin: 1, ddb_admin: 1, hubspot_admin: 1, tech_dept: 1
})

console.log(diff(hubspotUser.buildMatrix(),hubspotAdmin.buildMatrix()))
console.log(diff(techGuy.buildMatrix(),hubspotAdmin.buildMatrix()))
console.log(diff(techGuy.buildMatrix(),techAdmin.buildMatrix()))
console.log(diff(techAdmin.buildMatrix(),hubspotAdmin.buildMatrix()))

const unknownUser = new Identity({
    hubspot_write: 1, mysql_read: 1, sales_dept: 1
})

console.log('unknown user')

console.log(diff(unknownUser.buildMatrix(),hubspotUser.buildMatrix()))
console.log(diff(unknownUser.buildMatrix(),hubspotAdmin.buildMatrix()))
console.log(diff(unknownUser.buildMatrix(),techGuy.buildMatrix()))
console.log(diff(unknownUser.buildMatrix(),techAdmin.buildMatrix()))


// prints
// 0.1339745962155613
// 1
// 0.20943058495790523
// 0.8232233047033631
// unknown user
// 0.33333333333333326
// 0.42264973081037416
// 0.7418011102528389
// 0.7958758547680685

```

Which produces two outputs. The first set outputs compares users from known classes - a hubspot user and a hubspot admin (0.13 quite similar), it then compares a tech guy and a hubspot admin (1 which is not similar at all), it compares the tech guy with the tech admin (0.23 quite similar), and then it compares the tech admin and hubspot admin (0.82 not very similar).

It then compares an unknown user with each know user class. Again because we have very few properties we can probably make an educated guess about what role someone with hubspot write access, mysql read access who works in the sale department should be given, but we'll go through the exercise anyway. The unknown user is compared to the hubspot user (0.33 very similar), the hubspot admin (0.4 not so similar but not a million miles off), the tech guy (0.74 not at all similar), and the tech admin (0.79 even further away again).

This can be interpreted as - the minimum distance between this unknown user and a known user is 0.33 which is the distance between this user and the hubspot user, thus we would recommend that this new user be given the hubspot user role. We could also add warnings to say that the score is not perfect so the user may be missing a permission or may have some excess privileges. 

## Conclusion
There are so many rabbit holes and tangents when it comes to even the most basic machine learning problem. Hopefully I haven't made things even more confusing. If nothing else, remember the path of the dog

![pathofthedog](/images/pathofthedog.png)