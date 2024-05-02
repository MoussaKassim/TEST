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
                    <a class="nav-link" href="#software-tutorial">Software Tutorial</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#simulation">Simulation</a>
                </li>
                <li class="nav-item dropdown">
                    <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                        Data Analyses
                    </a>
                    <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                        <a class="dropdown-item" href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Metabolomics_data.md">Metabolomic data</a>
                        <a class="dropdown-item" href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Single_cell_RNA_seq.md">Single cell RNA seq data</a>
                        <a class="dropdown-item" href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Spatial%20_transcriptomic.md">Spatial Transcriptomic data</a>
                    </div>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="https://github.com/tkcaccia/KODAMA">
                        <span class="fab fa-github"></span>
                        Source code
                    </a>
                </li>
                <!-- Nouveau lien pour afficher la section Metabolomic Data -->
                <li class="nav-item">
                    <a class="nav-link" href="#metabolomic-data" onclick="toggleSection('metabolomic-data')">Metabolomic Data</a>
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
            # KODAMA An unsupervised and semi-supervised learning algorithm to perform feature extraction from noisy and high-dimensional data
        </p>
    </div>
</section>

<!-- News Section -->
<section>
    <div class="container">
        <h2>News</h2>
        <p>
            <!-- Contenu de la section News -->
        </p>
    </div>
</section>

<!-- Installation Section -->
<section>
    <div class="container">
        <h2>Installation</h2>
        <p>
            <!-- Contenu de la section Installation -->
        </p>
    </div>
</section>

<!-- Applications Section -->
<section>
    <div class="container">
        <h2>Applications</h2>
        <p>
            <!-- Contenu de la section Applications -->
        </p>
    </div>
</section>

<!-- Section pour Metabolomic Data -->
<section id="metabolomic-data" style="display: none;">
    <div class="container">
        <h2>Metabolomic data</h2>
        <p>
            The data belong to a cohort of 22 healthy donors (11 male and 11 female) where each provided about 40 urine samples over the time course of approximately 2 months, for a total of 873 samples. Each sample was analysed by Nuclear Magnetic Resonance Spectroscopy. Each spectrum was divided in 450 spectral bins.
        </p>
        <!-- Tutoriel et autres contenus de la section Metabolomic Data -->
    </div>
</section>

<!-- Bootstrap Scripts -->
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.3/dist/umd/popper.min.js"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

<!-- JavaScript pour afficher ou masquer la section Metabolomic Data -->
<script>
    function toggleSection(sectionId) {
        var section = document.getElementById(sectionId);
        if (section.style.display === "none") {
            section.style.display = "block";
        } else {
            section.style.display = "none";
        }
    }
</script>

</body>
</html>
