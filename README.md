# Introduction to Bioconductor annotation resources
![](https://github.com/jmacdon/Bioc2020Anno/workflows/.github/workflows/basic_checks.yaml/badge.svg)
# Instructors

* James W. MacDonald (jmacdon@uw.edu)
* Lori Shepherd (lori.shepherd@roswellpark.org)

# Workshop Description

There are various annotation packages provided by the Bioconductor
project that can be used to incorporate additional information to
results from high-throughput experiments. This can be as simple as
mapping Ensembl IDs to corresponding HUGO gene symbols, to much more
complex queries involving multiple data sources. In this workshop we
will cover the various classes of annotation packages, what they
contain, and how to use them efficiently. 

## Prerequisites

* Basic knowledge of R syntax
* Basic understanding of the various annotation sources (NCBI, EBI/EMBL)

Useful background reading

* The
  [AnnotationDbi](https://www.bioconductor.org/packages/release/bioc/vignettes/AnnotationDbi/inst/doc/IntroToAnnotationPackages.pdf)
  vignette.
* The
  [biomaRt](https://www.bioconductor.org/packages/release/bioc/vignettes/biomaRt/inst/doc/biomaRt.html)
  vignette.
* The
  [GenomicFeatures](https://www.bioconductor.org/packages/release/bioc/vignettes/GenomicFeatures/inst/doc/GenomicFeatures.pdf)
  vignette.

## Preparation

To be able to follow along with this workshop, we have created a
Docker installation that includes the devel version of R, and all
required Bioconductor packages. In order to access this, you need to
first install [Docker](https://docs.docker.com/engine/install/) on
your own computer. Once you have done that, you can then load the
Docker container for this workshop by starting Docker.

How you do this is dependent on your operating system.

### Windows

Hit the 'Windows' key (lower left on your keyboard, between Ctrl and
Alt), then type Docker. If Docker is installed you should see Docker
App highlighted - click Enter to start the App. It can take some time
to get started. You can see it's doing something by clicking on the
little caret (^) in the lower right of your screen - there should be a
little animated Docker icon which indicates it's starting. Once it is
started, open a CMD prompt by hitting the Windows key again and typing
cmd, then Enter. In the CMD prompt type

```
docker run -e PASSWORD=<choose_a_password_for_rstudio> -p 8787:8787 jmacdon/bioc2020anno
```

You can choose any password for rstudio - that's what you will use to
log in. It will take some time for the Docker to be downloaded and
started, so you might consider doing this ahead of time.

### Linux

For Linux, it depends on how you installed. If you used a package
installer then presumably Docker will be set to start
automatically. Otherwise you need to start the Docker daemon by hand
(or set it to start automatically). There are too many variables to
give much detailed information here; for those on Linux, the
assumption is that you probably know what you are doing and can figure
it out from the Docker install page.

To start the daemon, if neccessary, do

```
sudo dockerd &
## followed by 

sudo docker run hello-world

```

If Docker is installed correctly it should print something
informative. To get the Docker container, it's the same as for
Windows.

```
docker run -e PASSWORD=<choose_a_password_for_rstudio> -p 8787:8787 jmacdon/bioc2020anno
```

### MacOS

There is an installer for MacOS. As with Windows, follow the
instructions - it's just a regular drag'n'drop install. Once it's
installed and started, open a terminal prompt and as above type.

```
docker run -e PASSWORD=<choose_a_password_for_rstudio> -p 8787:8787 jmacdon/bioc2020anno
```

For all operating systems, once the Docker container is initialized,
you can access it by opening a browser and typing

```
http://localhost:8787
```

Which should present you with an RStudio login. Use rstudio as the
username and the password you used to start the Docker.


## Workshop Participation

After each type of annotation package is introduced, students will be
given the opportunity to practice making their own queries. 

## _R_ / _Bioconductor_ packages used

* AnnotationDbi
* AnnotationHub
* BSgenome
* biomaRt
* ensembldb
* org.Hs.eg.db
* TxDb.Hsapiens.UCSC.hg19.knownGene
* EnsDb.Hsapiens.v79
* EnsDb.Mmusculus.v79
* Homo.sapiens 
* BSgenome.Hsapiens.UCSC.hg19
* hugene20sttranscriptcluster.db


# Workshop goals and objectives

Annotating data is a complex task. For any high-throughput experiment
the analyst usually starts with a set of identifiers for each thing
that was measured, and in order to make the results useful to
collaborators these identifiers need to be mapped to other identifiers
that are either more familiar to collaborators, or that can be used
for further analyses. As an example, RNA-Seq data may only have Entrez
Gene IDs for each gene measured, and as part of the output you may
want to include the gene symbols, which are more likely to be familiar
to a Biologist.

## Learning goals

* Understand what sort of annotation data are available
* Understand the difference between annotation sources (NCBI and EBI/EMBL)
* Gain familiarity with the various ways to query annotation packages
* Get some practice making queries

## Learning objectives

* Be able to use select and mapIds to map between identifiers
* Be able to extract data from TxDb and EnsDb packages
* Be able to make queries using biomaRt
* Extract and utilize various data from AnnotationHub

