---
layout:     post
title:      Deploying DNN-aided Modules in Wireless Communication Networks
date:       2022-06-28 00:00:00
author:     Tomer Raviv
categories: jekyll
thumbnail:  database
tags:
 - physical layer
 - machine learning
 - deployment
---

**TLDR** Incorporation of neural networks into communication components has the potential to boost performance in terms of reliability, complexity, latency and the capability to handle complex settings. However, there exist a few obstacles that prevent the academia and industry from adopting neural networks in wireless communication devices. This short essay describes a few algorithmic-level methodologies that address these obstacles. 

**Physical layer** communication refers to the set of operators and functions responsible for
bit level transmission over some physical transmission medium. Several of these functions
include: the encoding of the transmitted bits via some codebook; their modulation into symbols;
the symbols transmission over the medium; their detection using an equalizer; and finally the
decoding which results in the transmitted bits.

**The physical layer pipeline** is designed to fulfill several basic requirements with respect to
three main properties: latency, complexity and reliability. Latency is transmission’s time span,
passed from the message generation up to the final reconstruction. Several applications, such
as autonomous driving and smart manufacturing systems, enforce a strict latency threshold
as defined in ultra-reliable and low-latency communication (URLLC). Complexity measures
the amount of computations needed, and their specific type. Hardware which is specialized
for a specific type of computations, may be unfit for computations of a different type. This
all means that the number and type of computations needed for the end-to-end transmission
should estimated apriori for one to match the relevant hardware. Lastly, reliability quantifies the
probability of successful transmission. As unsuccessful ones may require re-transmission, one
needs to optimize this metric with respect to the domain as well. For example, in the Internet
of Things (IOT) scenario, there exist a handful number of resource-constrained devices which
has to communicate with each other. Their resources limit the achievable reliability. 

**However,** the advancements of emerging technologies, such as autonomous driving and the
Internet of Everything (IoE), are accompanied by requirements that are harder to fulfill than
ever before. The growing-in-complexity environment is rich in transmitting devices, diverse
transceivers’ hardware and reflections, suffering greatly from loss in reliability. In environments
where the physical model is unknown, one would want to find a mathematical expression of the
input-to-output relationship; but it is usually infeasible due to insufficient domain knowledge.
Moreover, even if one had such a mathematical model of the environment, no analytical optimization algorithm is guaranteed to solve it in real-time. To comply with either model deficit or
algorithm deficit, one has to improve existing methods to fulfill the ever-growing demands

**We know that machine-learning algorithms** can learn complex functions from data alone.
Therefore, they must be the solutions to either model algorithm deficit cases. Just feed data to
a deep neural network (DNN)-aided model and be done with the problem! Well, not at all.
Even as machine-learning has the potential to revolutionize the field, there still exist a few
setbacks. These can be attributed to the nature of the domain. Communication channels are
dynamic, implying that the standard pipeline of data collection, annotation and training is not
applicable as in other domains such as computer vision or natural language processing. This
means that we must find ways to facilitate the training process of DNN-aided components after
deployment.

**Assuming that we want to deploy some DNN-aided component,** such as a detector or a decoder,
then one is likely to ask prior to deployment:
1. *What* is the specific architecture of the DNN-aided component?
2. *Which* initial weights should we choose?
3. *How* to make it more efficient in terms of complexity or latency?

**After answering the above questions ** and developing the desired module, the engineer deploys
the component. But now, the engineer faces performance degradation! This is due to dynamic
nature of wireless communication channels; From a machine learning perspective, the data
distribution constantly changes thus creating a mismatch between the train and test distributions.
These changes are attributed to either short term changes, as in the realization of a new channel,
or long term variations, as in the joining of a new mobile user to the network. No matter the
reason, on-device training and monitoring is likely to be essential for successful deployment.
Thus, the engineer now faces a new set of questions, post deployment ones:
1. *When* to re-train the DNN-aided component?
2. *What* approaches promote effective re-training from the available data?
3. *Which* part of the DNN-aided component requires training?
4. *How* to optimize the inference process?

**As the field become more mature,** we are likely to transition from the first set of questions to
the second one. A similar transition has been shown in software development (DevOps) and now
in machine learning (MLOps). While still improving the low-level blocks (such as [WBP][1] or
[ViterbiNet][2]) on synthetic datasets, we should now also develop tools that assist in integrating
these blocks to production and monitor them, in a more high-level, broad approach. This short
essay targets the gap in the algorithmic-level methodologies that facilitate the operation of neural
networks in communication devices. Specifically, the several next ideas, presented in short, target
the post deployment aspect.

*Acknowledgements* Thanks to [Nir Shlezinger][3] and [Yair Be'ery][4] for their feedback on this post.

[1]: https://arxiv.org/pdf/1607.04793.pdf

[2]: https://arxiv.org/pdf/1905.10750.pdf

[3]: https://sites.google.com/view/nirshl

[4]: http://www.eng.tau.ac.il/~ybeery/

