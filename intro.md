Intro to Machine Learning
-------------------------

<small>
  <span style="color: darkblue;">&lt;</span><span style="color: goldenrod;">/&gt;</span>
  <a href="https://github.com/psse-cpu/se3121-intro-to-ml-slides">
    https://github.com/psse-cpu/se3121-intro-to-ml-slides
  </a>
</small>

<h4 style="margin-top: 192px; font-size: 0.85em;">
  <span class="course-code">SE 3121</span>
  <span class="course-title">Machine Learning</span>
</h4>

<div style="font-size: 0.75em; margin-top: 16px;">
  <b>Richard Michael Coo</b> |

  <a href="https://github.com/myknbani">
    <img style="vertical-align: middle" src="images/github-32px.png" alt="github logo">
  </a>
  <a href="https://twitter.com/myknbani">
    <img style="vertical-align: middle" src="images/twitter-32px.png" alt="twitterlogo">
  </a>
  <span style="vertical-align: middle">@myknbani</span>
</div>



### Outline

- What is machine learning?
- brief history
- ML as the best way forward
- supervised vs. unsupervised learning
- two types of supervised learning
  * regression
  * classification
- example non-ML AI algorithms
  * A* pathfinding algo
  * minimax gameplaying algo



#### Machine Learning

<div>
  <blockquote>
    Field of study that gives computers the ability to learn without being explicitly programmed. <br>
    <span style="font-size: 0.75em">
      - <span style="color: brown; font-style: italics">Arthur Samuel (1959)</span>
    </span>
  </blockquote>
  
  ![arthur samuel](images/arthur-samuel.jpg)
</div>



#### Arthur Samuel's Checkers Playing Program

![checkers](images/checkers.jpg)

- started with minimax algorithm
- also used $ \alpha-\beta $ pruning
  * limited memory during his time
- then allowed it to self learn



### Formal Definition

<div style="display: flex">
  <blockquote>
    A computer program is said to learn from experience E with respect to some task T
    and some performance measure P, if its performance on T, as measured by P, 
    <strong>improves with experience E.</strong>
    <br>
    <span style="font-size: 0.75em">
      - <span style="color: brown; font-style: italics">Tom Mitchell (1998)</span>
    </span>
  </blockquote>
  
  ![arthur samuel](images/tom-mitchell.jpg)
</div>



#### ML is the best way towards human-like AI

* Discuss on Canvas (or live class) the diff. between 
  - artificial intelligence and 
  - natural (human) intelligence
* e.g. the inhumanity of AIs in your favorite MOBA:
  - or other game genres?
  - improves over time?
    + doesn't fall for the same tricks again and again?
    + bots don't buy defuse kits even after several losing streaks
    + gets stuck in the small vent in CS:GO Mirage again and again
    + 👆 takes too long to unstuck as a team
  - very accurate chain-stuns?
  - very accurate moving, jumping headshots?



### Examples:

* learning from web browsing data, clicks, etc.
  - feel creepy about searches and ads being very smart?
* smart embedded systems / IoT
  - self-driving cars, self-piloting copters
  - janitor/slave robots
* five senses
  - computer vision
    * picture and face recognition
    * handwriting recognition, OCR
  - natural language processing
    * Siri/Cortana can understand (-ish) what you say
    * it can synthesize human-like speech to talk back to you

