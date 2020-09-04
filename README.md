# YouTube Radicalization Analysis
This project was completed with support from the Undergraduate Student Research Award provided by the National Science and Engineering Research Council of Canada. As well, this project was done under the supervision of Paul Tupper in the Department of Mathematics at Simon Fraser University.

## Table of Contents
- [Introduction](https://github.com/kaishuun/YouTube-Radicalization-Modelling/blob/master/README.md#introduction)
- [Data Collection](https://github.com/kaishuun/YouTube-Radicalization-Modelling/blob/master/README.md#data-collection)
- [Results](https://github.com/kaishuun/YouTube-Radicalization-Modelling/blob/master/README.md#results)
  - [Channel Flow Analysis](https://github.com/kaishuun/YouTube-Radicalization-Modelling/blob/master/README.md#channel-flow-analysis)
  - [Markov Model](https://github.com/kaishuun/YouTube-Radicalization-Modelling/blob/master/README.md#markov-model)
- [References](https://github.com/kaishuun/YouTube-Radicalization-Modelling/blob/master/README.md#references)


## Introduction 
YouTube is the largest and most popular video hosting platform in the world with over 30 million visitors and almost 5 billion videos watched per day. Almost 70% of content consumed from YouTube comes from the recommended videos, where the algorithm selects similar videos and other suggested videos that it thinks the user would enjoy. This brings up the issue of the bias that may exist within the YouTube algorithm as it has been hypothesized by researchers and media that a radicalization pathway exists on this platform. This pathway suggests that the recommendation algorithm steers users consuming mainstream political content towards more extreme content either on the far left or the far right of the political spectrum. Our goal for this study is to assess if this radicalization pathway exists and if there exists an algorithmic bias in the YouTube recommendation algorithm.


## Data Collection
We used a dataset provided by Mark Ledwich and Anna Zaitsev where they tagged over 800 YouTube channels with a respective political ideology. With this dataset, we were able to build a web scraper that visits each one of these channels and collects data about the channel as well as its 200 most recent videos with over 10 thousand views. In this pool of YouTube videos, we chose 200 videos from each ideology at uniform random,then visited and collected data on the video information (likes/dislikes, channel name, video name, views) as well as its first ten recommended videos.

As we do not have access to individualized YouTube accounts, we strictly look at the base performance of the recommendation algorithm with no previous videos watch or interactions.
We used Selenium WebDriver to automate this data collection process.

## Results

### Channel Flow Analysis
Here in this section, we look at the distribution of views for each ideology to better understand their popularity on YouTube. As seen in the boxplot and scatterplot below, we specifically looked at videos with views from 10 thousand to one million. The majority of the ideologies average around 30 thousand views per video with the most variable ideologies being the Partisan Left, Anti- Theist, as well as the Alt-light, this suggests that there exists more user interaction with videos from these ideologies. This data is also right skewed as certain videos gain more hype and become 'viral' where their views increase dramatically in comparison to regular videos. 

![](https://github.com/kaishuun/YouTube-Radicalization-Modelling/blob/master/Charts%20and%20Graphs/Ideology%20Subscriber.png)

We then model our data based on the assumption that everyone who watched a YouTube video will choose one of the first ten recommended videos at uniform random. In this situation, we split the views of the current video equally between the first ten recommended videos, channels that have more recommended videos as well as current videos with larger views are appropriately scaled in this case. In the diagram below we use a Sankey diagram to display the flow of users between the different ideologies using this method.

On the left side, each box is scaled in proportion to the sum of views in each ideology; and on the right side, it displays which communities gain more users from the recommendation system. If an ideology is bigger on the right side, then it is considered to be at an advantage by the recommendation algorithm.

![](https://github.com/kaishuun/YouTube-Radicalization-Modelling/blob/master/Charts%20and%20Graphs/Ideology%20Sankey%20Plot.PNG)

To gain a better understanding of the advantaged/disadvantaged ideologies we use a double bar plot to plot the original views each ideology has and the views gained/lost by the recommended videos. Here we see that mainstream communities such as the Partisan left and Social Justice channels gained more viewers by the YouTube algorithm, while fringe ideologies are at a disadvantage, often losing half of their views; these ideologies include Men's Right Activist, Anti-White and the Alt-Right. Here we also see that the Intellectual Dark Web (IDW) is at an advantage in comparison to right-leaning ideologies, this suggests that there exists a pathway for users to be drawn towards the IDW, but not towards other right-leaning ideologies. Here, we're able to conclude that the YouTube algorithm has a deradicalizing nature, favouring centralist ideals, but there exists a bias towards the IDW.

![](https://github.com/kaishuun/YouTube-Radicalization-Modelling/blob/master/Charts%20and%20Graphs/ideology%20user%20difference.png)

### Markov Model
Finally using the same data, we normalize the views sent to the recommended videos to gain the transition probabilities for a Markov Model. Similarly, the data is scaled in proportion to the number of times a channel appears in the recommended videos list and the views the current video has. We obtain the limiting probability of this model and we are able to gain the insight below. 

Here we see that Social Justice videos are heavily favoured in terms of recommendations in comparison to all other ideologies. By looking at the limiting probabilities we can reaffirm our previous findings that predominantly centralist ideologies are favoured by the YouTube algorithm at the base level with the IDW ideology growing in terms of trend. 

| Ideology   |      Limiting Probabity      | 
|----------|:-------------:|
| Alt-light | 0.01 | 
| Alt-right | 0 | 
| Anti-theist | 0.01 | 
| Anti-white | 0 | 
| Conspiracy | 0.01 | 
| Intellectual Dark Web | 0.14 | 
| Libertarian | 0.05 | 
| Men's Right Activist | 0 | 
| Partisan Left | 0.13 | 
| Partisan Right | 0.05 | 
| Religious Conservative | 0 | 
| Revolutionary Socialist | 0 | 
| Social Justice | 0.55 | 
| Socialist | 0.04 | 

## References

The inspiration for this project was based on Mark Ledwich and Anna Zaitsev's paper "Algorithmic Extremism: Examining YouTube's Rabbit Hole of Radicalization" that can be accessed [here](https://arxiv.org/abs/1912.11211).
The dataset of tagged ideologies and channels were also taken from the paper and could be accessed on Mark Ledwich's GitHub [here](https://github.com/markledwich2/Recfluence).
This project is not affiliated with any of the aforementioned researchers.

## Report
To see the research paper written for this project click the link [here](https://github.com/kaishuun/YouTube-Radicalization-Modelling/blob/master/Paper/Project%20Report.pdf)
