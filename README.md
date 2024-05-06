
<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8" />
<meta name="generator" content="pandoc" />
<meta http-equiv="X-UA-Compatible" content="IE=EDGE" />


<meta name="author" content="Zheng Li" />

<meta name="date" content="2022-06-07" />

<title>Introduction to BASS</title>

<script src="site_libs/header-attrs-2.12.1/header-attrs.js"></script>
<script src="site_libs/jquery-3.6.0/jquery-3.6.0.min.js"></script>
<meta name="viewport" content="width=device-width, initial-scale=1" />
<link href="site_libs/bootstrap-3.3.5/css/cosmo.min.css" rel="stylesheet" />
<script src="site_libs/bootstrap-3.3.5/js/bootstrap.min.js"></script>
<script src="site_libs/bootstrap-3.3.5/shim/html5shiv.min.js"></script>
<script src="site_libs/bootstrap-3.3.5/shim/respond.min.js"></script>
<style>h1 {font-size: 34px;}
       h1.title {font-size: 38px;}
       h2 {font-size: 30px;}
       h3 {font-size: 24px;}
       h4 {font-size: 18px;}
       h5 {font-size: 16px;}
       h6 {font-size: 12px;}
       code {color: inherit; background-color: rgba(0, 0, 0, 0.04);}
       pre:not([class]) { background-color: white }</style>
<script src="site_libs/jqueryui-1.11.4/jquery-ui.min.js"></script>
<link href="site_libs/tocify-1.9.1/jquery.tocify.css" rel="stylesheet" />
<script src="site_libs/tocify-1.9.1/jquery.tocify.js"></script>
<script src="site_libs/navigation-1.1/tabsets.js"></script>
<link href="site_libs/highlightjs-9.12.0/textmate.css" rel="stylesheet" />
<script src="site_libs/highlightjs-9.12.0/highlight.js"></script>
<link href="site_libs/font-awesome-5.1.0/css/all.css" rel="stylesheet" />
<link href="site_libs/font-awesome-5.1.0/css/v4-shims.css" rel="stylesheet" />

<link rel="icon" href="https://github.com/workflowr/workflowr-assets/raw/main/img/reproducible.png">
<!-- Add a small amount of space between sections. -->
<style type="text/css">
div.section {
  padding-top: 12px;
}
</style>



<style type="text/css">
  code{white-space: pre-wrap;}
  span.smallcaps{font-variant: small-caps;}
  span.underline{text-decoration: underline;}
  div.column{display: inline-block; vertical-align: top; width: 50%;}
  div.hanging-indent{margin-left: 1.5em; text-indent: -1.5em;}
  ul.task-list{list-style: none;}
    </style>

<style type="text/css">code{white-space: pre;}</style>
<script type="text/javascript">
if (window.hljs) {
  hljs.configure({languages: []});
  hljs.initHighlightingOnLoad();
  if (document.readyState && document.readyState === "complete") {
    window.setTimeout(function() { hljs.initHighlighting(); }, 0);
  }
}
</script>









<style type = "text/css">
.main-container {
  max-width: 940px;
  margin-left: auto;
  margin-right: auto;
}
img {
  max-width:100%;
}
.tabbed-pane {
  padding-top: 12px;
}
.html-widget {
  margin-bottom: 20px;
}
button.code-folding-btn:focus {
  outline: none;
}
summary {
  display: list-item;
}
details > summary > p:only-child {
  display: inline;
}
pre code {
  padding: 0;
}
</style>


<style type="text/css">
.dropdown-submenu {
  position: relative;
}
.dropdown-submenu>.dropdown-menu {
  top: 0;
  left: 100%;
  margin-top: -6px;
  margin-left: -1px;
  border-radius: 0 6px 6px 6px;
}
.dropdown-submenu:hover>.dropdown-menu {
  display: block;
}
.dropdown-submenu>a:after {
  display: block;
  content: " ";
  float: right;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
  border-width: 5px 0 5px 5px;
  border-left-color: #cccccc;
  margin-top: 5px;
  margin-right: -10px;
}
.dropdown-submenu:hover>a:after {
  border-left-color: #adb5bd;
}
.dropdown-submenu.pull-left {
  float: none;
}
.dropdown-submenu.pull-left>.dropdown-menu {
  left: -100%;
  margin-left: 10px;
  border-radius: 6px 0 6px 6px;
}
</style>

