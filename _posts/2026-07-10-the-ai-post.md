---
title: My AI post
published: true
tag: ai
---

# Extended ramblings, criticisms and AI depression

I have been thinking a lot recently about AI usage, and trying my best to articulate what the impact of this stuff could mean for the
future of the software industry, my family, the planet. I want to approach this topic from the perspective of a boots-on-the-ground
software developer at a 'normal' company, who has - like most of my peers - been essentially threatened and intimidated into adopting
these tools at work. There are some nuts and bolts things that I think would be helpful and interesting to discuss about the real (and
imagined) capabilities of AI tools for software engineers, and also there will be a healthy amount of cathartic wailing. I'll be in my
feelings for sure. Rarely do I feel the need to open a firehose like this, but my thoughts are scattered and a bit hopeless, and I need
to write them down.

I don't want to pre-amble too much stating my bona fides in the industry, but I have worked as a Software Developer since around 2014 
when I joined an E-Commerce startup as an intern (15 dollars an hour!). Since then, I have been gainfully employed to write code for 
a dozen years, often leading teams, large projects and working long hours at different companies. Most of my career has been spent
writing Golang, and I'd like to think I'm somewhat of an expert in that area. I do game development on the side, but so far I'd say it
is in a less than professional capacity (just browse around this website for proof!). I also do many personal projects for the pure
joy of it.

> I love programming. If left alone, I would do it all day every day.

I am not one of these developers who got into the industry for 'the money', or career stability or anything. I just love it. Some of
my fondest memories are staying up late writing code in neovim, solving problems, and watching the pixels flash across my screen in
the precise way I told them to. Being in absolute control over everything, making something out of nothing. Programming a computer
makes you a god of your own discrete world where every new thing you learn allows you to sculpt your world in a new way. I love
programming. If left alone, I would do it all day every day. Everything I write here is based on the foundation of that love, and I
hope that shines through.

## State of Software Development in mid 2026: silver lining?

Like most programmers I woke up one day and was commanded to use AI tools to do my job. I watched the layoffs happen, and often they
happened to people who were most vocal about their AI skepticism, or pushing back on offshoring practices. I guess I had the good 
sense to keep my mouth shut so I could continue to have a job. A job that is no longer recognizable, but one I need nonetheless. My
job now, is not so much to write code, but to write markdown files that will turn into LLM prompts that will maybe write the code I
would have written myself. I am told that unless I do it this way, I'm not being efficient. I'm wasting my time typing. The AI can
'do it faster'. My lifetime of experience, skill and depth of knowledge has been discarded without a second thought because the
most evil people on earth have convinced the business community that AI tools can replace white collar labor. So here I am, stuck
developing the tools and techniques that are designed to replace me. I can either raise my voice now and lose everything, or keep
my head down and hope to emerge from the storm without being homeless. It feels like shit.

What's even worse, is that these tools were, and continue to be literally trained on stolen data from across the internet. Much of
that I directly contributed to in open source code I wrote by hand, stack overflow threads I found myself in and reddit replies I
typed out on my phone. Our own expertise was stolen without our consent and force fed to us on the other end in order to make our
talents obsolete. Will we benefit from this? Not really. Each and every time a non-technical person is awestruck by the capabilities 
of LLM coding agents, I feel like a small piece of my soul is lost. I realize now that these people probably never respected me for
the things I could do with a computer. The now 20 year personal journey I have been on to improve my skills at programming has become
a shattered mirror I now stare in. A sort of dystopian slide-show I am forced to actively participate in, where I am the software
engineer of my own demise.

> Writing software with AI is shit unless you are already good at writing software without AI

The tech business community has been consuming the Koolaid at a lip purpling rate. They are saying it loud and clear:
"We want to replace white collar labor". A phrase that will delight everyone! Yet, clearly for this to be a possibility at all,
Generative AI for writing Software (with a capital S) must have some real world capabilities. *I hate to break it to everyone, but AI
is capable of writing code.* I know, it's true, it fucking sucks. However... I am realizing some interesting things about these tools,
and it gives me hope: **Writing software with AI is shit unless you are already good at writing software without AI.** This is my 
silver lining, it is the truth, and I cannot imagine that this could ever change in any meaningful way. Allow me to elucidate.

