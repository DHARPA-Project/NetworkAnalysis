# Network Analysis

Network analysis examines relationships among entities, such as persons, institutions, documents, or words. Navigating between multiple scales, one can use network analysis to describe and draw conclusions about relational properties of individual entities, of subsets of entities, and of entire networks. Thus, network analysis is well suited to approach research questions that focus on relationships and offers a way to integrate micro and macro perspectives.

## Table of contents

1. [The DHARPA Project](#1-the-dharpa-project)
2. [Methodological considerations](#2-methodological-considerations)

   2.1 [Networks are abstractions](#21-networks-are-abstractions)

   2.2 [When should I use Network Analysis?](#22-when-should-i-use-network-analysis)
   
   2.3 [Methods and data](#23-methods-and-data)

   2.4 [Terminology](#24-terminology)
  
3. [Getting started](#3-getting-started)
4. [Conclusions](#4-conclusions)
5.  [Remarks](#5-remarks)
6.  [License](#6-license)
7.  [Links](#7-links)
8.  [References](#8-references)
9.  [The team](#9-the-team)
10. [How to cite](#10-how-to-cite)

## 1. The DHARPA Project
While the ‘digital humanities moment’ has yielded great accomplishments and enthusiastic interdisciplinary cooperations across the humanities and between the humanities and the sciences, concerns have been raised about the little transparency in digital practices as well as the difficulty of replicating studies due to the lack of data access or standardised practices as well as unclear methodological processes (Faull et al 2016; Jakacki et al 2016, 2015; O’ Sullivan 2019). Such concerns have for instance led scholars to claim that digital humanities is still in “search of a methodology” (Dobson 2019) and the metaphor of the 'black box' has started to be used (Smith 2014) to describe the apparent loss of human agency in the digital reseach process. This could be to some extent due to the fact that traditional historical inquiry itself has in some ways been like a “Mechanical Turk,” with the decisions and interventions made by the researcher hidden from view and only the well-oiled and seemingly autonomous product on display. The [**DHARPA Project**](https://dharpa-project.github.io/) (Digital History Advanced Research Projects Accelerator) aims to reverse this trend. We want to encourage historians and digital humanities scholars to lift the lid, to show how the application of their expertise works in tandem with technology to produce knowledge, how even digitally enabled research is not a product but a process, reliant on the critical engagement of the scholar. 

In this workflow, we aim to promote a self-reflective analysis of the interaction of technology and humanities practice and we use network analysis as a case study.

## 2. Methodological considerations

Almost everything can be represented in the form of a network. That does not mean that it will be useful or insightful. In the following, I will outline some basic considerations that need to be taken into account when considering network analysis as a method and introduce the basic teminology.

## 2.1 Networks are abstractions

Network graphs and the databases that are usually used to build them concentrate on one or a few sort of relationships between a limited set of actors, deliberately ignoring the fact that these actors necessarily have other relationships among themselves and with outsiders. Choices in "boundary specification" (whom do we observe? which ties among them? at what time(s)?) heavily constrain the sort of questions that can be analyzed by network analysis. This implies, on the one hand, that interpretations based on network data should be careful not to reify notions such as centrality or isolation, that are always relative to a choice of relations and actors observed; on the other hand, nothing prevents us to study some sorts of relations thanks to some historical sources, even if they generally do not systematically record all the sorts of relations that we would be interested in (Lemercier, 2015).

## 2.2 When should I use Network Analysis?

Network Analysis is a collection of methods that can be useful to study complex relational patterns. If you are interested in studying such patterns and have already identified them in your sources, then there is a good chance that network analysis will help you to explore and analyse them in greater depth. You might still need to think more carefully about what exactly the entities (nodes) are that you want to study and how exactly the relationships (edges) between them can be expressed and defined. The clearer your conception of these elements, the more solid your network analysis project will be.

In order to be able to do network analysis, your data will need to be in a certain shape. Typically, the data would be retrieved from a database. Some table data might also be easily tweaked into an appropriate format, but if your starting point is a collection of unstructured text (like .txt files) then some preprocessing steps will be necessary to parse the data into a format suitable for network analysis before you can start analysing anything.

A good guide to help answering the question whether or not it is worthwhile and feasible to engage with network analysis can be found here: https://cvcedhlab.hypotheses.org/125

## 2.3 Methods and data

Some methods, like calculating centralities, or detecting or discovering communities in a network, will be appropriate for all sorts of datasets and a variety of research questions. It does not matter if the network is small or large, if it constitutes a social network or a text network. These methods can provide insights that are otherwise difficult to obtain and can raise new research questions. However, the meaning and interpretation of the results of these methods can be very specific to the individual network. In the following, I will describe approaches to calculate centralities and to detect communities in a realtively abstract way. Ideas on how some of the results can be interpreted in light of a case specific research question can be found in the various Jupyter notebooks in this repository.

As with many other methodological choices in network analysis, the choice of the graph type (directed, undirected etc.) can substantially affect the results of centrality measures and community detection outcomes. Which choice or combination makes the most sense will depend on the research question. Some researchers will want to investigate different aspects of their network and explore their data in the form of different graph types. Others will have a more narrow research question and focus on one set of methods tailored to one particular graph type.
Generally speaking, research questions focusing on the analysis of "structure" will indicate a preference for an undirected graph, while the focus on "flow" will indicate a directed network and imply the use of the associated methods. Those are not necessarily mutually exclusive, and a more general research question would entail that a researcher investigates both structure and flow.

### Calculating Centralities

One of the most common operations in network analysis is to identify important nodes.
What makes a node important depends on your network and your notion of importance.
An important node might be a node that has the most connections. A node
with one connection has a degree of one and degree centrality is a way for calculating a normalized value for this measure. 
Another kind of “importance” is betweenness-centrality. It indicates a node
that lies between two distinct parts of a network (A node through which most "shortest paths" pass through). A node with high betweenness centrality
can indicate that the node is a “broker” or a “gatekeeper”. 

Here are some (but not all!) of the more popular centrality measures:

**Closeness centrality** is measuring how close a node is located with respect to every other node in the network.

**Degree centrality** is a measure to identify the nodes which have the most connections in the network, they are often interpreted as **hubs**.

**Betweenness centrality** looks at all the shortest paths that pass through a particular node. It is expressed on a scale of 0 to 1 and is good at finding nodes that connect two otherwise disparate parts of a network. 
In contrast to a **hub**, this sort of node is often referred to as a **broker** because the value can be interpreted as indicating a node with an active brokering role in the network.

**Eigenvector centrality** considers if a node has many direct connections on its own, but it also considers how it is connected to other highly connected nodes. It’s calculated as a value from 0 to 1: the closer to one, the greater the centrality. In information networks, eigenvector centrality is useful for understanding which nodes can get information to many other nodes quickly. If you know a lot of well-connected people, you could spread a message very efficiently.

It is important to note that all these different labels (hubs, brokers) constitute **interpretations** of the obtained numbers and generate assumptions about the roles of individual actors in a network.
Edge **weights** can significantly alter some of these centrality measures and yield very different rankings in terms of centrality. Because weights are interpreted as the "connection strength" in some measures and as "distance" (or cost) in other measures, it is important to adjust calculations according to the type of network. For example, this can imply that it might be appropriate to invert the egde weights when calculating weighted betweenness centrality in an information network. 

Depending on the choice of centrality, very different nodes in a network can be identified as "important" in one way or other (Ortiz-Arroyo, 2010):

![image](https://user-images.githubusercontent.com/53467834/173307418-51d741b3-fff3-4708-ad4e-987653534d29.png)


### Detecting Communities

Community detection is a popular operation in network analysis, especially with social
networks like social media groups, but it also has its uses with text networks.
This method idetifies groups of nodes that belong together based on one or several properties of the graph.
By partitioning the graph into distinct communities, it is possible to detect node characteristics that are otherwise not recorded (as node attributes) or not easily discernible.
If nothing else, this method can help to raise new questions about the network and initiate a search for the unknown common denominators among the nodes that were placed in the same community according to the partition of the community detection algorithm.

A common approach is to identify communities by searching for node clusters in a network that have a notably higher density. These density clusters can then be interpreted as distinct communities within the network.

There are specialized methods to detect communities in **directed networks**. In most cases, those methods would rely on analyzing flow rather than structure. Depending on the data and research question, it can be very misleading to use community detection algorithms on directed graphs that have been originally developed for undirected graphs ("It is clear that ignoring edge directionality and considering the graph as undirected is not a meaningful
way to cluster directed networks as it fails to capture the asymmetric relationships implied by the edges
of a directed network." (Malliaros & Vazirgiannis, 2013)).
A flow-based community detection algorithm (like the "infomap" algorithm) can, for example, detect citation patterns in citation networks.

It is also possible to search for **overlapping communities** where nodes belong to more than one group. Some methods can be found here: https://cdlib.readthedocs.io/en/latest/overview.html

## 2.4 Terminology

|          Term         |                                                                                                                                                   Description                                                                                                                                                  |
|:---------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| Actor                 | The entity which is described by a node, e.g. a person, an institution etc.                                                                                                                                                                                                                                    |
| Broker                | A node which is positioned e.g. between two clusters and can act as a “bottleneck”                                                                                                                                                                                                                             |
| Community             | A set of nodes which are relatively more connected to each other than to the rest of the graph                                                                                                                                                                                                                 |
| Co-occurrence network | A network in which the edge between nodes is based on the fact that both  appear together in the same context, usually in texts. An example would  be two people who are mentioned in the same paragraph.                                                                                                      |
| Component             | A connected part of the network. Networks often consist of multiple disconnected components. An isolated node can be considered to be a component.                                                                                                                                                             |
| Degree of a node      | The number of edges connected to this node. Variants include in-degree/out-degree, which counts the number of ingoing and outgoing edges in a directed network. Sometimes indicated by the size of the  sphere representing the node. Also called degree centrality when normalized.                           |
| Diameter of a network | The shortest distance between the two most distant nodes in the network i.e. the largest shortest path lenght.                                                                                                                                                                                                 |
| Directed network      | A network in which the edges are directional, e.g. when actor A sends a letter to actor B.                                                                                                                                                                                                                     |
| Dyad                  | A group of two connected nodes, the smallest possible network                                                                                                                                                                                                                                                  |
| Edge                  | Connection, also called link, arc, or tie between nodes.                                                                                                                                                                                                                                                       |
| Edge attribute        | Data which describes a certain aspect of an edge, for example how often two actors speak to each other.                                                                                                                                                                                                        |
| Ego network           | A network which contains all connections of an actor to their alteri and usually also the connections between the alteri. A classic example is a correspondence network derived from the collected letters of a single individual.                                                                             |
| Graph                 | (in a network and math. context): objects which are connected by links. However, often used interchangeably with “network” even by experts.                                                                                                                                                                    |
| Homophily             | The tendency of nodes to become connected to other nodes that are similar under a certain definition of similarity.                                                                                                                                                                                            |
| Hub                   | A node with a degree far higher than the average in a network.                                                                                                                                                                                                                                                 |
| Matrix                | A way of representing a network where there is a row and a column for each node, and the values in the cells indicate whether an edge exists between a pair of nodes.                                                                                                                                          |
| Multi-mode network    | A network with more than one node type, for example author-nodes, book-nodes, and subject-nodes; victim-nodes, suspect-nodes, crime-scene-nodes, and crime-weapon nodes.                                                                                                                                       |
| Node                  | Sometimes called a vertex. Refers to the object which is connected to other objects in a graph.                                                                                                                                                                                                                |
| Node attribute        | Data which describes a certain aspect of a node, for example an actor’s age or gender.                                                                                                                                                                                                                         |
| Node centrality       | Describes the extent to which a node is connected to other nodes within a  network. Various algorithms exist to describe different aspects of such  connectivity. To some extent centrality can be linked to abstract  notions such as “influence”, “power” or “importance”.                                   |
| One-mode network      | Also "unipartitite network". A network of just one  node type, in contrast to bipartite or multi-mode network.                                                                                                                                                                                                 |
| Projection            | Usually "projection of a bipartite network". When a bipartite network is projected, one of the node types is transformed into an edge. For example, instead of two people-nodes being  connected to a place-node, they are now connected to each other, and the place-node  becomes the edge connecting them.  |
| Shortest path         | The shortest path (fewest number of steps) between two  nodes in the network.                                                                                                                                                                                                                                  |
| Weighted network      | A network in which each edge has a numerical weight attached to it, indicating the strength (or intensity) of the connection. In an unweighted network all edges are assumed to have a weight of 1.                                                                                                            |                                                                               |

For sources see the [links](#7-links) section.

## 6. License
See COPYING file in this repository.

## 7. Links

### Introductions to Network Basics

http://www.scottbot.net/HIAL/index.html@p=6279.html

### Network terminology
https://cvcedhlab.hypotheses.org/106

https://folgerpedia.folger.edu/Glossary_of_network_analysis_terms

## 8. References

Marten Düring et al., eds., Handbuch Historische Netzwerkforschung: Grundlagen Und Anwendungen, Schriften des Kulturwissenschaftlichen Instituts Essen (KWI) zur Methodenforschung Band 1 (Berlin: LIT, 2016).

Claire Lemercier, “Formal Network Methods in History: Why and How?,” in Social Networks, Political Institutions, and Rural Societies, ed. Georg Fertig, Rural history in Europe 11 (Turnhout, Belgium: Brepols, 2015).

Fragkiskos D. Malliaros and Michalis Vazirgiannis, “Clustering and Community Detection in Directed Networks: A Survey,” Physics Reports 533, no. 4 (2013): 95–142, accessed June 13, 2022, https://linkinghub.elsevier.com/retrieve/pii/S0370157313002822.

Mark Newman, Networks: An Introduction (Oxford University Press, 2010), accessed December 3, 2020, https://oxford.universitypressscholarship.com/view/10.1093/acprof:oso/9780199206650.001.0001/acprof-9780199206650.

Daniel Ortiz-Arroyo, “Discovering Sets of Key Players in Social Networks,” in Computational Social Network Analysis, ed. Ajith Abraham, Aboul-Ella Hassanien, and Vaclav Sná¿el (London: Springer London, 2010), 27–47, accessed March 17, 2021, http://link.springer.com/10.1007/978-1-84882-229-0_2.

Deryc T. Painter, Bryan C. Daniels, and Jürgen Jost, “Network Analysis for the Digital Humanities: Principles, Problems, Extensions,” Isis 110, no. 3 (August 30, 2019): 538–554, accessed March 3, 2021, https://www.journals.uchicago.edu/doi/full/10.1086/705532.

John Scott, Social Network Analysis - SAGE Research Methods, 2017, accessed March 11, 2022, https://methods.sagepub.com/book/social-network-analysis-4e.

John Scott and Peter Carrington, The SAGE Handbook of Social Network Analysis (London, United Kingdom: SAGE Publications Ltd, 2014), accessed March 11, 2022, http://methods.sagepub.com/book/the-sage-handbook-of-social-network-analysis.

Stanley Wasserman and Katherine Faust, Social Network Analysis: Methods and Applications, Structural analysis in the social sciences 8 (Cambridge ; New York: Cambridge University Press, 1994).

Katharina A. Zweig, Network Analysis Literacy: A Practical Approach to the Analysis of Networks, 1st ed. 2016., Lecture Notes in Social Networks (Vienna: Springer Vienna : Imprint: Springer, 2016), https://link-springer-com.proxy.bnl.lu/book/10.1007/978-3-7091-0741-6.

## 9. The team

## 10. How to cite
To cite the repository, please use the following format according to the APA style guide:

Jaskov, Helena. 2022. *Network Analysis in Python* (v. 1.0.0). University of Luxembourg. https://github.com/DHARPA-Project/NetworkAnalysis
