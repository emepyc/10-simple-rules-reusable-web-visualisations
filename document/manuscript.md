# Ten Simple Rules for Writing Reusable Web Visualisations

# Abstract
Browsers’ performance has increased hugely; a process which has happened hand in hand with the latest advances and standardisation of key technologies such as HTML5, CSS3 and ECMASscript (formerly JavaScript) and the commoditization of network computing resources (i.e. cloud computing). All these factors have enabled the web to incorporate well established ideas and proven and tested principles from other domains of computer science and software engineering. In the last five years we have witnessed a qualitative leap, by virtue of which the web is now a computing platform with the added benefits of immediate availability of data, code and real-time collaboration. It has thus become the preferred medium for scientists of all disciplines to publish their research, along with visualisation software that can be reused and iterated. The following 10 rules offer guidelines learnt from our experience building and sharing data-driven web applications to maximise the benefits that users and developers can get from our software.

TODO: We need a note about reusability

TODO: We need a note about interactivity

## 1. Define the context, question and audience
AP: The goal of data visualisation is to communicate complex information accurately, making the relevant bits stand out among the less important data. In short, to raise the signal-to-noise ratio, figuratively speaking. Working on a given visualisation should start with a question asked in regular language (e.g. “What genes are related to a specific disease?”, “How does a certain treatment affect the expression of a gene?”). However, as web developers, our responsibility is two-fold if we want our data visualisation to be reusable. We want to make our end product, our code, to be easily integrated in any environment. This is one of the fundamental ideas that permeate the following nine rules.

MP: The goal of data visualisation is to help understand complex information easily and accurately. When working on a new visualisation, we should start by formulating the questions we want to help answer. This question should be asked in regular language (e.g. “What genes are related to a specific disease?”, “How does a certain treatment affect the expression of a gene?”). Not stating this context appropriately may lead to visualisations that just display data without helping its understanding.

As developers, though, our responsibility is twofold: On one side we want to build an end product able to help in the interpretation of our data, but on the other side we want to build a solid piece of software that follows accepted characteristics of good software (see for example [Ten Simple Rules for Developing Usable Software in Computational Biology](http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005265)). Some of these characteristics are discussed in the next rules adapted to the current state of web technologies and web visualisation and requires a mind shift for developers.

For example, while developing reusable web visualisations, defining your audience is not straightforward. On one hand we have the _final users_, ie the users that will access the visualisation through their web browser. On the other hand we have the _developers_ that will reuse your visualisation in their specific web application. We can't even define the _final users_ as a homogenic group since they will be users of the host application your visualisation is embedded in. Taking all these considerations before start coding will probably save you from costly rectifications in later phases of development.

The bottom line of this rule is: think before you start coding. The rest of the rules presented here are meant to help you in identifying common pitfalls and some thoughts to take into account before start coding your new shiny visualisation. 

## 2. Explore different ways of visualising the data

Coming up with the best visualisation for your data can be challenging. Most of the visualisations in science and especially in research are made by scientists or software developers without formal training in design, basic perceptual/cognitive principles or knowledge about the different visual channels to encode data.
One good thing about resources offering this kind of information is that they are normally well designed, know about basic perceptual and cognitive principles and use the right visual channels to improve your learning.
Gaining some understanding about these topics will increase the impact of your visuals.

User experience (UX) principles and practices will also help. This includes sketching sessions, collaborative design (design studio) user testing etc. Take into account accepted solutions to show the type of data you have but also try to be creative exploring different alternatives even if you end up discarding them.

A typical design session we have found particularly useful is as follows: Gather a diverse group of people: not just the developers, but also real or potential users and data experts. Explain the problem, then each participant should/could attempt to sketch 1-3 ideas within a limited time – don’t be afraid to try unconventional ideas, just sketch freely. In a second phase, the participants explain their designs and answers any question from the rest of the participants. Iterating the same procedure 2 or 3 times you will find that the designs start to converge picking up the best ideas exposed by the individual sketches.


