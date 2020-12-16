+++
title = "AWS Machine Learning Specialty Certification"
date = 2020-12-15T12:22:50Z
author = "Shane Nolan"
keywords = ["", ""]
cover = "/images/avatar.png"
summary = "In this blog post I share my experience studying for the AWS Machine Learning Specialty Exam. From what got me interested in the subject matter to what got me through the exam"
+++

I recently took the opportunity to sit the AWS Machine Specialty Learning Specialty exam, widely regarded as one of the most, if not *the* most difficult AWS exam. Gather round and let me tell you all a tale of mystery and adventure, which attempts to shine some light on this elusive certification by describing how I prepared myself for this exam, and how I ultimately achieved a passing score of 922 / 1000.

- [Learning Materials](#LearningMaterials)
- [Sample Exam Sources](#SampleExamSources)
- [About the Exam](#AboutTheExam)
- [TLDR: Top Tips](#TopTips)

If you've somehow stumbled across this blog without knowing who I am, I work on the Platform Architecture & Security team for ServisBOT, a conversational AI company, where I have been working with AWS on a daily basis for the last 18 months. However, my machine learning journey actually began a few years ago when I built a simple angular application that used simple correlation and regression techniques to predict 
winners of English Premier League football matches, I thought I could use this system to beat the bookmakers and that it would earn me a place in the machine learning hall of fame, but in reality the best I could do was place second in the office fantasy football league. Not bad for someone who has literally zero interest in soccer, but I lost interest and motivation when the millions failed to roll in immediately.

Fast forward twelve months and you find me half way through my Masters degree, signed up for classes in Business Intelligence and Data Mining, suddenly in what felt like the deep end of data analytics and machine learning. I had to simultaneously get to grips with a whole host of technologies and concepts that were new to me, from Qlikview graphs, VLookups and Pivot Tables to Euclidean Geometry, Recurrent Neural Networks and Ensemble Learning Techniques. I designed some small projects to work on in my spare time, nothing fancy, just working on basic techniques and concepts to make sure I had it all clear in my head. For example I used python to build a simple Market Basket Analysis system, and used java (shudder) to build my own k-means clustering algorithm. (I haven't explicitly mentioned it in my top tips for learning ML, but I don't recommend using java for rapidly prototyping your own frankenstein versions of well know machine learning algorithms) After completing both classes, I moved onto Cloud Architecture and my thesis, and as a result, machine learning was once again swept under the rug.

Let's take another trip forward through time and space, all the way to late 2020, at this stage, I had completed my Masters thesis and once again focused my attention on machine learning. This time I had a purpose and an end goal, I was working in the right industry and in the right role where a deeper knowledge of machine learning would allow me to contribute in a meaningful way to an area I had an interest in. So with some unjustified confidence, I put the AWS Machine Learning Specialty certification in my crosshair.

I would estimate that I spent approximately 16 weeks preparing for the exam. This involved roughly 12 weeks studying ML Theory and 4 weeks focusing on AWS ML services. During these 16 weeks I also took 4 practice exams, and I would estimate that I took each exam 3 to 4 times. A lot of guides I've read suggest you take the exams over and over until you're seeing machines learning in your sleep, however I don't subscribe to that learning model, I didn't want to fall into the trap of just memorizing a relatively small subset of possible questions. I feel if you have an understanding of the fundamental concepts, you'll never have to use your memory again (except for some of the equations I'm going to tell you to learn off later). Over the course of 16 weeks my average exam score went from 40% to 90%.

The rest of this blog covers the [learning materials](#LearningMaterials) I used, where I found good [sample exams](#SampleExamSources), a little bit of discussion [about the exam](#AboutTheExam) itself and a [TLDR](#TopTips) that lists my top tips for anyone considering sitting the exam. In an [accompanying post](/posts/aws-ml-study-points) I have also put compiled a more comprehensive list of high level study points, which is more of a brain dump of topics which can be used to focus your study and identify any knowledge gaps.

*There are no referral links on any of the links listed below, and I have no financial interest in any of these resources. I'm recommending them because I have used them and found that they worked for me. I'm sure there are better resources out there, and I can confirm that there are a lot of resources out there that are much worse.*

# Learning Materials
<a name="LearningMaterials"></a>

The AWS documentation was my primary source of learning. The documentation provides direction on what topics are important and require further investigation and attention. More often than not, they will link you to whitepapers or videos for further study, however, whenever I felt the trail ended prematurely I would simply continue my research using Google, usually finding myself reading related threads on reddit and stack-overflow, blogs on medium, articles on wikipedia (I hope this doesn't get me blackballed in academic circles), or using one of the following three books:

- [Data Mining concepts and Techniques](https://www.amazon.co.uk/dp/0123814790) (Third Edition) by Han, Kamber and Pei 
- [Business Intelligence: A Managerial Perspective on Analytics](https://www.amazon.co.uk/dp/1292004878) (Third Edition) by Sharda, Delen and Turban
- [The Hundred-Page Machine Learning Book](https://www.amazon.co.uk/dp/199957950X)

Most of the other blogs I have read regarding exam preparation recommend video courses to take, and although I've heard great things about A Cloud Guru and Sundog, I can't personally recommend a course because I haven't used any. If you decide to focus on video learning, I would recommend doing some research before handing over any cash, read reddit threads, reach out to people on linkedin and try out free trials. A little youtube also goes a long way, just make sure the videos are recent.

Once you feel you have a firm grasp of the fundamentals, it's time to ruin all of that confidence by trying out your first sample exam and realising you still know nothing !

# Sample Exam Sources
<a name="SampleExamSources"></a>

- Frank Kane (Sundog) has a great sample exam with full explanations for every answer. I found this exam to be most representative of the actual exam. It is a bit pricey but Udemy have sales every other week, so its worth keeping an eye on before buying. This exam can be found [here](https://www.udemy.com/course/aws-machine-learning-practice-exam/)

- Abhishek Singh (Some guy) has a number of sample exams, the explanations are not as thorough as Frank Kanes, but can help highlight areas requiring more study. It can be found [here](https://www.udemy.com/course/aws-certified-machine-learning-specialty-full-practice-exams/)

- The official AWS sample questions can be found [here](https://d1.awsstatic.com/training-and-certification/docs-ml/AWS%20Certified%20Machine%20Learning%20-%20Specialty_Sample%20Questions.pdf)

- The official AWS Machine Learning course has some good learning resources as well as a sample exam. Sign up [here](https://www.aws.training/Details/eLearning?id=42183)

# About The Exam
<a name="AboutTheExam"></a>

The exam is split into 4 domains: 

- Data Engineering
- Exploratory Data Analysis
- Modelling
- Implementation & Operations

You have 3 hours to answer 65 scenario based questions and from my experience, the exam had a pretty even distribution across all domains. Each section requires general ML knowledge as well as AWS service knowledge, the first two domains really test your general ML knowhow, and the latter two domains really test your knowledge of the relevant AWS services. 

The questions can be intimidating as they can be quite long with a lot of intricate details hidden in plain sight. Often the crux of the problem will be summed up in the last two or three sentences so it can be useful to quickly skim the end of the question before starting from the start so that you have some context of the problem, and subsequently know what to look for. 3 hours is not a long time so if you can save yourself some time by not reading a long backstory then you should do so. 

It felt like I was asked 6 or 7 questions similar to the below in the actual exam. (useless context followed by black and white question)
```
One trick is to tell 'em stories that don't go anywhere
like the time I caught the ferry over to Shelbyville. 
I needed a new heel for my shoe, so, I decided to go to Morganville, 
which is what they called Shelbyville in those days. 
So I tied an onion to my belt, which was the style at the time. 
Now, to take the ferry cost a nickel, and in those days, 
nickels had pictures of bumblebees on 'em. Give me five bees for a quarter, you'd say.

Now the important thing was I had an onion on my belt, 
which was the style at the time. 
They didn't have white onions because of the war. 
The only thing you could get was those big yellow ones...

Which AWS service is a serverless data integration service 
that makes it easy to discover, extract, prepare, transform, 
combine and load data for analytics, 
machine learning, and application development? 

a) Glue
b) RoboMaker
c) Cost Explorer
d) GuardDuty
```

# Top Tips
<a name="TopTips"></a>

And so we've made it to my Top Tips, Tricks And Tactics For Training Yourself To Think Like A Total Machine Learning Legend. Remember to learn at your own pace and adapt to what works best for you, but I hope these tips will at least help you to structure your own study plan and revision sessions. Make sure to also check out my [high level study points](/posts/aws-ml-study-points). By the time you are ready to sit the exam, you should be able to go through that list and comfortably discuss and/or explain each point or topic.

1. Know all the AWS black box ML services at a high level
    - What are they used for (have sample use cases ready to go)
    - What **other services** can they interact with to build a complete solution
- Know all of the SageMaker Algorithms at a more in depth level
    - What does the algorithm do - be able to explain it to a 5 year old
    - Know a sample use case
    - What **resources** does it need and what **instance type** can satisfy those requirements
    - How does it read in data and does that data need to be in a **specific format**
    - What are the **important associated hyper-parameters**
        - Why are they important / What effect do they have
    - **XGBoost** is Amazons pride and joy, if you get a question about this wrong, you'll find yourself on their list of enemies
- Some services can somehow find their way into questions in **every domain**, know these inside out
    - Athena
    - Glue
    - IAM
    - Kinesis
- Confusion Matrix
    - In my exam I had multiple **2x2** and **3x3** confusion matrix questions
    - You should be able to calculate **Accuracy**, **Precision**, **Recall** and **F1** scores in your sleep
    - Remember I said you shouldn't need to use your memory - this is the exception - memorize these formulae
- TF-IDF Matrix
    - I had two questions on this in the real exam.
    - Matrix Dimensions and **Calculating scores** and **Interpreting results**
- Working with images
    - Know the difference between **Image Classification**, **Object Detection** and **Semantic Segmentation**
- Regularization
    - Relationship between **polynomial complexity** and **model overfitting**
    - L1 v L2
- Know how to read the questions and link them to answers
    - Often you'll find that the question will give you an entire backstory when a backstory is not needed. **Quickly skim the end of the question** before 
    - Look for **key words and phrases** like *minimal cost*, *high performance*, *heavy traffic*, *low effort*, *quickest solution*, these phrases can help you quickly identify the correct answer, or at least quickly disregard some of the incorrect answers.
- Common Sense
    - Making something easier by decreasing its security is **never** the right answer, there were a surprising number of questions with terrible security decisions as possible answers. 
    - AWS like their own services, if you are asked a question where the options are either use Lambda and AWS Comprehend or an on premise dockerized ruby application that uses the 7compass sentimental gem, the answer is more than likely to be the former rather than the latter.
- Trust Your Instinct
    - Don't spend time second guessing yourself. Have confidence in yourself, breathe, read the question carefully, convince yourself why your selected answer is right and why the wrong answers are wrong, slow is smooth and smooth is fast. I did not mark a single answer for review, I made my decision and moved on.

By following the above tips and tricks, I am confident you will gain the proper knowledge to successfully tackle this exam too. I'm looking forward to reading your blog about how you passed !