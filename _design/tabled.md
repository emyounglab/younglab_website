# Tabled text (2026-10-02)

Text the Final canvas has no place for, lifted verbatim from HEAD 428dca2 during the CSS/markup recode. Not published (Jekyll skips _design/). Restore, cut, or rehome each item.

## research.md

### Map caption, third sentence (the first two are now the Research lede)

> This is sometimes called host onboarding: developing the foundational genetic tools an organism needs to enter the biofoundry pipeline for high-throughput combinatorial pathway engineering.

### Current Funding line (map panel)

```html
<p class="rmap-funding">NSF CREATE Biofoundry &middot; WPI BioHub &middot; DEVCOM &middot; Evonik &middot; Takeda &middot; <a href="#funding">all funding</a></p>
```

### Part Kits: paragraph and Addgene widget

```html
<details class="research-section" id="part-kits">
<summary><h2>Part Kits</h2></summary>
<p>We distribute standardized genetic part kits that enable reproducible synthetic biology across labs and organisms. The MoClo kits follow modular cloning, a standard that enables parts from different labs to assemble in a single reaction. We distribute through Addgene.</p>
<ul class="project-links">
  <li><a href="https://www.addgene.org/kits/young-opencidar/">OpenCidar</a></li>
  <li><a href="https://www.addgene.org/browse/article/28252864/">Xd MoClo</a></li>
  <li><a href="https://www.addgene.org/browse/article/28275214/">Dh MoClo</a></li>
</ul>
{% include addgene-widget.html %}
</details>
```

### Software Projects: PRYMETIME description and its four uses

```html
<details class="research-section" id="software-projects">
<summary><h2>Software Projects</h2></summary>
<p>We have developed open-source tools for synthetic biology design, data analysis, and genetic engineering workflows.</p>

<h3><a href="https://github.com/emyounglab/prymetime">PRYMETIME</a></h3>
<p>Pipeline for Recombinant Yeast genoMEs That Identifies Markers of Engineering. It assembles yeast genomes from long and short reads and finds the engineering in them. <a href="https://doi.org/10.1038/s41467-021-21656-9">Introduced in 2021</a>, it has since carried four lines of work:</p>
<ul class="tool-uses">
  <li><b>Onboarding our own yeasts.</b> Reference genomes for <a href="https://doi.org/10.1128/MRA.00397-23"><i>Kregervanrija delftensis</i></a> and <a href="https://doi.org/10.1128/MRA.00611-22"><i>Ogataea polymorpha</i></a>.</li>
  <li><b>Detecting engineering in unknown samples.</b> <a href="https://doi.org/10.1021/acssynbio.3c00398">Ensemble detection of DNA engineering signatures</a> across many target organisms, for IARPA FELIX.</li>
  <li><b>Sequencing yeasts we did not engineer.</b> With Reeta Rao, the <a href="https://doi.org/10.1093/g3journal/jkad093">genetic basis of probiotic yeast phenotypes</a> and the <a href="https://doi.org/10.1128/iai.00103-24">virulence and drug tolerance of <i>Candida auris</i></a>.</li>
  <li><b>Verifying engineered strains.</b> With Claudia Vickers, how <a href="https://doi.org/10.1021/acssynbio.3c00363">plasmid integration diversifies an engineered strain</a>.</li>
</ul>
</details>
```

### Organizations: sentence

```html
<details class="research-section" id="organizations">
<summary><h2>Organizations</h2></summary>
<p>We build and share automation capacity through two biofoundries, described under <a href="#biofoundries">Biofoundries</a>.</p>
<ul class="project-links">
  <li><a href="https://createbiofoundries.org">CREATE Biofoundry</a></li>
  <li><a href="https://massbiohub.org">BioHub</a></li>
</ul>
</details>
```

### Closing line

```html
<p class="research-join">We take PhD students, undergraduates, and postdocs. See <a href="{{ '/join/' | relative_url }}">Join the lab</a>.</p>
```

