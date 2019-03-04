|考虑网络结构|考虑结构和其他信息|DL|Graph Conv|GAN|
|:-:|:-:|:-:|:-:|:-:|
|DeepWalk|CENE|ANE|[GCN](https://arxiv.org/pdf/1609.02907.pdf)|GraphGAN|
|LINE|CANE|SDNE|[GraphSAGE](https://papers.nips.cc/paper/6703-inductive-representation-learning-on-large-graphs.pdf)||
|GraRep|Trans-net|[ASNE](https://arxiv.org/pdf/1705.04969.pdf)|||
|node2vec|[TANE](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.703.7147&rep=rep1&type=pdf)|[DANE](https://www.ijcai.org/proceedings/2018/0467.pdf)|||
|struct2vec|[AANE](http://www.public.asu.edu/~jundongl/paper/SDM17_AANE.pdf)||||
|[HOPE](https://www.cs.sfu.ca/~jpei/publications/Graph%20Embedding%20KDD16.pdf)|[ABNE](https://arxiv.org/pdf/1811.11728.pdf)|||
---
# 1 用什么模型？
模型的选择有很多种，从古典方法，到只考虑结构信息，再到考虑节点和边的信息，再到深度模型，令人眼花缭乱。
选择模型一定要和你的实际问题相关：
- 实际问题更加关注内容相似性（局部邻域相似性）那么可以选择：node2vec，LINE，GraRap等；
- 实际问题更加关注结构相似性：struct2vec，蚂蚁金服使用struct2vec相比node2vec有质的提升；
- 考虑节点和边的额外信息：CANE，CENE，Trans-net等；
- 处理大规模易变图：可以采用GraphSANE，或者先采用其他GE方法，再使用GraphSANE归纳学习；
- 微调模型：GraphGAN；
- 整合学习：将得到的向量表示聚合，如concat等方式。

总之，用什么模型取决于你的问题！
(from 吴天龙）
# 2 模型学习
## KDD17-metapath2vec
对DeepWalk和Skip-gram模型进行修改，以适应异质网络。随机游走的路径基于Meta-path，下一个节点必须符合Meta-path的规则，比如Author-Paper-Author元路径，当前节点为Paper，则随机游走的节点必须在Author节点进行选择。Skip-gram的输出对节点进行分类，而不是对所有节点的概率进行输出。
## VLDB11-PathSim: Meta Path-Based Top-K Similarity Search in Heterogeneous Information Networks
提出一种元路径的方法度量查询之间的相似度，元路径方法可以保存路径之间的结构信息。如APA可以保存引用关系或者协作关系，APCPA可以保存作者与作者在会议级别的关系。
## SIAM13-Multi-view clustering via joint nonnegative matrix factorization
多视角聚类算法。
