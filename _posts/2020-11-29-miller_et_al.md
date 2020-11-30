---
layout: post
title: Paper using ReadFish
authors: 
 - Matt Loose
---

<blockquote class="twitter-tweet" data-dnt="true"><p lang="en" dir="ltr">Excited to share our work that demonstrates the clinical potential of targeted long-read sequencing. We use Read Fish (Read Until) on a <a href="https://twitter.com/nanopore?ref_src=twsrc%5Etfw">@nanopore</a> platform to systematically analyze clinical samples and find variants not seen w/clinical testing. 1/n <a href="https://t.co/DjE1Bi7wHh">https://t.co/DjE1Bi7wHh</a></p>&mdash; Danny Miller, MD, PhD (@danrdanny) <a href="https://twitter.com/danrdanny/status/1324079670577410048?ref_src=twsrc%5Etfw">November 4, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

It's great to see this [paper](https://www.biorxiv.org/content/10.1101/2020.11.03.365395v1) from Danny Miller and colleagues who have used ReadFish and selective sequencing to analyse the genomes of 33 individuals. They investigate the utility of adaptive sampling for a range of different questions of relevance to human disease and obtain approximately 20x coverage over all their targets on each flowcell.

This is a really interesting paper and a nice use of selective sequencing.  Now Oxford Nanopore have built this basic use case into MinKNOW, users with access to MinKNOW on a GridION MK1 can run this very easily. If you have access to GPU then you can use our [ReadFish](https://github.com/looslab/readfish) tools to do the same thing.

The 20x coverage can be improved by using a nuclease flush of the flowcell every 24 hours or so and also loading slightly more library than you would do normally. Depending on how many reads you will be rejecting, you will alter the read length profile of your library and - effectively - the molarity as far as sequencable ends. So we recommend overloading your library. 