## people.yml fields no longer rendered

PI phone, building, room, address, affiliations and the titles links are still in _data/people.yml; the canvas People page shows only bio and the links line. _includes/person-card.html (the old renderer, with the Contact/Phone/Address popups) is deleted; recover it from git if needed.

## join.md (old copy, replaced by the mockup copy)

```html
<p class="lead lead-blue">We welcome motivated students and researchers interested in <strong>synthetic biology, metabolic engineering, genomics, and microbiology</strong>. Our work sits at the interface of chemical engineering and biology, and we value both wet-lab and computational skills.</p>
<div class="pub-section">
<h2 id="phd-ms">Prospective PhD and MS students</h2>
<p>Apply through the <a href="https://www.wpi.edu/academics/departments/chemical-engineering/graduate">WPI Chemical Engineering graduate program</a>. After submitting your application, feel free to reach out by email with your CV and a brief note about your interests.</p>
<p><strong>What to include in your email:</strong></p>
<ul>
  <li>2–3 sentences on why you're interested in the Young Lab specifically</li>
  <li>Relevant experience (wet lab, computation, genomics, fermentation, etc.)</li>
  <li>Your timeline and availability</li>
</ul>
</div>

<div class="pub-section">
<h2 id="undergraduates">Undergraduate researchers</h2>
<p>WPI undergraduates interested in working in the lab are encouraged to email Prof. Young directly. Please include your interests, relevant coursework or experience, and your résumé.</p>
</div>

<div class="pub-section">
<h2 id="postdocs">Postdoctoral researchers</h2>
<p>Please email a CV and a brief research statement describing how your interests align with our ongoing work. Candidates with backgrounds in metabolic engineering, synthetic biology, microbial genomics, or related fields are encouraged to apply.</p>
</div>

<div class="pub-section">
<h2 id="collaborators">Collaborators and visiting scholars</h2>
<p>We are open to collaborations with academic and industry partners. Send a short note describing the project idea and any relevant timelines.</p>
<p><strong>Contact:</strong> <a href="mailto:emyoung@wpi.edu">emyoung@wpi.edu</a></p>
</div>
```

## research.md: Organism Onboarding paragraphs (replaced 2026-10-02 by Parts collections / Genomes and transcriptomes)

```html
<p>In yeasts we have developed two hosts, <a href="https://doi.org/10.1101/2025.10.23.684212"><i>Debaryomyces hansenii</i></a> and <a href="https://doi.org/10.1007/s00253-024-13379-w"><i>Xanthophyllomyces dendrorhous</i></a>, that can grow on inexpensive sugars, and we use <a href="https://doi.org/10.1002/bit.28891">comparative transcriptomics</a> to characterize a new yeast before we engineer it. The same foundation has produced reference genomes and phenotype maps for other nonconventional yeasts &mdash; <a href="https://doi.org/10.1128/MRA.00397-23"><i>Kregervanrija delftensis</i></a>, <a href="https://doi.org/10.1128/MRA.00611-22"><i>Ogataea polymorpha</i></a>, and <a href="https://doi.org/10.1093/g3journal/jkad093">probiotic strains characterised by nanopore sequencing</a>.</p>
<p>In bacteria we have developed <a href="https://doi.org/10.1021/acssynbio.3c00104">a genetic part library</a> that is generalizable to a large set of gram negative soil bacteria and biomaterial producing bacteria, using a broad host range plasmid to test already designed DNA parts in various organisms. We have tested this in <i>Pseudomonas putida</i>, a soil bacterium with unusual metabolic versatility and tolerance of chemical stress, which makes it a durable host, or chassis, for sensing in the field; in <i>Cupriavidus necator</i>, a potential platform host for biomaterial production from CO<sub>2</sub>; and in <a href="https://doi.org/10.1101/2023.08.21.554206">bacterial nanocellulose producing bacteria</a>.</p>
```
