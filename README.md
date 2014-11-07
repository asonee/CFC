##################################################################################################################################################
##
## A Small User Guide for Class-Feature-Centroid (CFC)
##           Hu Guan, Jingyu Zhou, Minyi Guo
##                    Feb 3, 2009, V1.1
##
## Copyright (c) <2009>.
## All rights reserved.
##
## Redistribution and use in source and binary forms, with or without
## modification, are permitted provided that the following conditions are met:
##     * Redistributions of source code must retain the above copyright
##       notice, this list of conditions and the following disclaimer.
##     * Redistributions in binary form must reproduce the above copyright
##       notice, this list of conditions and the following disclaimer in the
##       documentation and/or other materials provided with the distribution.
##     * Neither the name of the Shanghai Jiao Tong University nor the
##       names of its contributors may be used to endorse or promote products
##       derived from this software without specific prior written permission.
##
## THIS SOFTWARE IS PROVIDED BY AUTHORS ''AS IS'' AND ANY
## EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
## WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
## DISCLAIMED. IN NO EVENT SHALL AUTHORS BE LIABLE FOR ANY
## DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
## (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
## SERVICES;
## LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
## ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
## (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF
## THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
##
##################################################################################################################################################

0 Prerequisites: a working Java Run Time Environment >= 1.6.0
  We have successfully tested on Java version 1.6.0 and 1.7.0.
  Note: it's known not working for Java 1.5.0.

1 Download the cfc.zip file;

2 Unzip cfc.zip file to a folder;

3 Keep the folder structure:
	## working folders
	cfc                          ## current working folder
	cfc\20_newsgroup             ## 20-newsgroup corpus, obtained from http://kdd.ics.uci.edu/databases/20newsgroups
	cfc\out                      ## directory for output results
	cfc\conf                     ## config file's folder
	## executable jar file
	20-parser-sjtu.jar           ## parsing 20-newsgroup corpus into a series of files
	cfc-sjtu.jar                 ## getting the testing result in this corpus
	## help file
	readme.txt
	
4 Change to directory "cfc" in command line mode;

5 Run 20-parser-sjtu.jar file with this command:
	java -jar 20-parser-sjtu.jar

	This command would help you to parse 20-newsgroup corpus and get some important statistic information.
	
	You should get some running information such as:
	"finish in getting category and file information ..."
	"finish in coping No-1 class: alt.atheism"
	
	If you can not get those running information, you'd better assure your java's running environment.	
	
6 Run cfc-sjtu.jar file with this command:
	java -jar cfc-sjtu.jar
	
	This command produce the testing results for the 20-newsgroup corpus.
	
7 Read the result from "out" folder

	20-all_idf.txt            ## total IDF(Inversed Document Frequency) statistic information
	20-inner_df.txt           ## total inner-class distribution information
				  ## each line represents a category
	20-inter_df.txt           ## inter-class distribution information
				  ## similar to document frequency among the categories
	
	20-newsgroup.txt          ## total term frequency information in 20-newsgroup
	20-newsgroup_vector.txt   ## total TF-IDF scores for every document
	
	categorizeslist.txt       ## category name

	cfc_test_sim.txt          ## 6635 texts' testing information using CFC's classification method.
				  ## Each line represents the similarity
				  ## scores between a document and 20 categories
				  ## (normalized by the maximum value of each line).
				  ## For the whole corpus (from 0 to the maximum), testing documents are those:
				  ##          (document index) mod 3 == 0

	cfc_train_sim.txt         ## training texts' result for CFC's classification
				  ## similar to cfc_test_sim.txt
	
	test_cfc_stat_result.txt  ## testing result's statistic information, for each category,
	                          ## the format is: 
	                          ## Number of Documents, True Positive, False Negative, False Positive
	
8 Introduction to CFC
	CFC is a centroid-based classifier for multi-class text categorization.
It is built from two important class features: inter-class term
distribution and inner-class term distribution.

	Note:
	In 20-inner_df.txt, a higher value would mean a good discriminative word.
	
	In 20-inter_df.txt, a higher value would mean a worse discriminative word among categories.
