---
layout:     post
title:      Data Augmentation for Deep Receivers
date:       2022-02-25 00:00:00
author:     Tomer Raviv
categories: jekyll
thumbnail:  database
tags:
 - augmentation
 - domain-orientation
---

**TLDR** What is the role of data augmentation techniques in communication? What are the motivations for employing them? Be sure to check out [the new paper][1]!

**Motivation** Machine learning is a thriving field, with applications to many different domains. But no matter what domain you tackle, for training & finetuning you will need many labeled samples. As the model’s complexity and number of parameters grow - so does the amount of training data. But, one inherent limitation in the data collection process is that the data collected describes one stationary problem, i.e. some constant distribution. For example, language-to-language translation, or image-based object detection. This fact limits the applicability of ML to communication scenarios, which are dynamic by nature. Specifically, data collected for one time instance may be irrelevant to a second time instance, forcing data re-collection.

**Previous Approaches** Several approaches have been invented to allow neural-based digital receivers to constantly adapt under varying-channel conditions. The first type of approach targets the *model architecture*. The obtained data is used to train a compact neural network, e.g. [ViterbiNet][2] and [BCJRNet][3]; One which builds on domain knowledge to reduce the amount of parameters, and therefore the needed labeled samples. The second type targets the *training algorithm*, and how its design should facilitate rapid adaptation. For example, adopting a meta-learning approach could help the receiver learn some inductive bias applicable to many channel realizations. But, a promising third type deals with the *data aspect*.

**Data in Communication** How should data be used effectively? Previous methods employ active learning to choose the subset of the most confident symbols, for example in [this paper][4]. A [different scheme][2] uses forward error-correction (FEC) codes to increase the tolerance to channel errors, thus being able to train on the received word and its estimated original symbols even as the channel slightly changes. But, these methods only reduce the quantity of trainable symbols, while we suggest synthesizing more symbols.  cannot synthesize channel margins of tolerated errors for a given for online-supervised learning. But, these cannot synthesize more samples. One can then ask - how?

**Augmentations for Classical Domains** Augmentations are widely spread in machine learning. For example, [in computer vision][5], one has a diverse set of options for data augmentation -- from crop and translation to color-jitter or cutout -- all of which modify an image without affecting its label. [In speech processing][6], data augmentation can be achieved using several domain-tailored transforms such as time warping and frequency masking. In both vision and speech, the purpose of using augmentations in their respective cases is to enrich the data set by exploiting domain knowledge regarding the nature of the data. The enriched set is then used for training the model with samples that may be observed during inference but are not included in the train set. But what should one take into account when employing communication tailored augmentations?

**Key Considerations for Communication Augmentations** We take several main pillars that are relevant to communication into account:
1. *Domain Oriented* - The proposed method should be [oriented towards the domain][7]. This is achieved by clustering the data based on the constellation symbol, and by adapting this clustering between blocks in block-fading channels as [a form of temporal smoothing][8].
2. *Diversity* - The number of samples per class is to be kept approximately uniform, so as to avoid biases towards one class or another, as specified in [this paper][9] and [this one][4].
3. *Complexity* - As our method has to be implemented by a digital receiver in real-time, we must keep the sample-complexity low, and the computation lightweight. 

**Proposed Approach** That’s it for my preview to augmentations in communications! See our proposed approach [in the paper][1], check it out!

[1]: https://github.com/tomerraviv95/data-augmentations-receivers

[2]: https://arxiv.org/abs/1905.10750

[3]: https://arxiv.org/abs/2002.00758

[4]: https://github.com/yoavchoen/Symbol-Level-Online-Training

[5]: https://arxiv.org/abs/2004.14990

[6]: https://arxiv.org/abs/1904.08779

[7]: https://epubs.siam.org/doi/pdf/10.1137/1.9781611974973.24

[8]: https://arxiv.org/abs/2012.01287

[9]: https://arxiv.org/abs/1906.02778
