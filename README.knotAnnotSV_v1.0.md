# **knotAnnotSV Manual**

![](RackMultipart20201209-4-1ub5q1o_html_943cbbcf632b6f76.gif)

**Version 1.0**

[https://github.com/mobidic/knotAnnotSV](https://github.com/mobidic/knotAnnotSV)

Copyright (C) 2020-present GUIGNARD Thomas

Please feel free to contact me for any suggestions or bug reports

email: t-guignard@chu-montpellier.fr

TABLE OF CONTENTS

[1.INTRODUCTION 3](#_Toc56172170)

[2.REQUIREMENTS / INSTALLATION 3](#_Toc56172171)

[a) Requirements 3](#_Toc56172172)

[b) Installation 3](#_Toc56172173)

[3.INPUT 3](#_Toc56172174)

[a) Input files 3](#_Toc56172175)

[b) Arguments 4](#_Toc56172176)

[4.OUTPUT 4](#_Toc56172177)

[a)Output html format 4](#_Toc56172178)

[b)Output file path(s) and name(s) 4](#_Toc56172179)

[c)Compact and expanded display modes 4](#_Toc56172180)

[d)Default order of the annotation lines 5](#_Toc56172181)

[e)Available functions 5](#_Toc56172182)

[f)&quot;Gene name&quot; color visualisation 5](#_Toc56172183)

[5.USAGE / OPTIONS 6](#_Toc56172184)

[6.Test 6](#_Toc56172185)

[7.FAQ 6](#_Toc56172186)


### INTRODUCTION

**knotAnnotSV** is a program designed to create a customizable html file from an [AnnotSV](https://lbgi.fr/AnnotSV)output file. This will allow to easily filter and explore each SV. Annotations can be directly displayed in the web browser or by mouse hovering (tooltip).

By default, the html generation is configured to optimize the analysis by clinicians and biologists. However, thanks to a configuration file, the user can:

- Customize the order, the choice, the name and the description of the annotation columns
- Choose to display the annotation directly or in a tooltip

Moreover, several functionalities (search, highlight, links to public databases…) are available to help the user.


## REQUIREMENTS / INSTALLATION


# Requirements

The knotAnnotSV program is written in the Perl language. Modern Unix systems have this scripting language already installed. knotAnnotSV requires the following 2 Perl libraries (available via [CPAN](https://www.cpan.org/)):

- YAML::XS
- Sort::Key::Natural

# Installation

Please use git to download the most recent development tree.

The sources can be cloned to any directory:

cd /path/to/install/

git clone https://github.com/mobidic/knotAnnotSV.git


## INPUT

# Input files

knotAnnotSV takes an AnnotSV output file (&#39;_file_&#39;.annotated.tsv) and a configuration file as inputs.

**Configuration file:**

knotAnnotSV uses an indented yaml file (e.g. config\_cyto.yaml) to configure the AnnotSV output file.Several default configuration files are already distributed with the installation:

config\_cyto.yaml

config\_AnnotSV.yaml

These configuration files are used by knotAnnotSV to:

• Define the POSITION (column ordering) of each field you want to display

• Define in COMMENTLIST which associated fields to display in tooltips (by mouse hovering)

• Define in RENAME which column name to display in the output

• Define in HEADERTIPS some information about the column you want to display in the header tooltips (by mouse hovering)

• Inactivate fields you are willing to use either with a starting &#39;#&#39; or &#39;POSITION: 0&#39; or by deleting the corresponding line

NOTE : use space instead of tab for indentation, tabs are not allowed

# Arguments

knotAnnotSV takes several arguments as input including options that are detailed in &quot;USAGE / OPTIONS&quot; section. The different arguments can be passed to the program using the command line.


## OUTPUT

# Output html format

Giving an AnnotSV tab-separated values file, an html file is created that can be displayed in a web browser.

**Browser compatibility:**

Firefox 83.0

Chrome 86.0.4240.75

Edge 83.0.478.54

IE 11

# Output file path(s) and name(s)

Two options (--outDir and --outPrefix) can be used to specify the output directory and/or file name.

By default, the html file is written in the current directory and named annotSV.html.

# Compact and expanded display modes

**AnnotSV context:**

A typical AnnotSV use would be to first look at the annotation and ranking of each SV as a whole (i.e. &quot;full&quot;) and then focus on the content of that SV by genes (i.e. &quot;split&quot;). This is possible thanks to the 2 types of lines provided by AnnotSV:

- An annotation on the **&quot;full&quot;** length of the SV. Every SV are reported, even those not covering any gene. This type of annotation gives an estimate of the SV itself.

- An annotation of the SV &quot; **split&quot;** by gene. This type of annotation gives an opportunity to focus on each gene overlapped by the SV. Thus, when a SV spans over several genes, the output will contain as many annotations lines as genes covered.

**Display modes in knotAnnotSV:**

Two display modes are available in the web browser:

- &quot;Compact&quot;: only the &quot;full&quot; AnnotSV lines are displayed
- &quot;Expanded&quot;: the &quot;full&quot; and &quot;split&quot; AnnotSV lines are displayed

**Useful:**

A double-click on a « full » line opens the associated « split » lines. The full lines are highlighted in light blue.

# Default order of the annotation lines

By default, the annotation lines are sorted from the most (e.g. 5) to the least (e.g. 1) pathogenic SV using the « AnnotSV ranking » values.

# Available functions

**Top of the HTML page:**

- Choose the number of lines to be displayed (50, 100 or all) in the upper left corner
- To search for a topic (gene name, phenotype…), just type a word or phrase in the Search box in the upper right corner

**Header:**

- Display the definition of the column name by mouse hovering (tooltip)
- Click small triangle in each column to sort the data
- Below each column name, a search box is available for:

- Searching words

- Filtering a range of numerical values (with the &quot;\&gt;&quot;, &quot;\&gt;=&quot;, &quot;\&lt;&quot; and &quot;\&lt;=&quot; symbols) and extracts matching records. The results are dynamically updated.

e.g. to select frequencies smaller than 1%, type &quot;\&lt;0.01&quot;

**Annotation lines:**

- Right click on an annotation line to highlight it (changes the color to yellow)
- Double-click on a « full » line to open the associated « split » lines
- Mouse hover each annotation to show complementary information (tooltip)
- Click on the « AnnotSV ID » to open the SV coordinates in the UCSC Genome browser (the SV region is highlighted in blue and zoomed out by 1.5)
- Click on the various links to access directly to the corresponding public database

**Footer:**

- Click to choose the desired display mode.

For more explanation, see the « Compact and expanded display modes » section.

**NOTE:**

To come back to the default annotation lines order, the user can click on the first column (AnnotSV ID).

# &quot;Gene name&quot; color visualisation

A sequential palettes of red is used to visualize for each gene its corresponding pLI. Darker colors means higher pLI values (e.g 1.0).

![](RackMultipart20201209-4-1ub5q1o_html_f875927e7d535f39.png)


## USAGE / OPTIONS

To run knotAnnotSV, the default command line is the following:

cd /path/to/install/knotAnnotSV

perl ./knotAnnotSV.pl --configFile config\_AnnotSV.yaml --annotSVfile file.annotated.tsv

The command line can be completed by some options.

To show the options simply type:

perl ./knotAnnotSV.pl

--configFile \&lt;YAML config file for customizing output\&gt;

--annotSVfile \&lt;AnnotSV annotated file\&gt;

--outDir \&lt;output directory (default = current dir)\&gt;

--outPrefix \&lt;output file prefix (default = &quot;&quot;)\&gt;

--genomeBuild \&lt;Genome Assembly reference (default = hg19)\&gt;

--datatableDir \&lt;Local Path to DataTables directory containing css and js files (default = &quot;&quot;, requires web connection)\&gt;


## Test

In order to validate the knotAnnotSV installation and to facilitate its use we have provided with the installation an input/output example in the « example » folder.

1. Change to the repo directory, and run the example

cd /path/to/install/knotAnnotSV/

perl ./knotAnnotSV.pl --annotSVfile ./example/example.annotated.tsv --configFile ./config\_AnnotSV.yaml

2. Display the html output on a web browser

3. Have fun with the exploring!


## FAQ

**Q: What does knotAnnotSV means ?**

If pronounced like « knot a knot SV », knotAnnotSV is a French-inspired word game meaning that this tool creates a link between the SV data to be analysed :o)

knotAnnotSV documentation v1.0 2020/11/13 9
