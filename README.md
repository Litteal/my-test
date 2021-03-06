# HiseqWGS_2017 (Test version)
[![Packagist](https://img.shields.io/packagist/l/doctrine/orm.svg)](https://github.com/Litteal/HiseqWGS_2017.beta/blob/master/LICENSE "OVERVIEW MIT license")
[![Packagist](https://img.shields.io/badge/Python-2.7-brightgreen.svg)](https://www.python.org/downloads/ "click to downlocad page")
[![Packagist](https://img.shields.io/badge/GATK-3.6-brightgreen.svg)](https://software.broadinstitute.org/gatk/download/archive "click to download page")
[![Packagist](https://img.shields.io/badge/GNU-%3C%205.0-brightgreen.svg)]()
[![Packagist](https://img.shields.io/badge/Java-7%2C8-brightgreen.svg)](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
[![Packagist](https://img.shields.io/badge/Root-v5.34.20-blue.svg)](https://root.cern.ch/releases "click to download page")
[![Packagist](https://img.shields.io/badge/pysam-%3E%200.8.4-blue.svg)]()
[![Packagist](https://img.shields.io/badge/Version-beta-orange.svg)]()
<br>

A WGS pipeline constructed by multiple tools. Meant to  produce shell scripts for analysis the whole genome sequencing data based on provided parameters.<br>

Whole pipeline : raw data -> filter -> align -> correct bam -> call SNPs and indels -> call SVs -> call SNVs <br>

* __Author__: Songjing <br>
* __E-mail__: kakaluote707@sina.com<br>
* __Edit__: 14 Mar,2017<br>

## Overview <br>
This pipeline contains germline variants calling as well as somatic variants calling.You can just use few parameters then it can procedure all shell scripts to run each step.
![](https://github.com/Litteal/HiseqWGS_2017.beta/blob/master/etc/WGS%20analysis%20pipeline.png)

## Usage <br>

#### For single/multiple sample(s):
	 perl HiseqWGS_2017.pl -c HiseqWGS_2017.conf -f rawData.list -A -V -S
#### For tumor/normal pair(s) samples:
	 perl HiseqWGS_2017.pl -c HiseqWGS_2017.conf -f rawData.list -A -z

##### options: <br>
        -c:*    STR     configure file,including the path of tools used.(eg:HiseqWGS_2017.conf)(required)
        -f:*    STR     sample fastq list(required)
        -R:     STR     read group header line such as "\@RG\\tID:id\\tPL:[illumina]\\tPU:$platform_unit\\tSM:samplename\\tLB:lib"[Default: Auto]
        -m:     STR	memory to use [Default:12 (Gb)]
        -p:     Boolens first fastq file consists of interleaved paired-end sequences[Default: False]
        -t:     INT     number of threads to use [default:16]
        -o:     STR     output dir prefix  [Defalut:'./outdir_\$date']
        -tmp:   STR     TMP dir prefix     [Default:'./TMP_\$date']

        -A:*    Boolens Call align(align+markdup+sort+index) [Default:False]
        -V:*    Boolens Call var  (calling SNP,indels)       [Default:False]
        -S:*    Boolens Call sv   (calling sv,CNV)           [Default:False]

        -trio:  Boolens Necessary if your samples came from a family(eg:child,father and mother)[Defalut: False]
        -z:     Boolens Necessary if your samples are tumor/normal pairs[Default: False]

        -help|?:        show this usage page
        -more:          more default information


## Prerequisites<br>
* GNU gcc =4.7 ~ 5.0 , (gcc 4.8.4 used here)
* g++
* python 2.7
   	* pysam 0.8.4 or newer(0.9.1 used here)
	*	numpy (0.12.1 used here)
	*	scipy 
* automake make cmake git libncurses5-dev zlib1g-dev g++ gcc gfortran
*	python2.7-dev 
*	python-pip 
*	libblas-doc libblas3 libblas-dev
*	liblapack3 liblapack-dev
*	zlib-1.2.11
*	libX11-dev libxpm-dev libxft-dev libxext-dev dpkg-dev binutils
*	libssl-dev libpcre3-dev xlibmesa-glu-dev libglew1.5-dev libftgl-dev libmysqlclient-dev libfftw3-dev libcfitsio3-dev 
*	graphviz-dev libavahi-compat-libdnssd-dev libldap2-dev 
*	python-dev libxml2-dev libkrb5-dev libgsl0-dev libqt4-dev
*	root(v5.34.20)
*	samtools(1.3.1)
*	bwa_mem(0.7.12)
*	java 8 java 7
*	picard-tools(1.54)
*	Speedseq(v0.1.2)
*	Conpair (master version now)
*	CREST
*	muTect-1.1.5
*	GATK (3.6)
*	SOAPnuke*(no need if can't get)
*	fastQC
*	Oncotator*
*	VEP*
*	GISTIC*
## installation<br>
##### You can use existed script `install_HiseqWGS_2017.pl` to install all the environment exclude reference data.<br>
	perl < path to install_HiseqWGS_2017.pl> /etc/install_HiseqWGS_2017.pl [-o] < OUT_PATH >
## Other Required data 
* Please note,the reference version and corresponding truth set we used here was GRCh37(hg19) or b37 genome(from 1000G project),it probably will to support GRCh38(hg38) in the future, and these data you can download from GATK Resource bundle [ftp://ftp.broadinstitute.org/bundle/hg19/](ftp://ftp.broadinstitute.org/bundle/hg19/) ,note that need a account of GATK web page to log in. Or archive it from my cloud bucket().
	
