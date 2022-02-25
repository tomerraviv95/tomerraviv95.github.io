---
layout:     post
title:      The State of ML-Based Communication
date:       2021-01-22 00:00:00
author:     Tomer Raviv
categories: jekyll
thumbnail:  heart
tags:
 - ML in communication
 - progress
---

**TLDR** I discuss the gap between the current and desired states in machine-learning based communication, including key points to consider in paper writing.

**Machine learning is here to stay.** It has had tremendous impact over plentiful domains, many of which were stuck because manual engineering of solutions is analytically unfeasible: There is no tractable mathematical relation between an image and the class of the animal therein. In communication, ML shines in two main scenarios: Either in a model deficit case, or an algorithmic deficit one ([paper][1]). 

**Trend** However, another ML trend is slowly becoming mainstream. This new trend applies ML to classical applications, considered solved both in academia and the industry. These specific cases are of little theoretical or practical interest; It seems they are explored simply because ML is the new kid on the block. What are the causes for this unsettling phenomena?

**Data** Several major distinctions must be made between ML in comms and in other typical fields. The first aspect is the data. In comms, we typically run on simulated data; the setup (e.g. constellation, channel etc.) is fully controlled by the user. So while in most domains the distribution of the data is given, in comms it can change as one wishes. 

**Task** In the dominant domains, many tasks are well defined: image classification, object detection, translation and much more. Current research applies ever-more sophisticated methods to nail another 1% in performance, as is clearly shown [here][2]. We, the ml comms researchers, are still busy with defining the exact tasks. Signal detection then? OK, but with or without CSI? And how to measure success? Performance, complexity and latency metrics are all important. 

**Education** There are some [amazing tutorials][3] out there. However, it is obviously not enough to educate beginners in the field. A CV practitioner has limitless options, from online courses, both in academia and in MOOCs, to interactive hands-on experience and books. This not only helps students to enter an unknown field, but also sets a common ground among all colleagues working under the same intellectual umbrella.

**Gradient Descent** Even as (1) easy access to abundance of data, (2) undefined tasks and (3) lack of proper education may all result in ineffective research, I do believe that ml-based comms is headed in the right direction. As research in the field becomes more mature, many unknowns will become apparent; Then we will see less papers employing a DL tool just because it is cool. 

**Downfalls** In the last 2 years, I’ve had the opportunity to review over 20 papers in the field. For better or worse, many had avoidable downfalls. The effect of these critical mistakes is split into two: Locally, these individual stumbles harm the acceptance of a paper; An experienced practitioner should know the minutiae of the field. Globally, as we all stand on the shoulders of giants, a single neglection of important details could lead, in the long term, to a handful of papers making similar mistakes. As such, I concentrated several such downfalls. Addressing even several of them in your paper will be of great service both to yourself, and the colleagues in the field.

**Proper Baseline** Comparison of DL to non-DL methods is like walking on a thin line. To keep an analysis of apples to apples, one should present both DL and non-DL approaches, with the specific doses depending on the application itself. A new training scheme? Better to test it on multiple DL-based architectures. Developed a new parameterized model from a classical one? Then both the vanilla and the weighted one are to be introduced. 

**Complexity** Moreover, note that while errors rates’ simulations are straightforward, overall complexities are much harder to measure in DL versus non-DL cases. Common metrics I’ve seen are: (1) the number of iterations, (2) additions and multiplications or (3) total parameters. There is no magic answer, the chosen metric depends on the analyzed methods and baselines. If you prefer to avoid this fuss, still remember to include some reference on the overall complexity; Comms is not a one-dimensional accuracy optimization problem. 

**Ablations Studies** These are the simulations that prove your solution is complete in terms of performance: removing components, altering strategies or substituting the model all hurt the measurable metrics. But how to choose which ablations are vital? First, it starts with understanding what your purpose is. Are you trying to show that the model generalizes well? Diverse? Adapts quickly? Each chosen characteristic requires a different study. Yet, all studies are to have a tight connection with the communication domain; Testing different channels is relevant, but varying learning rates or batch sizes -- not as much.

**Reproducibility** It is natural to divide the reproducibility of a paper into three levels: (1) empirical results, (2) code and (3) full computational environment. (1) As a rule of thumb, when there are more than 3-4 hyperparameters, it is wise to include all in a suitable table. Ofcourse, the table exists as a support to the text; Hyperparameters should also be mentioned either briefly or explained deeply within. (2) While common in other domains, it is still a rare sight in comms. Knowledge is much easier to digest with the code that supports the evidence, rather than through hollow equations or distant theory. (3) I have not run into a single paper that exports the full dependencies in an accessible way (e.g. docker).

**Architectures** Embed domain knowledge in your architectures! Feature engineering, model parameterization and much more... While throwing an RNN on the problem is tempting, it contributes little to the advancement of the field or to the understanding of the reader. Another thumb rule: As long as there is no benefit of the parameterized architecture on the classical vanilla one, this solution is irrelevant. Lastly, a domain-oriented method is the way to a fully scalable solution. 

**Standards** It all starts and ends with the standards we employ. Set a high bar in all aspects: research works, peer reviews and presentations.

*Acknowledgements* Thanks to [Nir Shlezinger][4] and [Yair Be'ery][5] for their feedback on this post.

[1]: https://ieeexplore.ieee.org/document/8542764

[2]: https://paperswithcode.com/sota/object-detection-on-coco

[3]: https://www.youtube.com/watch?v=tWBMgre6VWE

[4]: https://sites.google.com/view/nirshl

[5]: http://www.eng.tau.ac.il/~ybeery/
