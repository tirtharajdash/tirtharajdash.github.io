---
layout: post
title:  Let’s build Intelligent machines with Hide-and-Seek
date:   2020-03-07 12:30:00
description: My doctoral research written as a "Popular Science Story"
---
**Prelude – Introducing the Characters**

It’s a sunny afternoon in a remote village in India. For children, this is the perfect time to play some games with each other. A game which is quite popular among them is known as hide-and-seek (In Hindi, this translates to *“Lukaa Chhipee”*).

The village is comprised of small and large houses arranged in closed neighbourhoods. *“Ok. I am closing my eyes, you guys hide and I will search you. I am counting to 3; 1... 2... 3...”,* says a boy named “Seeker”. Now, the seeker has to find one or more of his friends to win this game of hide-and-seek. He goes to one location near him, then one more, and continues to do so. Finally, he finds one of his friends the “Hider”. He continuously goes on to find a few more of his friends, and finally all of them. He wins the game of hide-and-seek.

Little did I know that such a simple-yet-wonderful childhood game of hide-and-seek can be useful towards building computing machines that can learn from the experiences. In scientific jargon, we call these machines “Artificial Intelligence (AI)” tools. One of such tools is popularly known as “Neural Network” which is inspired by the way human learns from past experiences. An experience is called a data instance and is defined with a set of external inputs, called “features” in AI terminologies. These biologically inspired neural networks process external features and produce an action, called “output”. This output could be a category to which the given experience belongs or a quantity. The quality of the output of the neural network depends on the quality of external features that it received. An analogous example to understand this concept is the following. Consider, we are in a restaurant. In the end, we have to decide whether our experience was good or bad. This decision, in entirety, depends on the questions such as: 

*Whether we were welcomed with manners? Was the place clean? Was there proper ambient lighting? Was the place crowded? Was the food served in time? How was the service? Was the cost reasonable as per taste?*

If we can form such questionnaires that are almost perfect, then it would make our brain eligible to decide on our experience with this restaurant. Such is the way a neural network produces output with the help of its intricate neuro-synaptic circuitry. By the way, you may be wondering: How did we form the above questions related to our restaurant experience? A straight forward answer to this may be: We have gone to many restaurants in our life so far and those experiences made our preparation of questionnaire quite easier. Isn’t it? Some directly come from our own experience, and some come from what other experts say about their experiences with various restaurants.

A special kind of AI tool that can help us form these types of external features from past experiences along with some expert knowledge is called Inductive Logic Programming (ILP). This is the tool that can help us to produce features using data and expert knowledge defined in terms of logical clauses. We build our ILP engine with the very idea of hide-and-seek game, where there are countably infinite locations in which a set of hiders can hide and the goal of the ILP engine is to find hiders in those locations. Essentially, a hider means a good feature that will go as an input to our neural network.

**The Setting**

Let’s go back to our village version of hide-and-seek that we have described briefly in the previous section. Let’s there be n possible locations. The hider has to select one of these locations and hide there until the seekers find him. The hider’s selection of a hiding location is based on preferential ordering i.e. hider assigns some probabilities to each location for selection. This forms a distribution over locations called *‘hider distribution’*. Naturally, the hider does not disclose this distribution to the seeker. In the worst-case scenario, the seeker will not be able to find the hider until he visits (opens) all locations other than the one where the hider is hiding. In this case, the seeker makes n-1 mistakes before he finds the hider. Can the seeker do better than this? The answer to this is “Yes”. But, the very first idea that comes to our mind is: 

*If the seeker could know the hider distribution exactly, then every time the hider hides using his distribution, the seeker would be able to find him.*

Isn’t it? 

Interestingly, our theory proves that this leads again to the worst-case result of n-1. Further, our theory finds a seeker which is a bit more random than the hider. Let see what we meant exactly here.

Let's assume that the hider distribution is known to the seeker and the seeker knows that his performance will be bad if he uses the same hider distribution. So, he constructs a distribution in which the locations for which the hider’s selection probabilities are low get higher importance and the locations for which the hider’s selection probabilities are high gets lower importance. Essentially, this seeker distribution has more randomness than the hider’s distribution, but, it does minimize the mean value of mistakes made by the seeker before finding the hider. But, there is a catch here. The seeker does not know the hider distribution. So, what can he do? We gave a statistically simple idea to the seeker:

*See, you don’t know anything about hider distribution. So, equal importance is given to every box. This makes each box receiving 1/n probability and forms the uniform seeker distribution. One safe assumption is that the hider will always select locations using his distribution for which the probability is more than 1/n. Let’s call the set of locations for which the probability is 1/n as “Good partition” and the rest as “bad partition”. Let’s say this good partition forms the “p” proportion of the n. Now, uniformly select a bunch of locations (“s”) at once to find at least one location from the good hider partition with very confidence (“c”). Repeat this process until you find a hider.*

Now, the seeker asked us: But, how do I decide this p? How do I know how many boxes I should draw uniformly at once?

We said: If you still have no idea about that. Go with p = 50% and a confidence of 95%. (In our research, we prove this bound relation among s, p, and c, which is independent of n.)


**The Plot**

The applicability of the theory is studied extensively on 73 biochemical problems directly related to drug discovery. These problems are obtained from the National Cancer Institute under the National Institute of Health, United States. The goal is to construct machines that can automatically predict whether a biochemical compound has the potential to either inhibit or kill cancer cells. As mentioned earlier, our ILP engine uses the hide-and-seek theory to generate good features essential for a neural network. Good features are those distinctively express the compound concerning their resulting property: inhibiting or killing. One such of such features is found to act as a very high discriminative accuracy of 90% on known data of various chemical compounds:

*The compound has a single bond, a double bond, two benzene rings connected, a fused ring, and a hetero-non-aromatic structure.*

We can see that such a descriptive analysis would help to construct neural networks that have the potential to outperform neural networks built with only atom-bond descriptions of a chemical molecule. Using the hide-and-seek approach, we were able to construct very good features efficiently describing the chemical molecules. The neural networks built with these hide-and-seek based features are evaluated for all the 73 different problems.


**The Climax and the Sequel**

The neural networks built with the hide-and-seek based features proved themselves winner against the neural networks built only with the atom-bond descriptions available for chemical compounds. One remarkable result is that 500 good features are sufficient to learn powerful predicting machines which have far higher accuracies than the machines built with thousands of atom-bond features as used in the state-of-the-art. This result makes the applicability of a simple game-theoretic formulation very useful for the whole community of Artificial Intelligence as a whole.

Well, where should the story advance further?

We have been looking at another simple aspect of hide-and-seek games that we have not incorporated in this story yet. The locations that have high importance in the hider’s distribution are neighbours of each other. This means:

<blockquote>
Good locations have good neighbourhoods.
</blockquote>

We end this article with a famous quote by Belgian psychotherapist Esther Perel:

<blockquote>
“When there is nothing left to hide, there is nothing left to seek.”
</blockquote>

The biggest advantage of doing Science is that there is always something to seek as *there is always something hiding.*

<hr>

This story is a "Popular Science Story" version of the article [Tirtharaj Dash, Ashwin Srinivasan, Ramprasad S. Joshi, A. Baskar: Discrete Stochastic Search and Its Application to Feature-Selection for Deep Relational Machines. ICANN (2) 2019: 29-45](https://link.springer.com/chapter/10.1007/978-3-030-30484-3_3).
