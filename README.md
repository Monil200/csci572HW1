csci572HW1
==========
Configuring Tika (deduplication off):

As per the documentation, https://tika.apache.org/1.5/parser_guide.html 
Create a folder “tsv” in tika-1.6/tika-parsers/src/main/java/org/apache/tika/parser folder and copy the following files in it
		1)TSVParser.java
		2)JSONTableContentHandler.java
Replace the parser.parser file in  tika-1.6/tika-parsers/src/main/resources/META-INF/services with the one we have submitted.
Re-Install maven using
			mvn clean install
Create the following sub folders in “tika-1.6” folder
	1)Inputs
	2)Outputs
Copy the input files(.tsv extension) into the “input folder” on which the tika parser has to be invoked.
Place colheaders.txt in “output folder” which was previous created
Copy crawler.py into “output  folder”. This is where the output JSON files will be generated.

Run:

Go to the output folder and run the following command:

python crawler.py
The crawler runs on the input files present in the input folder and produces json files in the output folder one json file per line.

Tika with Deduplication:

Place the deDuplicateFinder.py in the outputs folder created above.
Run the deDuplicateFinder.py to get the number of unique job postings.
	python deDuplicateFinder.py
Instructions for running ETLlib

Create following folder in Tika 1.6 
            etlliboutput 
 Place the etllibJsonExtractor.py  in etllibouput folder 
Place colheaders.txt in “etlliboutput” which was previous created

run the etllibJsonExtractor.py to get list of individual json output files 
		python etllibJsonExtractor.py  
   Once this process  gets executed ettliboutput folder  will contain list of individual json files 
We can our deduplication algorithm on the generated individual json output files by place the deDuplicationFinder.py in this folder and execute it as mentioned in the previous steps.
Fix to ETL Lib
We have noticed that ETL lib was producing each unique record twice. We have made changes to fix this bug. We believe this issue was a blocker. This change was merged into original ETL code in the following link        https://github.com/chrismattmann/etllib/pull/27
 


           





