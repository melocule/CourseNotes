# Part 1: Encodings
## Part 1a
![[Pasted image 20220128164856.png]][Matrix Diagram (Y-Shaped) | Data Viz Project](https://datavizproject.com/data-type/matrix-diagram-y-shaped/)

### What I liked
I find this visually intruiging because I've never seen it being used before, despite it being a type of matrix which everyone feels pretty familiar with. Unlike the typical matrix however, this is able to visualize 3 categorical variables instead of 2, which brings in more possibilities.

### What I didn't like
I couldn't really understand how the data was encoded at a glance. The bottom dot-filled corners seem to be using perspective as if it were a 3D shape, but the 'roof' of the shape was two-dimentional even though it was also a grid. It clicked when I saw the examples they listed, but the mismatched use of perspective and even the text being at an angle was unsettling and slightly uncomfortable to read.

<div style="page-break-after: always;"></div>


## Part 1b

1.  What does “Input” mean? How are the visualizations categorized in this scheme? How does (if at all) this map to the language in our readings?

Input means the raw tabular data that is being directly visualized. 

The visualizations are divided by the format of their input-- the type of data (range, value, category), and how they are organized into rows and columns in tabular form. 

This maps to **tables** in our readings, as well as **attribute types** of the **fields** in the table. 

3.  What does “Shape” mean? How are the visualizations categorized in this scheme? How does (if at all) this map to the language in our readings?

Shape is the sillouette of visualization. They're categorized into different kinds of sillouettes, not necessarily literally visually similar ones (e.g. infographic shapes are very different from each other) but moreso the thought behind the shape.

This does **not** map to how the word "shape" is used in our readings, where it is a channel for an attribute marking instead of the overall shape. Two scatterplots can use different shapes as channels, yet be categorized as having different shapes on this website. It maps better to an  **idiom** from our readings.

5.  What does “Function” mean? How are the visualizations categorized in this scheme? How does (if at all) this map to the language in our readings?

Function means the purpose of the visualization for the user-- what they want to clearly see/understand using this data visualization (e.g. if they want to compare attributes, understand a concept, see correlations).
This closely maps to the "why" of the 3 questions asked to understand the use of a data visualization from the start of our textbook.

<div style="page-break-after: always;"></div>


# Part 2: Xenographics

1.  What is the Xenographics project, and what is its goal?
It's a repository of strange, experimental visualizations managed by Maarten Lambrechts with the intent to fight "xenographphobia", inspire others, and popularize new chart types.

3.  How are the visualizations categorized and organized on the project website?
On the homepage there is no clear default ordering, and no way to select the order that the visualizations appear. However, there are search functions and you can select by the tags  that the visualizations are categorized by: 
- Correlation
- Distribution
- Domain specific
- Geo
- Hierarchy
- High dimensional
- Mashup
- Network
- Scale stacking
- Time

5.  What was the most interesting or surprising thing you learned by watching the talk and exploring the website?
I explored the individual xenographs which were each interesting, but I felt like I learned the most from the article he's published on the site: [On Graphonyms: the Importance of Chart Type Names – Xenographics](https://xeno.graphics/articles/on-graphonyms-the-importance-of-chart-type-names/)
It exposed me to a taste of what the data visualization culture is like, and where it is in its development-- new visualizations appear all the time, and they haven't been named yet.

7.  Provide a link and short description to your favorite visualization on the website.
[Time curve – Xenographics](https://xeno.graphics/time-curve/)
There was no explanation of it directly on the page, but I found a good one here: [Time Curves: Folding Time to Visualize Patterns of Temporal Evolution in Data (inria.fr)](https://hal.inria.fr/hal-01205821/document)

This represents time as position along the length of a string, and then pulls parts of the string closer and further apart by the similarity of the value there. This is not only visually playful, but useful for comparing values over time to quickly find clusters and repetition.