## Spec-driven development, headless code and other phrases invented by the utterly deranged

Lets say for the sake of argument, you have a feature that will take you 4 hours (half a work day) to build. It is a very well-defined
feature, you know exactly how you'd go about building it, and this 4 hour estimate covers writing the code, automated tests, and
manual QA testing. You think 'aha!', I'll have Claude build it. So you describe your feature in a sentence or two in a Claude code
prompt and off it goes. 15 minutes later, the cookies are done baking and unfortunately you don't have what you want. Claude doesn't
realize that for local development you use a suite of docker tools that require some precise configuration. Claude also made some
assumptions about the shape of the data and got it all wrong, essentially building something completely useless. You also forgot to
tell Claude that it first has to get some data from a different API before it can even do anything.

A bit annoying, because you knew all this already, but Claude did not and he's the one who must code it. Hmm... there must be a better way.
You realize that the problem is simple: garbage in, garbage out. You need to give Claude more information so it can write the code
better. Keep adding context, business requirements, tribal knowledge and detailed implementation strategy requirements and you get
**Spec-driven development**.

So armed with this new buzzword, you start over. You spend an hour using a structured, spec-driven workflow (ai-dlc, bmad, etc) where
you - in great detail - describe the problem you are trying to solve. The fleet of skills does research, asks clarifying questions and
ultimately produces a quite spiffy plan that it will execute. You double-check it's approach, make any necessary adjustments, and at
the 1 hour mark, instruct Claude to execute it's plan. Claude executes the plan in a series of discrete steps. Along the way, you get
to confirm it's approach, and verify tests are passing, etc etc. 1 hour later, after completely executing the plan, the AI announces
the task is complete. The tests are all passing, the build succeeds, and all your manual testing seems to indicate that the feature
works perfectly. Along the way, you were able to verify that the code was following the pattern you instructed it to follow, and looks great.

> Let's sit and take a moment to understand what has just happened here. I saved an hour and a half of development time. But it was not free.

TIME: 2 hours 30 minutes, and you push your branch for code review. This is a real summary of a task I did recently at work. Sounds
great right? You may be thinking, wow... you shaved an hour and a half off your initial estimate and Claude was able to produce
high-quality, production-ready code that you - a senior engineer - would have written yourself! Correct. BUT! **Let's sit and take a
moment to understand what has just happened here.** I saved an hour and a half of development time. But it was not free. There is a cost 
to pay. Several, in fact. First, there is a monetary cost - $35 dollars in tokens using Claude Opus, on top of my salary. Next, there 
is a cost of understanding. It is unrealistic to expect developers who are moving at this accelerated speed to be able to review every 
line, and fully comprehend it. We are suspending our disbelief, and there **is** a cost to that. It may be hard to quantify, but it will 
emerge in the form of technical debt, maintenance cost, production outages and lost development time. Keep in mind, this was done with a
rare feature that had well-defined requirements, which we all know is a unicorn at any company. There is also the inconventient fact
that although an hour and a half of time was saved, I still had to wait until the next day for my coworkers to have time to review
the code. Did we just 'hurry up and wait'?

To summarize: *Spec-driven development is when you spend all your time telling Claude how to exactly write the code you know how to 
write yourself, and hoping it writes it to your satisfaction.* Assuming it does this (even with all the context and structure, it often
does not), you have saved some time, but also had to pay Anthropic for that. Oh, and by the way - unfortunately a junior developer is 
not capable of making Claude write code like this. So good luck getting a non-technical grunt to captain this workflow successfully
one day like our demonic business leaders want.

So I ask myself... was this actually even worth it? A question nobody in the business community seems to feel the need to ask. Tokens
are as cheap today as they will ever be. The economics of this is not going to improve.

> Headless code, and I cannot stress this enough, is for babies.

Now, I mentioned 'headless code' as a joke, but people are serious about this right now, so I'll describe this to the best of my
abilities: headless code is when you just have a bunch of detailed RFCs that define your business / technical requirements, and
the code that satisfies those RFCs is interchangeable and ultimately doesn't matter. Great, now that you have freed yourself from the
shackles of having to understand on a technical level anything that is produced by your company, you can finally fire all the people who
you hired to know that stuff. AI will loop and loop and loop until the RFC is satisfied. Other AI will review the code. Other AI will
deploy the code. You may even have an AI write the RFC, fuck it right? **Headless code, and I cannot stress this enough, is
for babies.** Some of the least capable people in the tech leadership at your company are salivating at this idea right now, and
it's funny because it's never going to happen.

