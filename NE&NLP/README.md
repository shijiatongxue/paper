# KDD17-metapath2vec
对DeepWalk和Skip-gram模型进行修改，以适应异质网络。
随机游走的路径基于Meta-path，下一个节点必须符合Meta-path的规则，比如Author-Paper-Author元路径，当前节点为Paper，则随机游走的节点必须再Author节点进行选择。
Skip-gram的输出对节点进行分类，而不是对所有节点的概率进行输出。