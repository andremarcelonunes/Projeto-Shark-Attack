# Shark Attack

My focus on this project were to clean the dataset that came from Kaggle, based on research by  https://www.sharkattackfile.net/index.htm
During my job, I tryied to answer the following question: 

* Which age group are  white sharks more likely to attack?

White Shark belongs to Family Lamnidae - Mackerel Sharks and your scientifc name is  *Carcharodon carcharias*

- gill openings large, barely extending onto the top of the head
- teeth enlarged, blade-like, and relatively few — less than 40 rows in each jaw
- gill rakers absent
- tail stalk slender, with precaudal pits and strong lateral keels
- caudal fin nearly symmetrical, with lower lobe almost as long as the upper
- coastal and oceanic; cool temperate to tropical zones of the Atlantic, Pacific, and Indian oceans

![](/archive/lamna-nasus.gif)

## Getting Started

I started seeing the file and I could see that there were many problems on it. First all, the duplicated lines were about 67,5% of all lines. The names of columns were hard to interpret easily, very confused! 

## Cleaning was a hard hard work!

### What I did to Cleanup?

  * Delete empty columns and no useful information on Dataframe
  * Investigating column age, lacked and unclear information on that 
  * Fixing age with a dictionary, too many conditions to deal on that
  * Creating a new column called "new_age"
  * Creating a Function for mapping Age column and assigned the right value to new_age
  * Some cases were marked as "check" in new_age cause seem ambiguous , after analyzing them, they were deleted and new_age column was converted to int64 type
  * Recognizing species on DataFrame, based on print, it was created an excel file to fix it
  * Based on excel file of species, It was created a new DataFrame
  * Merging both to create a new one called "tb_sharkattack_new"

### Start point of analisys

  Exporting the DataFrame to tb_sharkattack_new.csv. Is was sufficient for my task. 

## The Analysis 

During the process of identify age groups and others information regarding to it, many graphs were created to explore information, but I am going to focus on those regarding to main subject on next steps.

### White shark attack  young, children  or  elderly  people? 

Just to clarify one important problem on this dataset, Many attacks on humans, the  species are not identified, this number is about  64% of dataset. So, this can create a possible bias for this study.  
Let´s see all shark attacks identified on table bellow:

```
white	  13.440048
tiger	  5.798852
bull	  3.926306
nurse	  2.053760
blacktip  2.023558
whaler	  1.540320
mako	  0.815464

````
Look, when you see the attacks with species identified, you see white shark on the top, but it represents only 13,44%.




#### Let´s see better this number for all and white shark attacks





![](archive/dist_age.png)

The graph above is not a normal curve, but its similar to that. We can infer that mean is in the  20's 

Let´s use mean to consolidate the age. This indicator of central tendency works well when you don´t have outliers.  
looking into dataset,  you can see that age mean for white shark attacks is 30,4 years, differente from 27,4 when see the whole dataset. 
Let´s remember that all other cases that species weren't identified represent 64% of data and mean of age for those is 26 years. For sure,  it´s bring the mean for all  close to 26 years. But, what about per species?



Let´s see the distribution per species on the following graph: 

![](archive/dit_species.png)

The attacks are concentrated in the 20`s, but white shark is the red dot  above others is close to 30.  

Now, let´s see the same distribution curve for white shark :

![](archive/dist_white.png)

It´s not so different from that for all attacks, but there strange  tail on right side of the graph, isn't  it?  

To better understanding, the dataset was cut in 10 pieces of age group. I don´t see any consensus about group age from other sources, It depends highly on kind of research you are doing,  so I thought that  it would be a good  idea to create this groups. 
Let´s see how many attacks happened for  each  age group by white shark:

```
(9.6, 18.2]	 0.162528
(18.2, 26.8]	0.311512
(26.8, 35.4]	0.221219
(35.4, 44.0]	0.133183
(44.0, 52.6]	0.119639
(52.6, 61.2]	0.027088
(0.914, 9.6]	0.002257
(61.2, 69.8]	0.011287
(69.8, 78.4]	0.011287
(78.4, 87.0]	0.000000
```

As you can see the attacks happen in majority   between 18 and 44 years. 



Let´s see  for all others cases: 

