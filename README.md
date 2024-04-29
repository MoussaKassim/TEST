<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA - Knowledge Discovery by Accuracy Maximization</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
            <a class="navbar-brand" href="#">KODAMA</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ml-auto">
                    <li class="nav-item">
                        <a class="nav-link" href="#introduction">Introduction</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#installation">Installation</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#getting-started">Getting Started</a>
                    </li>
                    <!-- Add more navigation items here -->
                </ul>
            </div>
        </div>
    </nav>

    <div class="container mt-5">
        <section id="introduction">
            <h2>Introduction</h2>
            <p>KODAMA (Knowledge Discovery by Accuracy Maximization) is a novel learning algorithm for unsupervised feature extraction, specifically designed for analysing noisy and high-dimensional data sets (Cacciatore et al., 2014). The core idea of the original algorithm is to use an iteration procedure to produce a hypothetical classification through maximization of cross-validated predictive accuracy. Using only the data set as input (no a priori knowledge is needed), an iterative procedure permits classification with a high cross-validated accuracy. Two different classifiers are implemented in this package for the computation of cross-validated predictive accuracy: k-nearest neighbors (kNN) and Partial Least Squares - Discriminant Analysis (PLSDA). This procedure is repeated several times to average the effects owing to the randomness of the iterative procedure. After each run of the procedure, a classification vector with high cross-validated accuracy is obtained. KODAMA subsequently collects and processes these results by constructing a dissimilarity matrix to provide a holistic view of the data. This documentation introduces the usage of KODAMA.</p>
        </section>

        <section id="installation" class="mt-5">
            <h2>Installation</h2>
            <h3>Installation via CRAN</h3>
            <p>The R package KODAMA (current version 1.1) is part of the Comprehensive R Archive Network (CRAN). The simplest way to install the package is to enter the following command into your R session: <code>install.packages("KODAMA")</code>. We suggest to install the R package rgl for the data visualization in 3D interactive plots.</p>

            <h3>Manual installation from source</h3>
            <p>To compile the C/C++ code included in the package for customization or installation on alternative operating systems the package can be manually installed from source. To this end, open the package’s page at CRAN (Cacciatore et al., 2014) and then proceed as follows:</p>
            <ul>
                <li>Download KODAMA.tar.gz and save it to your hard disk</li>
                <li>Open a shell/terminal/command prompt window and change to the desired directory for installation of KODAMA.tar.gz. Enter <code>R CMD INSTALL KODAMA.tar.gz</code> to install the package. Note that this may require additional software on some platforms. Windows requires Rtools2 to be installed and to be available in the default search path (environment variable PATH). MAC OS X requires installation of Xcode developers and command line tools.</li>
            </ul>

            <h3>Compatibility issues</h3>
            <p>All versions downloadable from CRAN have been built using R version, R.3.2.3. The package should work without major issues on R versions > 3.0.0.</p>
        </section>

        <section id="getting-started" class="mt-5">
            <h2>Getting Started</h2>
            <p>To load the package, enter the following instruction in your R session:</p>
            <pre><code>library("KODAMA")</code></pre>
            <p>If this command terminates without any error messages, you can be sure that the package has been installed successfully. The KODAMA package is now ready for use. The package includes both a user manual (this document) and a reference manual (help pages for each function). To view the user manual, enter <code>vignette("KODAMA")</code>. Help pages can be viewed using the help command <code>help(package="KODAMA")</code>.</p>
        </section>
    </div>

    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.4/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</body>
</html>
