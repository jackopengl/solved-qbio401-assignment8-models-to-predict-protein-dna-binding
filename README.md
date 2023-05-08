Download Link: https://assignmentchef.com/product/solved-qbio401-assignment8-models-to-predict-protein-dna-binding
<br>
We are going to build models to predict protein–DNA binding based on the data obtained from highthroughput <em>in vitro</em> protein–DNA binding assays.

Download and install the following packages from Jupyter Notebook or other platforms:

<ol>

 <li>Bioconductor (refer the instructions on <a href="https://www.bioconductor.org/install/">https://www.bioconductor.org/install/</a><a href="https://www.bioconductor.org/install/">)</a></li>

 <li>The DNA shape prediction tool: DNAshapeR ( refer the instructions on <a href="https://www.bioconductor.org/packages/release/bioc/html/DNAshapeR.html">https://www.bioconductor.org/packages/release/bioc/html/DNAshapeR.html</a><a href="https://www.bioconductor.org/packages/release/bioc/html/DNAshapeR.html">)</a></li>

 <li>The machine learning tool: caret (refer the instructions on <a href="https://github.com/topepo/caret">https://github.com/topepo/caret</a><a href="https://github.com/topepo/caret">)</a></li>

</ol>

Complete the following tasks:

<ol>

 <li>Use the DNAshapeR package to predict DNA shape for each sequence bound by transcription factor <em>Mad, Max and Myc</em>. The datasets were obtained from the <em>in vitro</em> gcPBM (genomic context protein binding microarray) assay. The sequence data in FASTA format (Mad.fa, Max.fa and Myc.fa) can be found on Blackboard. Use plotShape() or heatShape() functions of DNAshapeR to generate ensemble plots for the DNA shape parameters of minor groove width (MGW), propeller twist (ProT), Roll, and helix twist (HelT). Discuss what you find from the results [2pt].</li>

 <li>Write an R function that takes as input a FASTA file. The function returns a feature matrix for “1mer” sequence model using one-hot encoding which is a way to represent categorical data as binary vector [3pt].</li>

</ol>

For DNA, we have four categories A, T, G, and C. Thus a one hot code for DNA is: A: [0,0,0,1]

C: [0,0,1,0]

G: [0,1,0,0]

T: [1,0,0,0]




For example, for the sequence AATTC, the 1-mer one-hot encoding is:

[0,0,0,1,0,0,0,1,1,0,0,0,1,0,0,0,1,0,0,0]

<ol start="3">

 <li>Use the function from Q#2 to generate a “1-mer” feature vector and combine the shape features generated from Q#1 for “1-mer+shape” model with respect to the datasets of <em>Mad</em>, <em>Max</em> and <em>Myc</em>. Use the caret package to build L2-regularized MLR models for “1-mer” and “1mer+shape” features with 10-fold cross validation (set the L2 <em>lambda</em> value between 2<sup>-15</sup> to 2<sup>15</sup>), and print out the average R2 (coefficient of determination) for these two models with respect to</li>

</ol>

the datasets of <em>Mad</em>, <em>Max</em> and <em>Myc</em>. The corresponding protein–DNA binding affinities can be found in corresponding *.s files. Compare the performance between “1-mer” sequence model and “1-mer+shape” model and explain what you find [3pt].