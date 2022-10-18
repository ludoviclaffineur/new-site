---
title: "From engineer to head of development&#58; 3 key learnings"
header:
  overlay_image: /assets/images/from-soft-en-hod.jpg
  og_image: /assets/images/from-soft-en-hod.jpg
  caption: "Photo credit: [**DALL·E 2**](https://openai.com/dall-e-2/)"
tagline: "Sharing 3 key learning from my 5 year experience as an engineer in a growing company"
img: "/assets/images/from-soft-en-hod.jpg"
last_modified_at: 2022-10-05 10:05:20 +0200
related: false
published: false
---


When I started my journey as a software engineer in my last company, I had no idea that I would end up in a team leading/engineer manager role. Rather frequent within fast-growing companies, where founding engineers evolve to management role quickly without real preparation (that's where the fun is, right?). It is definitively challenging to be promoted from a building role (i.e. where you are in charge to discuss and deliver a scope) to a role where you need to commit on deadlines where scope, feasibility and timing are of utmost importance and not totally under your direct control. 

<div class="banner">
This post will summarize my journey over the past 5 years and the learnings I am taking away, basically things I would have liked to know on day 1 of this adventure.
</div>

## Founding software engineer

When joining an early stage company, everyone tends to take extra responsibilities to grow the business (despite not always being the best to do it). It goes the same way for the software engineer role that requires much more than coding skills. Your main focus at that time should probably be communication because this is the time when the world of possibilities seems infinite and being able to communicate internally and externally about what you are able to do will definitely help the company making the right choices.

It's also a blank sheet with very little technical debt so you can build everything (disclaimer: you certainly should not). The most tricky part is to iterate fast and validate business hypotheses with as few developments as possible. Nobody wants to invest time in something that might be discarded next month because nobody is using it.

Let’s not forget that your time will also be absorbed by other topics than pure development. To make it more tangible, here is a summary list of regular tasks of my first year at the company:


### Tech:
- Design and discuss architectural decision
- Develop and maintain features
- Test features (functional, unit test,...)
- Set up a pipeline to ship feature, bug fix
- Set up a infrastructure for back end (DevOps)
- Analyze external solutions to accelerate the development
- Write documentation for internal and external uses


### Product Management:
- Provide feedback from bugs and limitations of the solution
- Define user stories
- Set up data analysis system and perform requests
- Ensure deadlines and scope can be met (project management)


### External communication:
- Reassure partners that you are a trustworthy tech department
- Present and sell the solution in events 
- Manage users' feedback (support, bug)


Practically, some mornings you may want to isolate yourself to ship that feature at the end of the sprint and the day after, you are going to explain and sell the solution to external parties in order to get access to their API.

<mark>In a nutshell, at this preliminary stage, a communicative engineer able to solve problems is a great asset for the company.</mark> As there is normally little commercial traction, nor product or product market fit (PMF), the typical mindset is still about being fast in the delivery with a clear scope. At that time, you are ready to build anything that must be rebuilt when the PMF has been found. Say hello to technical debt, no code solutions and manual work!

<div class="banner">
This stage has the incredible power to make alignment across people easy as you are working all together at the same place. The tech team (usually very small) tends to also be very confident about what they are able to deliver.
</div>


## From building to leading
The company is getting more funds to accelerate the development so, good news, the tech team is growing! As you are the one who has been participating in most of the development, you are starting to onboard new team members on the different codebases, making sure they understand product requirements and you are reviewing the code/features, and this, simply because you know the dark places of the code. You naturally receive a new title reflecting these new responsibilities as you are less and less developing new features.

<mark>Your role starts to shift from solving problems towards creating stability</mark> through process, common understanding and standards definition. You are not anymore in a very small team. You have team members with different experiences, great assets but this can also lead to frustrations and delivery inconsistencies. Focus is then on setting standard ways of working to avoid lengthy and unproductive architecture decisions for every pull request. By having these clear rules in place, every new joiner will hit the ground faster. 

At this stage you start to understand that your biggest contribution to the team is not producing code anymore, you have a team for that now but rather your knowledge on the business, software and the lessons learnt from past implementations, you now have a global vision. You start asking yourself more and more: <mark>What did we forget to consider about this feature that might fire back in a later stage of development?</mark>

On a regular basis, you find gaps in the way a feature is being implemented and you communicate your findings proactively to the team and product managers. You seek advice on how we should deal with this new information. Side story: the team starts to know that if you unexpectedly join a meeting , it's probably to bring bad news, meaning that something popped out that we did not think about earlier. It can entirely be linked to the development part (e.g. adding some missing security layer) or, on the contrary, linked to the experience that is not directly related to development: (e.g. feature to send emails but are the templates well ready and properly translated?). As a general rule, when an experience is not well covered, you have 3 options:
- drop that part and manage user's expectations, 
- find a workaround outside the development team to keep the deadline or
- stick to the targeted experience, meaning the team needs to develop it, creating delays.

The logical reaction of the development team should be the following: next time, they will try to involve you in all the scoping and implementation discussions. Clearly not scalable and quite schizophrenic for you. The biggest challenge is then to transfer your knowledge and create awareness to other stakeholders that your team is in learning mode and therefore failing is part of this process. Last piece of advice, <mark>support your team recovering from failures rather than preventing them at all cost</mark>. At the beginning the team velocity will probably be slower than at the previous stage.

This stage also coincides with a refocusing of the role on tackling the technical debt while the CTO plays the cross team alignment role and sets the vision. Practically, you focus on a specific area and delegate most of the codebase to other technical lead. You start to lose direct control on implementations but most of the time you keep the global picture.

## Key learnings

### Setting standards and governance rules early ease onboarding of new teammates
Loads of frustration of team members comes from poorly defined code practices or worse, multiple code practices in one codebase. Early on, make it clear on what are the values of the team, how we operate things and what are the standard rules of coding.

### At early stage an easy solution that needs to be rebuilt is better that a complex one
Don't build a solution for scaling at the first stage of your company. When the company is in growth mode significant time is wasted in processes in general (e.g. can be in the IT solution or anywhere else). You may want to prematurely optimize your code and performance but most of the time you can’t predict the bottlenecks before actually facing them. If your sales are not growing fast, you don't need to care too much. At the beginning, the first metrics should be how easy you can add and remove features from the codebase. Onboarding time should be less than a few days to be able to add a small feature and a few weeks to really find your way in the codebase. Also don't be too creative for your first architecture and use (ideally a standard) one and stick to it. New joiners will thank you and it will reduce the amount the questions.

<div class="banner">
Make it work, make it right and then make it fast. 
</div>


### Having a high performing team requires time

This is one of the most complex piece of learning to apply. Having a high performing team requires time. You can't really control how quickly the company evolves but hiring good team members is a must and they need time to work well and fast together. Team members need to be happy and thrilled by the challenge. This requires soft skills such as patience, empathy and people management. Additionally, the team must have a clear vision and objectives so everybody feels the boat is going in the right direction.