## 3 Design with data

Keep in mind your data volume and limits during your design phase. Your visualisation should be optimised for the typical amount of data but at the same time has to cope nicely with the extremes. In order to accomplish this you should know your data very well, find its distribution, its minimum and maximum values, etc.

Decide if some aggregation or filtering should be done in advance. If you need aggregation or filtering consider doing any needed transformation in your backend to optimise data transfer to the browser. In general, try to transfer only the data you need to visualise. If the data is very variable you may need to design different levels of aggregation or visualisation and adapt the data display accordingly.

It is also important to design any transitions you may need. For example if you need an overview vs a detailed view, how to zoom in and out, etc. If you use transitions make sure the user don't get lost and always give a clear way to revert the filtering.

Paper designs and sketching sessions are powerful tools to think about how to represent your data but sometimes they don't have enough level of detail. A working prototype, even if incomplete, will tell you if you are in the good track early in the development process.
 

## 4. Take advantage of the web
The web was built on links, use them! Don’t build a closed silo. Your data visualisation should link to other resources and should pull as much information as possible without losing focus of your core question. Don’t make it a do-all, show-all sorts of data. It’s a fine line. Use common sense. Think if the linked-to or pulled data enhances the understandability of the information you’re presenting.

When developing for the web you have access to lots of data resources from where you can pull data directly from the browser. Many renowned biological resources like Ensembl [REF Ensembl REST API paper], UniProt [REF? or just https://www.ebi.ac.uk/proteins/api/doc/#/] or Reactome [REF? or just http://reactome.org/pages/documentation/developer-guide/restful-service/#API] have REST API services you can use directly from the browser. This is a very powerful tool that has allowed the proliferation of client only web visualisations like Genoverse [REF], TnT Genome [REF] or Dalliance [REF] among others.

One of the main disadvantages of using such resources is that the visualisation depends on data you don't control, ie, if the data format served by these resources changes your visualisation will need to update at the same time (or as soon as possible, see BOX 1). Ideally these resources should be versioned so you can still access older versions but this does not always happens.

Taking advantage of the web also means that your component can and should link out to relevant resources. 

## 5. Be modular and be reusable
Modularity is a well recognised property of good software.
It is a good coding practice to organize the code in small parts (libraries, modules, etc) that ense\
mble together in a functional application. The same is true for reusable visualization components. B\
reaking up your component in smaller functional parts and making those parts available (through npm \
for example) increases the chances of any of the sub-components to be useful on their own to other c\
omponent developers.

## 6. Choose your dependencies carefully

## 7. Your code is (also) your product

## 8. Provide a good API for developers

## 9. Test and profile your code

## 10. Test with users as soon as you can and as often as you can

  
## BOX 1: Choose your distribution system

There are important considerations to take into account when deciding how to distribute your visualisation. One way is to distribute it using package managers (for example npm, yarn or bower for Javascript components). This is the approach adopted, for example, by BioJS [REF or biojs.io]. Packages distributed this way are then processed and served to the browser. The problem appears when the component depends on external data pulled directly from the browser. If the data format changes the component is left in a broken state. Fixing this requires creating a new version of the component, distribute it so it can be taken and deployed again leaving behind a number of broken versions in the package manager. Depending on the deployment process this may leave the broken version online for some time. Reducing this time requires a robust way to catch this problems as soon as they happen. This issue would not happen if data distributors version their data allowing components to access older versions.

In cases where the visualisation pulls non versioned data, one common strategy is to distribute the visualisation directly from a content delivery network (CDN). In this case, the code is not hosted in any package manager but served directly to the web application. By avoiding this middle step, changes in the code are reflected directly in all the web applications consuming the component. The problems in this case is that since the new versions become live automatically, it is much difficult for the consumers to test the new versions in staging servers. Components built in this way can not be modular as explained in rule #5 which makes them less flexible. 