<script type="text/javascript">
// manage active state of menu based on current page
$(document).ready(function () {
  // active menu anchor
  href = window.location.pathname
  href = href.substr(href.lastIndexOf('/') + 1)
  if (href === "")
    href = "index.html";
  var menuAnchor = $('a[href="' + href + '"]');

  // mark it active
  menuAnchor.tab('show');

  // if it's got a parent navbar menu mark it active as well
  menuAnchor.closest('li.dropdown').addClass('active');

  // Navbar adjustments
  var navHeight = $(".navbar").first().height() + 15;
  var style = document.createElement('style');
  var pt = "padding-top: " + navHeight + "px; ";
  var mt = "margin-top: -" + navHeight + "px; ";
  var css = "";
  // offset scroll position for anchor links (for fixed navbar)
  for (var i = 1; i <= 6; i++) {
    css += ".section h" + i + "{ " + pt + mt + "}\n";
  }
  style.innerHTML = "body {" + pt + "padding-bottom: 40px; }\n" + css;
  document.head.appendChild(style);
});
</script>

<!-- tabsets -->

<style type="text/css">
.tabset-dropdown > .nav-tabs {
  display: inline-table;
  max-height: 500px;
  min-height: 44px;
  overflow-y: auto;
  border: 1px solid #ddd;
  border-radius: 4px;
}

.tabset-dropdown > .nav-tabs > li.active:before {
  content: "";
  font-family: 'Glyphicons Halflings';
  display: inline-block;
  padding: 10px;
  border-right: 1px solid #ddd;
}

.tabset-dropdown > .nav-tabs.nav-tabs-open > li.active:before {
  content: "&#xe258;";
  border: none;
}

.tabset-dropdown > .nav-tabs.nav-tabs-open:before {
  content: "";
  font-family: 'Glyphicons Halflings';
  display: inline-block;
  padding: 10px;
  border-right: 1px solid #ddd;
}

.tabset-dropdown > .nav-tabs > li.active {
  display: block;
}

.tabset-dropdown > .nav-tabs > li > a,
.tabset-dropdown > .nav-tabs > li > a:focus,
.tabset-dropdown > .nav-tabs > li > a:hover {
  border: none;
  display: inline-block;
  border-radius: 4px;
  background-color: transparent;
}

.tabset-dropdown > .nav-tabs.nav-tabs-open > li {
  display: block;
  float: none;
}

.tabset-dropdown > .nav-tabs > li {
  display: none;
}
</style>

<!-- code folding -->



<style type="text/css">

#TOC {
  margin: 25px 0px 20px 0px;
}
@media (max-width: 768px) {
#TOC {
  position: relative;
  width: 100%;
}
}

@media print {
.toc-content {
  /* see https://github.com/w3c/csswg-drafts/issues/4434 */
  float: right;
}
}

.toc-content {
  padding-left: 30px;
  padding-right: 40px;
}

div.main-container {
  max-width: 1200px;
}

div.tocify {
  width: 20%;
  max-width: 260px;
  max-height: 85%;
}

@media (min-width: 768px) and (max-width: 991px) {
  div.tocify {
    width: 25%;
  }
}

@media (max-width: 767px) {
  div.tocify {
    width: 100%;
    max-width: none;
  }
}

.tocify ul, .tocify li {
  line-height: 20px;
}

.tocify-subheader .tocify-item {
  font-size: 0.90em;
}

.tocify .list-group-item {
  border-radius: 0px;
}


</style>



</head>

<body>


<div class="container-fluid main-container">


<!-- setup 3col/9col grid for toc_float and main content  -->
<div class="row">
<div class="col-xs-12 col-sm-4 col-md-3">
<div id="TOC" class="tocify">
</div>
</div>

