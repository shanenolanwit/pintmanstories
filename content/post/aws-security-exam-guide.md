+++
title = "My Guide to the AWS Security Specialty Exam"
date = 2021-07-18T18:29:52Z
author = "Shane Nolan"
keywords = ["", ""]
cover = "/images/avatar.png"
summary = "The view is worth the climb when it comes to climbing this particular cert"

+++

I recently took the opportunity to sit the AWS Security Specialty exam, widely regarded as one of the more difficult AWS exams. To make it extra spicy on myself, I sat the exam online through Pearson Vue. So turn off the television, in fact, why don’t you turn off all the lights except for the one over your favorite chair? and we’ll talk about security here in the dim. 

- [About the Exam](#AboutTheExam)
- [TLDR: Top Tips](#TopTips)

Picture the scene, it's 9pm on a Thursday evening in the middle of a heatwave in a country known for being bitterly cold. You're sweating but you're not sure is it because you're nervous about the exam, or because it's 28 degrees in your office which is becoming more and more like a sauna with every passing minute. The exam proctor asks you to take them on a tour of your office, to make sure the windows and blinds are shut and the door is closed, your amateur version of cribs ends with you standing in the middle of the room and spinning 360 degrees. You're warned that if anyone interrupts the exam, if your internet connection fails, if you look away or if your dog barks, your exam can be cancelled and you will not be refunded. So you sit down, the deathly silence and the extra pressure of someone watching your every move is causing that small trickle of sweat to intensify. Why did you buy a leather gaming chair? At least you wore a white t-shirt. 

![nervous](/images/nervous.png)


It's no ordinary Summer, Covid-19 has effectively kept you as a prisoner in your house for the last 18 months. . But restrictions are starting to ease, and the weather is starting to improve. The only thing that can ruin your evenings now is knowing that you have an exam to study for. You know there's a chance that if you take a few weeks off study to enjoy the weather that you'll likely forget everything you've learned to this point. So here you are, you originally planned to sit the exam in September but you decided at 6pm that you'd rather sit the exam at 9pm and just be done with it. 

So hot.

Twenty minutes in, you're comfortable gaming chair is comfortable no more. You sit back to gather your thoughts and adjust how you're sitting, before you have a chance to breathe a sigh of relief you get a message from the exam proctor that you need to stop moving around, that you need to stay centre frame in the webcam view. Now you're sitting still, the heat is making it hard to read the questions, most questions look like novels, some questions with 5 possible answers, each option almost as long as the question, but you somehow get through all 65, and still have enough time to review your answers, almost an hour in fact. 

That was the longest 2 hours of your life. you've lost about half a stone in weight at this stage. 

Half way through reviewing your answers, in the middle of trying to decipher some obfuscated IAM policy, you get another message from the exam proctor, this time its a FINAL WARNING, please stop moving your lips or your exam will be cancelled. You didn't even know your were moving your lips, you continue your revision, pretty much holding your breath to ensure you don't move your lips, but the heat and the sweat, the uncomfortableness combined with this new shortage of oxygen has made you decide that nothing matters anymore, your goal is now survival, if you don't finish this exam in the next minute, you might actually die in a pool of your own sweat. So you click finish review, submit exam.

![sweating](/images/sweat.png)

You've passed. That wasn't so bad was it?



# About The Exam
<a name="AboutTheExam"></a>

It's really difficult to say how long I spent studying. Unlike the machine learning specialty exam, security is a more integral part of my everyday job. By just working with AWS, graphing solutions and writing code you pick up on some nuances around some of the areas featured heavily in the exam. If I had to guess, I would estimate that I spent approximately 30 - 40 hours  over a period of 3 months specifically preparing for this exam. That's 3 practice exams taken 3 times, each taking around 2 hours. After each exam, I would read through the questions I got wrong and write down why the right answer was right and why the wrong answers were wrong. On top of this I watched the chapter summary videos of `A Cloud Guru's` guide to AWS Security, only watching more in depth videos if something in the summary didn't make enough sense on its own.

The exam is split into 5 domains: 

- Incident Response
- Logging and Monitoring
- Infrastructure Security
- Identity and Access Management
- Data Protection

You have 3 hours to answer 65 scenario based questions and from my experience, the exam had a pretty even distribution across all domains, with slightly more Identity and Access Management questions and slightly fewer Incident Response questions. I will avoid taking future exams from home, if possible, sitting the exam in a physical exam centre has so many benefits - you can brainstorm answers using a whiteboard and marker, you can take a supervised water break, you don't have to sit perfectly still, and you don't have to worry about your exam being cancelled due to a poor internet connection or loud children.

# Top Tips
<a name="TopTips"></a>

Difficulty is subjective, but I've outlined some tips which should help you structure your own study plan. 

 - Policies. Look at policies until you are seeing them in your sleep. Its important to know how IAM, S3 and KMS policies work together. Know that Deny always trumps Allow and assume everything is off limits until a policy allows it.
 - Cloudtrail. This comes up a lot in the practice exams. What do the logs contain, where should the logs be stored and how is this configured. Who should be allowed view them. How can you validate that they haven't been tampered with.
 - Cloudwatch. Featured a lot, but usually as part of another question. A lot of services will rely on cloudwatch alarms to notify parties of, or trigger a process to remediate a threat.
 - So many services, so little time. Know the high level differences between Cloudtrail, Cloudwatch, Config, Inspector, Trusted Advisor, Artifact, GuardDuty, Macie, Shield, and WAF. Just knowing the difference between these services will allow you to eliminate wrong answers. 
 - Key Rotation. Learn the different types of keys, how to rotate them and how often they rotate (if they rotate automatically). How to provide your own key material, when should you provide your own key material . . . what is key material.
 - VPCs. What can flow logs give you. Why use endpoints? NACL v Security Groups (Stateless v Stateful). Explain Direct Connect and VPC peering in 3 sentences or less.
 - Active Directory. Read about the AWS Directory Service.  AD is the trusted party. AWS is the relying party. Direction of access is the opposite of the direction of trust.
 - Perfect Forward Secrecy. WHat is it, why is it important and how do you set it up. (Read the docs for Cloudfront and Elastic Load Balancer)
 - On Prem Interactivity. Read extensively about Systems Manager on the AWS site, and google what Code Deploy is.
 - Balance the load. Difference between classic and application load balancers. I don't know how many times I forgot that a public facing application load balance can route traffic to private subnets. So now you know.
 - Encryption at rest and in transit. Know what your options are when working with Dynamo and S3. The Dynamo Encryption Client might sound made up, but it isn't.
 - Certs. Creating subordinate Certificate Authorities. Global certs v regional certs. Actually open AWS and set up https between client and Cloudfront & between Cloudfront and an Application Load Balancer. You will know about certs by the end of this exercise. If you get it right on your first go without help, then why are you wasting your time reading this blog?



By following the above tips and tricks, I am confident you will gain the proper knowledge to successfully tackle this exam too. I'm looking forward to reading your blog about how you passed !