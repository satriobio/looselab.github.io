---
layout: post
title: ReadFish Multiplatform Update
authors: 
 - Alex Payne
---

<div style="width: 450px; float: right;">
  <img src="/img/readfish_logo.jpg" width="400px">
</div>

Up until now [ReadFish][7], and selective sequencing, have been limited to users 
with both a linux OS and an NVIDIA GPU. In reality this requires a fairly 
large box - be it a GridION or a desktop able to support an NVIDIA 1080 GPU 
or above.
However, it would be ideal to be able to run selective sequencing on a laptop - 
even if it needs to be a moderately powerful device. This was already possible 
with ReadFish if you have a beefy NVIDIA GPU but many notable laptops *cough* 
Apple *cough* don't support this at this time.
Quite quickly after releasing our preprint people suggested using a CPU base 
caller:

<blockquote class="twitter-tweet" data-conversation="none" data-dnt="true"><p lang="en" dir="ltr">Or just do CPU basecalling ;) <a href="https://t.co/ICgitgG4Hj">https://t.co/ICgitgG4Hj</a></p>&mdash; Vlado Boza (@bozavlado) <a href="https://twitter.com/bozavlado/status/1225478731197812737?ref_src=twsrc%5Etfw">February 6, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Given the way we developed ReadFish, it is relatively straightforward to use 
different components. We therefore decided to implement an alternative base 
calling strategy using [DeepNano-Blitz][1] instead of [Guppy][2]. As a 
consequence we have been able to implement selective sequencing on computers 
without GPU and running Linux, macOS and even Windows. This brings the power of 
selective sequencing to laptops (with a few caveats below).

This also enabled [@mattloose][3] to spend a happy weekend running selective 
sequencing on a human genome at home. 

<figure>
  <img src="/img/homeseq.png">
  <figcaption>Happy home readfishing...</figcaption>
</figure>

## Results

So far we've run using DeepNano-Blitz on macOS, Windows (WSL), GridION, and 
Linux. In all cases we have seen enrichment comparable to running ReadFish 
using GPU accelerated base calling. A key caveat is that our DeepNano-Blitz 
implementation is currently non-adaptive; that is, it can enrich or deplete 
specific genomes or targets but this implementation does not automatically 
monitor reads as they are written or change targets during the experiment.

With that cleared up - what do we see? 
The figures below show coverage over BRCA1, PML and RARA, for runs on the 
GridION Mk1 CPU, a linux box we found in the lab, a MacBook Pro (2018 - 3.1 
GHz i7), and a windows desktop running Windows Subsystem for Linux (windows 10).
We also show two runs from our paper for comparison - the GridION Mk1 and the 
same linux box using an NVIDIA GTX 1080 GPU.

As can be seen, the coverage obtained with DeepNano-Blitz ReadFish is 
comparable (and on windows better!) than that seen on our original experiments.

<figure>
  <a href="/img/BRCA1.png"><img src="/img/BRCA1.png"></a>
  <figcaption>
    Coverage over BRCA1 when using the COSMIC panel and ReadFish either with 
    Guppy (GPU) base calling or DeepNano-Blitz (cpu). Smaller figures below 
    illustrate coverage over PML and RARA for the same experiments.
  </figcaption>
</figure>

<style>
/* Three image containers (use 25% for four, and 50% for two, etc) */
.column {
  float: left;
  width: 50%;
  padding: 5px;
}

/* Clear floats after image containers */
.row::after {
  content: "";
  clear: both;
  display: table;
}
</style>

<div class="row">
  <div class="column">
    <a href="/img/PML.png"><img src="/img/PML.png"></a>
  </div>
  <div class="column">
    <a href="/img/RARA.png"><img src="/img/RARA.png"></a>
  </div>
</div>

In the plot below you can choose a chromosome and look at the distribution of 
coverage for each target. Broadly speaking this is pretty uniform although a 
few targets have pseudogenes that could be cleaned up in future (for example 
see chromosome 4).

{% include 20201130_plot.html %}

The difference in coverage is largely down to down to yield for each flow cell. 
But there are some subtle differences which become apparent. Compare the GPU 
and CPU coverage on the GridION. The GPU experiment had much lower yield, but 
the median read length was shorter. Similarly, the Linux GPU has very low yield, 
but also one of the best median read lengths we have seen. The take home here 
is that speed is everything for efficient read until experiments. The faster 
you can unblock reads you don't wish to see, the better (and flushing your 
flow cell can help recover capacity). Thus the windows run shown here, at 
17&nbsp;Gb, uses brute force of yield to compensate for the longer reads 
observed. There is still room for tuning the windows based setup. 