<div class="toc-content col-xs-12 col-sm-8 col-md-9">




<div class="navbar navbar-default  navbar-fixed-top" role="navigation">
  <div class="container">
    <div class="navbar-header">
      <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-bs-toggle="collapse" data-target="#navbar" data-bs-target="#navbar">
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="index.html">BASS</a>
    </div>
    <div id="navbar" class="navbar-collapse collapse">
      <ul class="nav navbar-nav">
        <li>
  <a href="index.html">Introduction</a>
</li>
<li>
  <a href="about.html">Software tutorial</a>
</li>
<li>
  <a href="simu.html">Simulation</a>
</li>
<li class="dropdown">
  <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
    Real data analyses
     
    <span class="caret"></span>
  </a>
  <ul class="dropdown-menu" role="menu">
    <li>
      <a href="STARmap.html">STARmap (Wang et al., 2018)</a>
    </li>
    <li>
      <a href="MERFISH.html">MERFISH (Moffitt et al., 2018)</a>
    </li>
    <li>
      <a href="DLPFC.html">DLPFC (Maynard et al., 2021)</a>
    </li>
  </ul>
</li>
<li>
  <a href="license.html">License</a>
</li>
      </ul>
      <ul class="nav navbar-nav navbar-right">
        <li>
  <a href="https://github.com/zhengli09//BASS-analysis">
    <span class="fab fa-github"></span>
     
    Source code
  </a>
</li>
      </ul>
    </div><!--/.nav-collapse -->
  </div><!--/.container -->
</div><!--/.navbar -->

<div id="header">



<h1 class="title toc-ignore">Introduction to BASS</h1>
<h4 class="author">Zheng Li</h4>
<h4 class="date">2022-06-07</h4>

</div>


<p>
<button type="button" class="btn btn-default btn-workflowr btn-workflowr-report" data-toggle="collapse" data-target="#workflowr-report">
<span class="glyphicon glyphicon-list" aria-hidden="true"></span>
workflowr <span class="glyphicon glyphicon-ok text-success"
aria-hidden="true"></span>
</button>
</p>
<div id="workflowr-report" class="collapse">
<ul class="nav nav-tabs">
<li class="active">
<a data-toggle="tab" href="#summary">Summary</a>
</li>
<li>
<a data-toggle="tab" href="#checks"> Checks <span
class="glyphicon glyphicon-ok text-success" aria-hidden="true"></span>
</a>
</li>
<li>
<a data-toggle="tab" href="#versions">Past versions</a>
</li>
</ul>
<div class="tab-content">
<div id="summary" class="tab-pane fade in active">
<p>
<strong>Last updated:</strong> 2022-06-07
</p>
<p>
<strong>Checks:</strong> <span
class="glyphicon glyphicon-ok text-success" aria-hidden="true"></span> 7
<span class="glyphicon glyphicon-exclamation-sign text-danger"
aria-hidden="true"></span> 0
</p>
<p>
<strong>Knit directory:</strong> <code>BASS-analysis/</code> <span
class="glyphicon glyphicon-question-sign" aria-hidden="true"
title="This is the local directory in which the code in this file was executed.">
</span>
</p>
<p>
This reproducible <a href="https://rmarkdown.rstudio.com">R Markdown</a>
analysis was created with <a
  href="https://github.com/workflowr/workflowr">workflowr</a> (version
1.7.0). The <em>Checks</em> tab describes the reproducibility checks
that were applied when the results were created. The <em>Past
versions</em> tab lists the development history.
</p>
<hr>
</div>
<div id="checks" class="tab-pane fade">
<div id="workflowr-checks" class="panel-group">
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongRMarkdownfilestronguptodate">
<span class="glyphicon glyphicon-ok text-success"
aria-hidden="true"></span> <strong>R Markdown file:</strong> up-to-date
</a>
</p>
</div>
<div id="strongRMarkdownfilestronguptodate"
class="panel-collapse collapse">
<div class="panel-body">
<p>Great! Since the R Markdown file has been committed to the Git
repository, you know the exact version of the code that produced these
results.</p>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongEnvironmentstrongempty">
<span class="glyphicon glyphicon-ok text-success"
aria-hidden="true"></span> <strong>Environment:</strong> empty </a>
</p>
</div>
<div id="strongEnvironmentstrongempty" class="panel-collapse collapse">
<div class="panel-body">
<p>Great job! The global environment was empty. Objects defined in the
global environment can affect the analysis in your R Markdown file in
unknown ways. For reproduciblity it’s best to always run the code in an
empty environment.</p>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongSeedstrongcodesetseed0code">
<span class="glyphicon glyphicon-ok text-success"
aria-hidden="true"></span> <strong>Seed:</strong>
<code>set.seed(0)</code> </a>
</p>
</div>
<div id="strongSeedstrongcodesetseed0code"
class="panel-collapse collapse">
<div class="panel-body">
<p>The command <code>set.seed(0)</code> was run prior to running the
code in the R Markdown file. Setting a seed ensures that any results
that rely on randomness, e.g. subsampling or permutations, are
reproducible.</p>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongSessioninformationstrongrecorded">
<span class="glyphicon glyphicon-ok text-success"
aria-hidden="true"></span> <strong>Session information:</strong>
recorded </a>
</p>
</div>
<div id="strongSessioninformationstrongrecorded"
class="panel-collapse collapse">
<div class="panel-body">
<p>Great job! Recording the operating system, R version, and package
versions is critical for reproducibility.</p>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongCachestrongnone">
<span class="glyphicon glyphicon-ok text-success"
aria-hidden="true"></span> <strong>Cache:</strong> none </a>
</p>
</div>
<div id="strongCachestrongnone" class="panel-collapse collapse">
<div class="panel-body">
<p>Nice! There were no cached chunks for this analysis, so you can be
confident that you successfully produced the results during this
run.</p>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongFilepathsstrongrelative">
<span class="glyphicon glyphicon-ok text-success"
aria-hidden="true"></span> <strong>File paths:</strong> relative </a>
</p>
</div>
<div id="strongFilepathsstrongrelative" class="panel-collapse collapse">
<div class="panel-body">
<p>Great job! Using relative paths to the files within your workflowr
project makes it easier to run your code on other machines.</p>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<p class="panel-title">
<a data-toggle="collapse" data-parent="#workflowr-checks" href="#strongRepositoryversionstrongahrefhttpsgithubcomzhengli09BASSanalysistree6a631f82816b7be00b249f66a2288f7a3bd35adftargetblank6a631f8a">
<span class="glyphicon glyphicon-ok text-success"
aria-hidden="true"></span> <strong>Repository version:</strong>
<a href="https://github.com/zhengli09//BASS-analysis/tree/6a631f82816b7be00b249f66a2288f7a3bd35adf" target="_blank">6a631f8</a>
</a>
</p>
</div>
<div
id="strongRepositoryversionstrongahrefhttpsgithubcomzhengli09BASSanalysistree6a631f82816b7be00b249f66a2288f7a3bd35adftargetblank6a631f8a"
class="panel-collapse collapse">
<div class="panel-body">
<p>
Great! You are using Git for version control. Tracking code development
and connecting the code version to the results is critical for
reproducibility.
</p>
<p>
The results in this page were generated with repository version
<a href="https://github.com/zhengli09//BASS-analysis/tree/6a631f82816b7be00b249f66a2288f7a3bd35adf" target="_blank">6a631f8</a>.
See the <em>Past versions</em> tab to see a history of the changes made
to the R Markdown and HTML files.
</p>
<p>
Note that you need to be careful to ensure that all relevant files for
the analysis have been committed to Git prior to generating the results
(you can use <code>wflow_publish</code> or
<code>wflow_git_commit</code>). workflowr only checks the R Markdown
file, but you know if there are other scripts or data files that it
depends on. Below is the status of the Git repository when the results
were generated:
</p>
<pre><code>
Untracked files:
    Untracked:  code/run_giniclust3.py

Unstaged changes:
    Modified:   code/simu_utils.R
    Modified:   code/viz.R
    Modified:   data/MERFISH_Animal1.RData
    Modified:   data/starmap_mpfc.RData

</code></pre>
<p>
Note that any generated files, e.g. HTML, png, CSS, etc., are not
included in this status report because it is ok for generated content to
have uncommitted changes.
</p>
</div>
</div>
</div>
</div>
<hr>
</div>
<div id="versions" class="tab-pane fade">

<p>
These are the previous versions of the repository in which changes were
made to the R Markdown (<code>analysis/index.Rmd</code>) and HTML
(<code>docs/index.html</code>) files. If you’ve configured a remote Git
repository (see <code>?wflow_git_remote</code>), click on the hyperlinks
in the table below to view the files as they were in that past version.
</p>
<div class="table-responsive">
<table class="table table-condensed table-hover">
<thead>
<tr>
<th>
File
</th>
<th>
Version
</th>
<th>
Author
</th>
<th>
Date
</th>
<th>
Message
</th>
</tr>
</thead>
<tbody>
<tr>
<td>
Rmd
</td>
<td>
<a href="https://github.com/zhengli09//BASS-analysis/blob/6a631f82816b7be00b249f66a2288f7a3bd35adf/analysis/index.Rmd" target="_blank">6a631f8</a>
</td>
<td>
zhengli09
</td>
<td>
2022-06-07
</td>
<td>
Update software introduction and tutorial
</td>
</tr>
<tr>
<td>
html
</td>
<td>
<a href="https://rawcdn.githack.com/zhengli09//BASS-analysis/345228b446ca2cd0eb8ece1f6a832e9cf41b3958/docs/index.html" target="_blank">345228b</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-27
</td>
<td>
Build site.
</td>
</tr>
<tr>
<td>
Rmd
</td>
<td>
<a href="https://github.com/zhengli09//BASS-analysis/blob/9713c56c5fa59ac9a05dec6997a2af3bbb1d0da8/analysis/index.Rmd" target="_blank">9713c56</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-27
</td>
<td>
Link workflow figure to introduction page
</td>
</tr>
<tr>
<td>
html
</td>
<td>
<a href="https://rawcdn.githack.com/zhengli09//BASS-analysis/9a685114f1f29bb007c27088adaf8ce2582c56a2/docs/index.html" target="_blank">9a68511</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-27
</td>
<td>
Build site.
</td>
</tr>
<tr>
<td>
Rmd
</td>
<td>
<a href="https://github.com/zhengli09//BASS-analysis/blob/4ec8df1262087c7c78f682e56014a7087a756d4f/analysis/index.Rmd" target="_blank">4ec8df1</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-27
</td>
<td>
Publish the introduction, simulation analysis and STARmap analysis
</td>
</tr>
<tr>
<td>
html
</td>
<td>
<a href="https://rawcdn.githack.com/zhengli09//BASS-analysis/b2c476b7c59342294dc8304cd5d2f19213f27d43/docs/index.html" target="_blank">b2c476b</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-06
</td>
<td>
Build site.
</td>
</tr>
<tr>
<td>
html
</td>
<td>
<a href="https://rawcdn.githack.com/zhengli09//BASS-analysis/a6097f45ea3c63efeecda29c8c9305498aed39ee/docs/index.html" target="_blank">a6097f4</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-06
</td>
<td>
Build site.
</td>
</tr>
<tr>
<td>
Rmd
</td>
<td>
<a href="https://github.com/zhengli09//BASS-analysis/blob/9f8756a61ff477ed278dcfb8b2682e6c07fac36b/analysis/index.Rmd" target="_blank">9f8756a</a>
</td>
<td>
zhengli09
</td>
<td>
2022-02-06
</td>
<td>
Start workflowr project.
</td>
</tr>
</tbody>
</table>
</div>
<hr>
</div>
</div>
</div>
<div id="welcome-to-the-bass-website" class="section level1">
<h1>Welcome to the BASS website!</h1>
<p>This website maintains code for reproducing simulation and real data
application results described in the upcoming paper. For the software,
please refer to <a
href="https://github.com/zhengli09/BASS">BASS</a>.</p>
</div>
<div id="introduction-to-bass" class="section level1">
<h1>Introduction to BASS</h1>
<p>BASS is a method for multi-scale and multi-sample analysis in spatial
transcriptomics. BASS performs multi-scale transcriptomic analyses in
the form of joint cell type clustering and spatial domain detection,
with the two analytic tasks carried out simultaneously within a Bayesian
hierarchical modeling framework. For both analyses, BASS properly
accounts for the spatial correlation structure and seamlessly integrates
gene expression information with spatial localization information to
improve their performance. In addition, BASS is capable of multi-sample
analysis that jointly models multiple tissue sections/samples,
facilitating the integration of spatial transcriptomic data across
tissue samples.</p>
<div id="bass-workflow" class="section level2">
<h2>BASS workflow</h2>
<p><img src="BASS_workflow.png" /></p>
</div>
<div id="bass-model-overview" class="section level2">
<h2>BASS Model overview</h2>
<p>BASS relies on a Bayesian hierarchical modeling framework that
describes the relationship among gene expression features, cell type
labels, spatial domain labels, cell type compositions in each spatial
domain, and neighborhood graphs in a hierarchical fashion: <span
class="math display">\[
  \boldsymbol{x}_i^{(l)} | c_i^{(l)} = c \sim MVN(\boldsymbol{\mu}_c,
\boldsymbol{\Sigma})
\]</span> <span class="math display">\[
  c_i^{(l)} | z_i^{(l)} = r \sim Cat(\boldsymbol{\pi}_r)
\]</span> <span class="math display">\[
  \boldsymbol{z}^{(l)} \sim Potts(V^{(l)}, \beta)
\]</span> Above, the first equation models the expression feature of the
<span class="math inline">\(i\)</span>th cell on section <span
class="math inline">\(l\)</span>, <span
class="math inline">\(\boldsymbol{x}_i^{(l)}\)</span>, as depending on
its cell type label <span class="math inline">\(c_i^{(l)}\)</span> with
a multivariate normal distribution parameterized by a cell type-specific
mean parameter <span class="math inline">\(\boldsymbol{\mu}_c\)</span>
and a variance-covariance matrix <span
class="math inline">\(\boldsymbol{\Sigma}\)</span> that is shared across
cell types. The second equation models the probability of the <span
class="math inline">\(i\)</span>th cell belonging to the cell type <span
class="math inline">\(c\)</span> as depending on the underlying spatial
domain with a categorical distribution parameterized by the <span
class="math inline">\(r\)</span> domain-specific cell type composition
vector <span class="math inline">\(\boldsymbol{\pi}_r\)</span>. The
third equation models the spatial domain label of all cells on the
section <span class="math inline">\(l\)</span>, <span
class="math inline">\(\boldsymbol{z}^{(l)}\)</span>, as a function of
the neighborhood graph <span class="math inline">\(V^{(l)}\)</span>
through a homogeneous Potts model characterized by an interaction
parameter <span class="math inline">\(\beta\)</span>.</p>
<br>
<p>
<button type="button" class="btn btn-default btn-workflowr btn-workflowr-sessioninfo" data-toggle="collapse" data-target="#workflowr-sessioninfo" style="display: block;">
<span class="glyphicon glyphicon-wrench" aria-hidden="true"></span>
Session information
</button>
</p>
<div id="workflowr-sessioninfo" class="collapse">
<pre class="r"><code>sessionInfo()</code></pre>
<pre><code>R version 4.2.0 (2022-04-22)
Platform: x86_64-pc-linux-gnu (64-bit)
Running under: Ubuntu 18.04.5 LTS

Matrix products: default
BLAS:   /usr/lib/x86_64-linux-gnu/openblas/libblas.so.3
LAPACK: /usr/lib/x86_64-linux-gnu/libopenblasp-r0.2.20.so

locale:
 [1] LC_CTYPE=en_US.UTF-8       LC_NUMERIC=C              
 [3] LC_TIME=en_US.UTF-8        LC_COLLATE=en_US.UTF-8    
 [5] LC_MONETARY=en_US.UTF-8    LC_MESSAGES=en_US.UTF-8   
 [7] LC_PAPER=en_US.UTF-8       LC_NAME=C                 
 [9] LC_ADDRESS=C               LC_TELEPHONE=C            
[11] LC_MEASUREMENT=en_US.UTF-8 LC_IDENTIFICATION=C       

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
[1] workflowr_1.7.0

loaded via a namespace (and not attached):
 [1] Rcpp_1.0.8.3     bslib_0.3.1      compiler_4.2.0   pillar_1.7.0    
 [5] later_1.1.0.1    git2r_0.28.0     jquerylib_0.1.4  tools_4.2.0     
 [9] getPass_0.2-2    digest_0.6.29    jsonlite_1.8.0   evaluate_0.15   
[13] tibble_3.1.6     lifecycle_1.0.1  pkgconfig_2.0.3  rlang_1.0.1     
[17] cli_3.2.0        rstudioapi_0.13  yaml_2.3.5       xfun_0.29       
[21] fastmap_1.1.0    httr_1.4.2       stringr_1.4.0    knitr_1.37      
[25] sass_0.4.1       fs_1.5.2         vctrs_0.3.8      rprojroot_2.0.2 
[29] glue_1.6.2       R6_2.5.1         processx_3.5.2   fansi_1.0.2     
[33] rmarkdown_2.12.1 callr_3.7.0      magrittr_2.0.2   whisker_0.4     
[37] ps_1.6.0         promises_1.1.1   htmltools_0.5.2  ellipsis_0.3.2  
[41] httpuv_1.5.4     utf8_1.2.2       stringi_1.7.6    crayon_1.5.0    </code></pre>
</div>
</div>
</div>


<!-- Adjust MathJax settings so that all math formulae are shown using
TeX fonts only; see
https://docs.mathjax.org/en/latest/web/configuration.html. This will make
the presentation more consistent at the cost of the webpage sometimes
taking slightly longer to load. Note that this only works because the
footer is added to webpages before the MathJax javascript. -->
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    "HTML-CSS": { availableFonts: ["TeX"] }
  });
</script>




</div>
</div>

</div>

<script>

// add bootstrap table styles to pandoc tables
function bootstrapStylePandocTables() {
  $('tr.odd').parent('tbody').parent('table').addClass('table table-condensed');
}
$(document).ready(function () {
  bootstrapStylePandocTables();
});


</script>

<!-- tabsets -->

<script>
$(document).ready(function () {
  window.buildTabsets("TOC");
});

$(document).ready(function () {
  $('.tabset-dropdown > .nav-tabs > li').click(function () {
    $(this).parent().toggleClass('nav-tabs-open');
  });
});
</script>

<!-- code folding -->

<script>
$(document).ready(function ()  {

    // temporarily add toc-ignore selector to headers for the consistency with Pandoc
    $('.unlisted.unnumbered').addClass('toc-ignore')

    // move toc-ignore selectors from section div to header
    $('div.section.toc-ignore')
        .removeClass('toc-ignore')
        .children('h1,h2,h3,h4,h5').addClass('toc-ignore');

    // establish options
    var options = {
      selectors: "h1,h2,h3",
      theme: "bootstrap3",
      context: '.toc-content',
      hashGenerator: function (text) {
        return text.replace(/[.\\/?&!#<>]/g, '').replace(/\s/g, '_');
      },
      ignoreSelector: ".toc-ignore",
      scrollTo: 0
    };
    options.showAndHide = true;
    options.smoothScroll = true;

    // tocify
    var toc = $("#TOC").tocify(options).data("toc-tocify");
});
</script>

<!-- dynamically load mathjax for compatibility with self-contained -->
<script>
  (function () {
    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src  = "https://mathjax.rstudio.com/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML";
    document.getElementsByTagName("head")[0].appendChild(script);
  })();
</script>

</body>
</html>
