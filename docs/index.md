---
hide:
- navigation
- toc
---
<style>
    .jumbotron {
        position: relative;
        display: inline-block;
        width: 100%;
        max-width: 100%;
        overflow: hidden;
        height: 300px; /* Set fixed height */
    }

    .jumbotron img {
        display: block;
        width: 100%;
        height: 100%; /* Ensure image fills container height */
        object-fit: cover; /* Crop image to cover the container */
    }

    .overlay {
        position: absolute;
        bottom: 0;
        width: 100%;
        background: linear-gradient(to top, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0));
        color: white;
        padding: 20px;
        box-sizing: border-box;
    }

    .overlay h1 {
        color: white;
        font-size: 2.5rem;
        font-weight: bold;
        margin: 0;
    }

    .overlay p {
        color: white;
        font-size: 1.5rem;
        margin: 0;
    }

    .overlay a {
        color: white;
        text-decoration: none;
        font-weight: bold;
    }

    .big {
        color: #3b88c3;
        font-size: 3em; 
    }
</style>

<div class="jumbotron">
    <img src="../static/whale.jpg" alt="Name">
    <div class="overlay">
        <h1>Welcome</h1>
        <p>Loose Lab</p>
        <!-- <a href="#">Learn More</a> -->
    </div>
</div>

<br>

# About

Our research focuses on the robust implementation of long-reads sequencing  in different area of applications. We push the limits of sequencing platform by addressing important technical goals, from successfully obtaining intact chromosomes sequence and trying to enrich rare and elusive transcripts.

Our current research goal is but not limited to:

<!-- - Sequencing of of ultra-long or "whales" reads 
- Nanopore adaptive sampling for DNA and RNA
- Implementation of real-time nanopore data analysis -->

<div class="grid cards" style="text-align: center;" markdown>

- __:whale2:__{ .big }
    
    Sequencing of of ultra-long or "whales" reads

- __:simple-target:__{ .big }

    Nanopore adaptive sampling for DNA and RNA

- __:material-run:__{ .big }

    Implementation of real-time nanopore data analysis

</div>


## Featured Protocols and Tools

<div class="grid cards" style="text-align: center;" markdown>

- ![Image title](static/findingnemo.webp ){ width="150" }
    
    __:material-dna: Protocol:__ FindingNemo in OneDay

    ---

    Cell to Flowcell in One Day

    [:simple-protocolsdotio: Protocol.io](https://www.protocols.io/view/findingnemo-in-oneday-ultra-long-ont-library-prepa-14egnzqzyg5d/v1)

- ![Image title](static/readfish_light.png){ width="375" }

    __:material-fish: Tool:__ ReadFish

    ---

    Flexible and fast adaptive sampling

    [:material-github: Github](https://github.com/LooseLab/readfish)


- ![Image title](static/ROBIN_logo2_small.png){ width="186.41" }

    __:material-bird: Tool:__ ROBIN

    ---

    Real time analysis of nanopore methylation data

    [:material-github: Github](https://github.com/LooseLab/ROBIN)

</div>

<div style="text-align: center;" markdown>
  [Find more protocols and tools](research.md){ .md-button }
</div>

# News and Release

<div class="grid cards" markdown>

- __ReadFish Multiplatform Update__

    Up until now ReadFish, and selective sequencing, have been limited to users with both a linux ...

    2020-12-02

    [:material-open-in-new: Read](blog/2020/12/02/readfish-multiplatform-update/)

</div>

# Collaborators

<div style="display: flex; gap: 50px; justify-content: center; align-items: center;" markdown>

![northeastern](static/Shield_of_the_University_of_Birmingham.svg){ width="150" }

![northeastern](static/northeastern.png){ width="200" }

![ucsc](static/ucsc.png){ width="200" }

![nanopore](static/nanopore.png){ width="400" } 
    
</div>
<!-- </figure> -->