Do I even need to explain why? Chances are, you work for a company that can barely manage to build a content blog. But now you think
you have the expertise to fundamentally change the way software development is done? And hand the car keys to a hallucinating
robot while you are locked in the trunk? Good luck!

> If you know how to write the code, give me one good reason why the LLM should write it instead?

I have talked at length about the real world tradeoffs, expectations and capabilities of AI tools in software development. But I still
don't think it has the future that the LinkedIn bozos are hoping for. What every developer is realizing right now, is that using AI
tools to write your code has real costs. You are trading speed of development for expertise. You are trading speed of development for
understanding. You are trading speed of development for an uncritical acceptance of output. These are sometimes perfectly fine tradeoffs
to make... but surely not always? Is writing lots of code even important? Why is the industry rushing forward to optimize in this one
single direction? I'm beginning to lose grasp on reality...

HERE WE GO, EXPLAIN ONE THING TO ME: If you know how to write the code, give me one good reason why the LLM should write it instead?
Speed??? Oh for fucks sake, here we go again. I can think of dozens of ways to finish projects faster at a company, and none of them
involve how fast text files can get deployed to AWS:

- Product owners not knowing what they want and refusing to respond to clarifying questions: wasted time
- Meetings with the wrong people attending: wasted time
- Stakeholders waiting a week to validate features on staging because they were busy: good thing the AI wrote it so fast!
- Relying on old / bad tools that take more time to use because rebuilding is not prioritized: wasted time
- Refusing to modernize infrastructure: wasted time
- Accepting that your build times will be 20 minutes instead of investing time into fixing it: 20 minutes isn't that long!
- Every app at your company coming packaged with it's own MySQL container in docker-compose for local development instead of just 1:
hurray, now I am out of storage and must waste time! (sorry that is my axe to grind)

I could literally do this all day.

Fixing any one of these things at your company would increase velocity, but it's not a priority, and never will be. Because each of these
problems require creative solutions, critical thinking, cooperation, communication and any number of C words. You know what else? None of
these things can be fixed, or made better by how fast you can deploy text files to AWS. Yet, for some reason it does not occupy the same
mindspace for your boss as how fast you can fucking write code. So now we should all understand that the reason this shit is being thrust
upon us in the first place is because the MBA community is a talentless flock of pidgeons who believe they have found the EZ button under
a banana peel, and now they don't need to do any of that pointless stuff like 'thinking' and 'trying' because the text files are flying
onto the servers at record speed. 

You can think of using AI to write your code the same way as using a SaaS product. You use a SaaS product when you just want the some
specific output, and do not care to be responsible for anything that happens in between. When you use AI to write code, you are 
essentially turning the tech at your own company into a SaaS product for yourself. This is a perfectly reasonable thing to do for many
projects, but... again... surely not always??? Why wouldn't you aspire to understand how your own software works? All the important
bits that make your software unique, that make your company money, that define business rules, or processes... I am not buying a future
where a hallucinating anti-humanity device is trusted to just 'handle all that shit'.

## Where Software Development ends up

In the future, I believe we will use AI for all those little projects that don't matter. The things we used to pay SaaS companies to just
do for us so we don't have to think about it. All the critical stuff should be written mostly by hand and understood by a human being. I
will die on that hill. The smart folks will use locally running models, lightweight agent harnesses, and restrict code generation to 
boilerplate, hyper-targeted agent skills for recurring tasks (and mostly just for tool calling) and any number of random things that are
tedious, not fun or useful to write, and don't require any technical understanding. The folks who do this will stay ahead due to pure
competence and technical expertise. I don't care that one person can shit out 30k lines of code per day, that means nothing to me.

## Final thoughts, please don't stop learning how to code

We are investing the technical knowledge of a generation into markdown files instead of junior developers who will become the seniors of
the future. Don't let it be you too. Don't let them win. 
