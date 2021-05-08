Creators: Giancarlo Cabeza, Agustin Garcia
Date: 5/7/2021
Class: CIS 192
Assignment: CIS 192 Final Project: DeepFake App


This is the readme for our final project for CIS 192: DeepFake, the social media of tomorrow!

First, we will describe the overall structure of this code, how to install and run, etc. Then, we will describe where each of the grading
components were met.


1. Project Summary
Agustin and I have a love for deep fakes (those memes were people say they had an algorithm watch 1,000 Friends episodes and generate one of their own). Although the term deep fake is being used loosely here, we really wanted to use this idea of algorithmic prediction to create "deep fakes" of our own. We also really liked the last assignment with building a website, and we thought it would be cool to combine the two: a social media platform centered around "deep fakes" generated by machine learning.

Our platform, called DeepFake, is similar to a typical social media site in some of its features: accounts, liking posts, a "wall" with everyone's posts, and the ability to delete posts. However, what stands out about this platform is that what people type is not what gets posted to the world. For every post (or as we call it, every fake), the user will type in the names of the people who they would like to include in their generated deep fake. Our current set of entities includes musicians and politicians, and it allows users to either create deep fakes using just one person, using multiple people in the same genre, or using people across genres! We thought it would be cool since no post is every likely to be the same, which means new content can always be created!


2. Structure of the code
To handle the machine learning / deep fake generation part, we compiled a list of songs for artists and speeches for politicians, each encapsulated in their own text file in the corpus folder.

We used Django to handle databases/webdev, which means the standard files like manage.py, views.py, models.py, apps.py, and urls.py all apply. We also created another class called nlp_generationp.oy which uses markovify to generate the "deep fakes" based upon the user input. This file will, based on the user input, compile a "master corpus" based on the individual text files, and then use that to generate a randomly determined number of sentences/verses for the deep fake (between 5 - 10 sentences or verses). The html files in templates are then used to render the website, where users can see the deep fakes on the home and profile pages, can sign up on the accounts page, and can be introduced to the platform on the splash page.

3. Running and Installing
To run and install, look at requirements.txt to see what is required to run this. Otherwise, simply type python manage.py runserver in the command line to start hosting the website on a local server (port 8000). From there, you can use the website to your heart's content.

When inserting in the parameters for a post, you must be sure to type the names exactly as they should be typed! That means that they should be spelled correctly, and there should be no commas separating any inputs (spaces between each word are fine, and in cases like reo speedwagon, a space is required between the two words).

For example, if I wanted to make a deepFake off of taylor swift and donald trump, I would type:
taylor swift donald trump
The case of the letters do not matter, but they must be spelled correctly and they must have spaces as appropriate. We will implement features in the future which better handle for malinput.


4. Grading components
4.1. Class Definition and Magic Methods
To meet this requirement, we made two models in the models.py class to represent both posts as well as people. As for the magic methods, we included a __str__ and __eq__ method for the classes. However, we did not originally know that __eq__, when overridden, actually makes the class not hashable. Thus, we also had to override the __hash__ magic method, and here we just called the super hash method. 

4.2 Two first-party packages
Here, we used both random and os/re. We used random so that we could randomly generate a number which would represent the number of verses to create from the markovified model. We used os to handle file paths and directories, which was especially helpful for reading from text files in the corpus folder (a different folder than the manage.py file). Finally, we used regex to help with pattern matching for various reasons.

4.3 Two third-party packages
Not only did we use Django to help with webdev and databases, but we also used markovify and its built in NLP models to help us create the "deep fakes" for each post.

4.4 In-line documentatoin
Feel free to look at our comments throughout!

4.5 Readme.md
You are reading it right now!

4.6 A Video Walkthrough
The video is here on youtube: https://youtu.be/BYHBUQRWMdQ

Also, the source code is hosted on github as well: