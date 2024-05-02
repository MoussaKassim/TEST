<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <style>
        /* Navbar Styles */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            background-color: #333;
            border-radius: 0; /* Rounded rectangle */
        }
        .navbar-nav .nav-link {
            color: white;
            transition: color 0.3s, background-color 0.3s; /* Transition for glowing effect */
        }
        .navbar-nav .nav-link:hover {
            color: #FFA500; /* Modern orangish color */
            background-color: rgba(255, 165, 0, 0.1); /* Orange background */
        }
        .navbar-brand {
            color: white;
            font-size: 24px;
        }
        /* Body padding to compensate for fixed navbar */
        body {
            padding-top: 56px; /* Height of the navbar */
            margin-left: 200px; /* Adjusted to accommodate the sidebar */
        }
        /* Sidebar Styles */
        #sidebar {
            position: fixed;
            top: 0;
            left: 0;
            bottom: 0;
            z-index: 1000;
            background-color: #333;
            width: 200px;
            padding-top: 56px; /* Height of the navbar */
            overflow-y: auto;
            transition: all 0.3s;
        }
        #sidebar ul {
            list-style-type: none;
            padding: 0;
        }
        #sidebar ul li {
            padding: 10px;
            color: white;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        #sidebar ul li:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }
        #content {
            margin-left: 200px; /* Adjusted to accommodate the sidebar */
            padding: 20px;
        }
        /* Section Styles */
        section {
            margin-top: 20px;
            padding: 20px;
            border-radius: 10px;
            background-color: #f9f9f9;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
        }
        section h1 {
            color: #007bff;
            margin-bottom: 20px;
        }
        /* Card Styles */
        .card {
            border: none;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            transition: transform 0.3s;
            cursor: pointer;
        }
        .card:hover {
            transform: translateY(-5px);
        }
        .card-body {
            text-align: center;
        }
        /* Code Styles */
        pre {
            background-color: #f8f9fa;
            border: 1px solid #dee2e6;
            border-radius: 5px;
            padding: 10px;
            overflow-x: auto;
            position: relative;
            cursor: pointer;
        }
        pre:hover::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 255, 0.1); /* Blue color when hovered */
            border-radius: 5px;
            z-index: 1;
        }
        pre:hover::before {
            content: "\f0ea"; /* FontAwesome copy icon */
            font-family: "Font Awesome 5 Free";
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 20px;
            color: #007bff;
            z-index: 2;
        }
        .copy-box {
            border: 1px solid #dee2e6;
            border-radius: 5px;
            padding: 10px;
            background-color: #f8f9fa;
            margin-top: 20px;
            cursor: pointer;
            display: inline-block;
            position: relative;
        }
        .copy-box:hover {
            background-color: #e9ecef;
        }
        .copy-box::before {
            content: "\f0c5"; /* FontAwesome copy icon */
            font-family: "Font Awesome 5 Free";
            position: absolute;
            top: 50%;
            left: 5px;
            transform: translateY(-50%);
            font-size: 18px;
            color: #007bff;
        }
    </style>
</head>
<body>

<!-- Navbar -->
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container">
        <a class="navbar-brand" href="#">KODAMA</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
                <li class="nav-item">
                    <a class="nav-link" href="#introduction">Introduction</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#news">News</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#installation">Installation</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#applications">Applications</a>
                </li>
            </ul>
            <ul class="navbar-nav">
                <li class="nav-item">
                    <a class="nav-link" href="https://github.com/tkcaccia/KODAMA">
                        <span class="fab fa-github"></span>
                        Source code
                    </a>
                </li>
            </ul>
        </div>
    </div>
</nav>

<!-- Sidebar -->
<div id="sidebar">
    <ul>
        <li id="introLink">Introduction</li>
        <li id="newsLink">News</li>
        <li id="installationLink">Installation</li>
        <li id="applicationsLink">Applications</li>
    </ul>
</div>

<!-- Introduction Section -->
<section id="introduction">
    <div class="container">
        <h1>Introduction</h1>
        <p>
            KODAMA is an unsupervised and semi-supervised learning algorithm designed for feature extraction from noisy and high-dimensional data.
        </p>
    </div>
</section>

<!-- News Section -->
<section id="news">
    <div class="container">
        <h2>News</h2>
        <p>
            KODAMA facilitates the identification of patterns representing underlying groups in a dataset. This is an improved version of the KODAMA algorithm for spatially-aware dimensionality reduction.
        </p>
        <p>
            The KODAMA package has been integrated with t-SNE and UMAP to convert the KODAMA's dissimilarity matrix into a low-dimensional space.
        </p>
        <p>
            Relevant articles:
            <ul>
                <li><a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9887019/">Zinga, M. M., et al. KODAMA exploratory analysis in metabolic phenotyping. Frontiers in Molecular Biosciences, 9.</a></li>
                <li><a href="https://academic.oup.com/bioinformatics/article/33/4/621/2667156?login=false">Cacciatore, S., et al. KODAMA: an R package for knowledge discovery and data mining. Bioinformatics, 33(4), 621-623.</a></li>
                <li><a href="https://www.pnas.org/doi/abs/10.1073/pnas.1220873111">Cacciatore, S., et al. Knowledge discovery by accuracy maximization. Proceedings of the National Academy of Sciences, 111(14), 5117-5122.</a></li>
            </ul>
        </p>
    </div>
</section>

<!-- Installation Section -->
<section id="installation">
    <div class="container">
        <h2>Installation</h2>
        <p>
            The KODAMA package is available on <a href="https://CRAN.R-project.org/package=KODAMA">CRAN</a>.
        </p>
        <pre><code style="color: blue;">
library(devtools)
install_github("tkcaccia/KODAMA")
        </code></pre>
    </div>
</section>

<!-- Applications Section -->
<section id="applications">
    <div class="container">
        <h2>Applications</h2>
        <div class="card-deck">
            <div class="card">
                <div class="card-body">
                    <h5 class="card-title">Metabolomic data</h5>
                    <p class="card-text">Explore Metabolomic data</p>
                </div>
            </div>
            <div class="card">
                <div class="card-body">
                    <h5 class="card-title">Single cell RNA seq data</h5>
                    <p class="card-text">Explore Single cell RNA seq data</p>
                </div>
            </div>
            <div class="card">
                <div class="card-body">
                    <h5 class="card-title">Spatial Transcriptomic data</h5>
                    <p class="card-text">Explore Spatial Transcriptomic data</p>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- Metabolomic Data Section -->
<section id="metabolomicData">
    <div class="container">
        <h2>Metabolomic Data</h2>
        <p>
            The data belong to a cohort of 22 healthy donors (11 male and 11 female) where each provided about 40 urine samples over the time course of approximately 2 months, for a total of 873 samples. Each sample was analysed by Nuclear Magnetic Resonance Spectroscopy. Each spectrum was divided in 450 spectral bins.
        </p>
        <h3>Tutorial</h3>
        <p>
            Here, we load the MetRef dataset. Columns with only zero values are removed. 
        </p>
        <pre><code data-lang="R">
data(MetRef)
u=MetRef$data
u=u[,-which(colSums(u)==0)]
        </code></pre>
        <p>
            We apply the Probabilistic Quotient Normalization
        </p>
        <pre><code data-lang="R">
u=normalization(u)$newXtrain
        </code></pre>
        <p>
            We mean-center and univariate scaling the data set.
        </p>
        <pre><code data-lang="R">
u=scaling(u)$newXtrain
        </code></pre>
        <p>
            Two classification vectors are created
        </p>
        <pre><code data-lang="R">
class=as.numeric(as.factor(MetRef$gender))
class2=as.numeric(as.factor(MetRef$donor))
        </code></pre>
        <p>
            Different algorithms for dimensionality reduction are applied
        </p>
        <pre><code data-lang="R">
res_MDS=cmdscale(dist(u))
res_tSNE=Rtsne(u)$Y
res_UMAP = umap(u)$layout
        </code></pre>
        <p>
            We apply KODAMA with Partial Least Square Discriminant Analysis (PLS-DA) as a classifier with 50 components to drive the accuracy maximization. The KODAMA dissimilarity matrix's is converted into a low-dimensional space using three different methods (i.e., MDS, t-SNE, and UMAP).
        </p>
        <pre><code data-lang="R">
kk=KODAMA.matrix(u,f.par = 50)
res_KODAMA_MDS=KODAMA.visualization(kk,method = "MDS")
res_KODAMA_tSNE=KODAMA.visualization(kk,method = "t-SNE")
res_KODAMA_UMAP=KODAMA.visualization(kk,method = "UMAP")
        </code></pre>
        <p>
            Visualize the different clustering algorithms:
        </p>
        <p>
            a) labelled by the gender
        </p>
        <pre><code data-lang="R">
par(mfrow = c(2,3))
plot(res_MDS,pch=21,bg=rainbow(2)[class],main="MDS")
plot(res_tSNE,pch=21,bg=rainbow(2)[class],main="tSNE")
plot(res_UMAP,pch=21,bg=rainbow(2)[class],main="UMAP")
plot(res_KODAMA_MDS,pch=21,bg=rainbow(2)[class],main="KODAMA_MDS",)
plot(res_KODAMA_tSNE,pch=21,bg=rainbow(2)[class],main="KODAMA_tSNE")
plot(res_KODAMA_UMAP,pch=21,bg=rainbow(2)[class],main="KODAMA_UMAP")
        </code></pre>
        <p>
            <img src="https://github.com/tkcaccia/KODAMA/blob/main/figures/metabolites.gender.png" alt="Gender" />
        </p>
        <p>
            b) labelled by the donor
        </p>
        <pre><code data-lang="R">
plot(res_MDS,pch=21,bg=rainbow(22)[class2],main="MDS")
plot(res_tSNE,pch=21,bg=rainbow(22)[class2],main="tSNE")
plot(res_UMAP,pch=21,bg=rainbow(22)[class2],main="UMAP")
plot(res_KODAMA_MDS,pch=21,bg=rainbow(22)[class2],main="KODAMA_MDS",)
plot(res_KODAMA_tSNE,pch=21,bg=rainbow(22)[class2],main="KODAMA_tSNE")
plot(res_KODAMA_UMAP,pch=21,bg=rainbow(22)[class2],main="KODAMA_UMAP")
        </code></pre>
        <p>
            <img src="https://github.com/tkcaccia/KODAMA/blob/main/figures/metabolites.donor.png" alt="Donor" />
        </p>
    </div>
</section>

<!-- Bootstrap Scripts -->
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.3/dist/umd/popper.min.js"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

<!-- JavaScript for Smooth Scrolling and Active Navigation -->
<script>
    // Smooth scrolling for sidebar links
    document.getElementById('introLink').addEventListener('click', function() {
        document.getElementById('introduction').scrollIntoView({ behavior: 'smooth' });
    });
    document.getElementById('newsLink').addEventListener('click', function() {
        document.getElementById('news').scrollIntoView({ behavior: 'smooth' });
    });
    document.getElementById('installationLink').addEventListener('click', function() {
        document.getElementById('installation').scrollIntoView({ behavior: 'smooth' });
    });
    document.getElementById('applicationsLink').addEventListener('click', function() {
        document.getElementById('applications').scrollIntoView({ behavior: 'smooth' });
    });
</script>

</body>
</html>