```

0	(9.6, 18.2]	 0.277258
1	(18.2, 26.8]	0.266385
2	(26.8, 35.4]	0.178496
3	(35.4, 44.0]	0.112353
4	(44.0, 52.6]	0.070069
5	(52.6, 61.2]	0.040169
6	(0.914, 9.6]	0.032619
7	(61.2, 69.8]	0.014799
8	(69.8, 78.4]	0.006342
9	(78.4, 87.0]	0.001510

```
Huum!? Change a little, isn't?  it seems like white shark attack less people bellow 18  than others ! Is it really true!?


### Let´s check the activities involved in those attacks by white shark 

Maybe, knowing what people are doing it´s possible to know your age. Maybe?

```
surfing               159
diving                81
swimming              60
fishing               58
body                  24
Snorkeling            12
Kayaking              10
Treading water        6
standing              6
Lifesaving drill      2
SUP                   2

```
More than 50% of people were surfing, diving, fishing  or  swimming when were attacked by white shark. 

What about these  activities for all dataset?

```
surfing             887
swimming            693
fishing             503
diving              301
wading              143

```
Its seems like diving has relevancy to white shark attack more then other types of activities. 
For white shark it is 18% of attacks and for all others is 9%

Let´s see age group for those activities and their proportions: 

###### *multiplying  these numbers per 100 is the same of percentage*

```
group Age	prop_surfing	    prop_swimming    prop_diving	prop_fishing
(9.6, 18.2]		0.296505	        0.347763	     0.116279	    0.139165
(18.2, 26.8]	0.311161	        0.264069	     0.229236	    0.274354
(26.8, 35.4]	0.174746	        0.124098	     0.292359	    0.270378
(35.4, 44.0]	0.109357	        0.075036	     0.162791	    0.153082
(44.0, 52.6]	0.063134	        0.067821	     0.116279	    0.089463
(52.6, 61.2]	0.027057	        0.046176	     0.056478	    0.045726
(0.914, 9.6]	0.011274	        0.044733	     0.006645	    0.005964
(61.2, 69.8]	0.005637	        0.020202	     0.016611	    0.007952
(69.8, 78.4]	0.001127	        0.007215	     0.003322	    0.011928
(78.4, 87.0]	0.000000	        0.002886	     0.000000	    0.001988

```




### Correlation vs Causation
Even though, the mean of age says that white shark prefer a group of age, people between 18 an 44 years, those are surfing, swimming, diving and fishing, it´s not meaning that the white wants to attack them because of their age. Surfing and diving are sports that brings some risk of atttack, diving has a mean of age greater than others activities. According to article on site https://observador.pt/2021/10/29/novo-estudo-explica-razao-pela-qual-tubaroes-atacam-humanos/, humans are attacked by shark when they "think" humans are their natural food. like seals, turtle and other animals that live in ocean. So sharks don´t hunt humans, and even less chose group of age. They attack from bottom to up, than  someone surfing or diving can be attacked because sharks see them like those animals. Diving bring the high risk when involves fishing. Shark can smell far from  hundreds meters the fresh meet or blood of fishes. The probability to be attacked by shark is minimal, according to Institute of Australian Science between 1970 and 2000 died 12 people caused by shark while died 150 hit by coconut. So be careful with coconut tree on beach more than sharks.  



"...leading researchers to believe that the sharks' ability to differentiate between humans and prey is actually worse because of the lower visibility in oceans. They also believe that the mistaken identity theory could apply to other shark species associated with human fatalities, such as tiger sharks or bull sharks. (https://www.cbsnews.com/news/great-white-sharks-bite-humans-mistaken-identity/)



Look the pattern

![](archive/pattern_visual.jpg)



In many cases, the white shark were identified by witness and researches whit bite pattern and tooth fragments , even though thats be a hard task even to biologist to say which species can be involved, according to article on http://www.elasmo-research.org/education/white_shark/patterns.htm. The white shark attack from bottom to surface, but the victims by themselves  couldn´t identify the species and say white shark. 



## Conclusion

On this study, we can see a lot of attacks to main activities like surfing, swimming and fishing. There no evidence that if you have 30's, you are the next victim of  white shark. Clearly, people doing these activities are more exposed. I believe the mean of age for diving has impacted the mean of age for white shark attacks, but doesn't mean that they prefer one than others. When shark attack a human, feel that is not its  food and  doesn't eat. it thinks, it´s disgusting! 😂

Other problem is Availability *bias* can change our perceptions of risk and maybe the  researchers and witness can be impacted for this bias when identified the animals. The white is very famous on the movies where it hunt people.  In fact,  that species need be protected against illegal fishing and others human activities that reducing their population. By the way, a good question: Shark attacks is growing up while population is reducing. Why? 🤔