|                      | GridION MK1&nbsp;GPU | GridION MK1&nbsp;CPU | Linux GPU    | Linux CPU     | MacBook Pro&nbsp;CPU | Windows CPU   |
|---------------------:|----------------------|----------------------|--------------|---------------|----------------------|---------------|
| *Mean Read Length*   | 735.6                | 878.9                | 683.7        | 771.2         | 1085.0               | 1146.9        |
| *Median Read Length* | 423.0                | 662.0                | 402.0        | 564.0         | 745.0                | 823.0         |
| *Yield*              | 9.08&nbsp;Gb         | 14.93&nbsp;Gb        | 5.90&nbsp;Gb | 14.31&nbsp;Gb | 14.03&nbsp;Gb        | 17.27&nbsp;Gb |
| *Mean Coverage*      | 31.30                | 29.78                | 19.11        | 27.78         | 29.08                | 34.47         |
| *Coverage Std*       | 5.54                 | 5.30                 | 3.23         | 5.09          | 5.24                 | 6.62          |
| *Flushes*            | 2\*                  | 2                    | 2            | 2             | 2                    | 3             |


## Hardware Requirements

To run everything from one laptop (or desktop) we recommend at least 16&nbsp;Gb 
of RAM, 8 processing cores and an SSD. The processor needs to be one of intel 
i7 or Xeon. 

ReadFish will use four cores for base calling and mapping an entire flow cell 
in real time, leaving the remainder of the CPU power for MinKNOW. We have not 
run on an infinite number of systems and your mileage may vary, but 
DeepNano-Blitz provides a number of different models that you can try.

## Caveats

This branch of ReadFish is under development and  provided as is for you to try 
out. 

Currently this is only compatible with R9.4 data on DNA. This contrasts with 
Guppy ReadFish, which can handle RNA as well as DNA and any currently shipping 
flow cell type from ONT.

We have not yet implemented real-time base calling for the downstream reads - 
so any of our tools that look at base called reads to inform the choice of 
reads for sequencing will not currently work.
 
## So how do I set this up?

To get started you will need to download the pre-built DeepNano-Blitz 
installers from here: [https://github.com/alexomics/deepnano-blitz/actions/runs/324655081][5].
These have been built for Linux (using Ubuntu 18.04) and macOS on Python 
versions 3.6, 3.7, and 3.8.

On Windows we use Windows Subsytem Linux (WSL) to run ReadFish. 
To setup WSL see the [Microsoft documentation][4]. Once this is 
installed you may need to install or upgrade the Python3 version 
to be one of 3.6, 3.7, or 3.8; now continue the install using the 
instructions for Linux.

#### Setup a virtual environment:

```bash
python3 -m venv venv
source ./venv/bin/activate
pip install --upgrade pip wheel
```

#### Install DeepNano-Blitz:

Choose the `.whl` file corresponding to your OS and python version. E.g:

```bash
pip install deepnano2-0.1-cp36-cp36m-linux_x86_64.whl
```

#### Install ReadFish:

```bash
pip install git+https://github.com/nanoporetech/read_until_api@v3.0.0
pip install git+https://github.com/LooseLab/readfish@caller_refactor

# Install ont_pyguppy_client_lib that matches 
#   your guppy server version. E.G.
pip install ont_pyguppy_client_lib==4.0.11
```

#### Setting the CPU caller

To use DeepNano-Blitz for base calling the `caller_settings` table in the 
experiment TOML file must contain the `network_type` parameter. For more 
information on the available parameters see [TOML.md][6].

[1]: https://academic.oup.com/bioinformatics/article/36/14/4191/5831289
[2]: https://www.nanoporetech.com
[3]: https://twitter.com/mattloose
[4]: https://docs.microsoft.com/en-us/windows/wsl/install-win10
[5]: https://github.com/alexomics/deepnano-blitz/actions/runs/324655081
[6]: https://github.com/LooseLab/readfish/blob/caller_refactor/TOML.md#deepnano-blitz
[7]: https://www.nature.com/articles/s41587-020-00746-x
