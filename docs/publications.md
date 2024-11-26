---
title: Publications
hide:
- navigation
- toc
---

# Publications

<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/pcooksey/bibtex-js@1.0.0/src/bibtex_js.min.js"></script>
<script src="../static/bib.js"></script>
<bibtex src="../static/works-complete.bib"></bibtex>
<style>
    /* Minimal style adjustments */
    h1.header { margin-left: 8px; }
    h1.YEAR { font-size: 17px; font-weight: bold; display: inline; margin-left: 8px; }
    ::placeholder { color: black; opacity: 1; }
    .pub svg { color: grey; }
    .pub.md-search__form {
        background-color: var(--md-default-bg-color);
        box-shadow: 0 0 .2rem #00000042;
        /*
        height: 2.4rem;
        position: relative;
        transition: color .25s,background-color .25s;
        z-index: 2; */
    }
</style>

<div class="pub" style="background-color: #white">
    <div class="md-search__form pub">
        <input type="text" class="md-search__input bibtex_search" name="query" aria-label="Search" placeholder="Search" autocapitalize="off" autocorrect="off" autocomplete="off" spellcheck="false" data-md-component="search-query" required="">
        <label class="md-search__icon md-icon" for="__search" style="color: black">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M9.5 3A6.5 6.5 0 0 1 16 9.5c0 1.61-.59 3.09-1.56 4.23l.27.27h.79l5 5-1.5 1.5-5-5v-.79l-.27-.27A6.516 6.516 0 0 1 9.5 16 6.5 6.5 0 0 1 3 9.5 6.5 6.5 0 0 1 9.5 3m0 2C7 5 5 7 5 9.5S7 14 9.5 14 14 12 14 9.5 12 5 9.5 5Z"></path></svg>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M20 11v2H8l5.5 5.5-1.42 1.42L4.16 12l7.92-7.92L13.5 5.5 8 11h12Z"></path></svg>
        </label>
    </div>
</div>

<br>

<div class="bibtex_structure">
  <div class="group year" extra="DSC number">
    <a href="#top" style="display: inline"><em>(Top of the page)</em></a>
    <div style="padding-bottom: 10px;"></div>
    <div class="sort journal" extra="DESC string">
      <div class="templates"></div>
    </div>
  </div>
</div>

<div id="bibtex_display">
  <div class="bibtex_template" style="display: none;">
    <ul>
      <li>
        <span class="if title">
          <a class="bibtexVar" href="http://www.website.com/~demo/papers/+BIBTEXKEY+.pdf" extra="BIBTEXKEY">
            <span style="text-decoration: underline;" class="title"></span>,
          </a>
        </span>
        <div class="if author">
          <span class="author"></span>
        </div>
        <div>
          <span class="if journal"><em><span class="journal"></span></em>,</span>
          <span class="if publisher"><em><span class="publisher"></span></em>,</span>
          <span class="if booktitle">In <em><span class="booktitle"></span></em>,</span>
          <span class="if address"><span class="address"></span>,</span>
          <span class="if month"><span class="month"></span>,</span>
          <span class="if year"><span class="year"></span>.</span>
          <span class="if note"><span class="note"></span></span>
        </div>
      </li>
    </ul>
  </div>
</div>