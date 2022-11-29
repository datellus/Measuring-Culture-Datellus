# __An Adaptation from the Paper Measuring Corporate Culture Using Machine Learning by Datellus__

The following files shows how to execute the instructions from the following repository: https://github.com/MS20190155/Measuring-Corporate-Culture-Using-Machine-Learning . The original repository was from 2020, therefore there have been changes in the way we need to execute the code, especially in the way we load de __Stanford Core NLP__ .

## __Cloning the Repo__

First you need to clone this repo. It has the same files as the original with some minor changes. You can do this by using __git clone__.

## __Most Important Change : Installing Stanza__

The original repository uses the __StanfordNLP Module__ however it outputs an error of timeout. That´s why we need to install __Stanza__. You can find the instructions in here https://stanfordnlp.github.io/stanza/installation_usage#installation. 

After installing __Stanza__ you need to download __Stanford Core NLP__. Thankfully, Stanza does this for us. All the instructions are shown here https://stanfordnlp.github.io/stanza/client_setup.html. You have to choose if you want stanza to install the dependencies on a default path or a specific path. Personally, I like to set my own custom path. 

Once the files are download, you have to tell stanza were this files are. I worked on Windows, so I set this path manually. You have to navigate to the folder were stanza was installed an search for the client.py file :  __C:Path_to_Stanza/stanza/stanza/server/client.py__ . Working with Ubuntu is easier since you just export the Env Variable as mentioned on the link. Now, open this file with any text editor and find the line (__by default line 248__) were the __CoreNLPClient Class__ is built. In there, find the __classpath__ argument and manually set the path to the folder in which stanza downloaded the corenlp files like this : "C:/Users/Marcelojtc/Desktop/Measuring-Corporate-Culture-Using-Machine-Learning/stanfordstanza/*". 

Notice how I __Add an *__ at the end, this is necessary to work.

## Transforming PDF Files to Txt Files

The model uses Text files so the first step is building this txt files. You need to run the file __Pdf2Text__ inside the data folder. In this folder you need to store all the pdf files that you want to use, particulary in the folder which says __pdf_files__. After selecting all the files, open your terminal and run __python pdf2text.py__. This will transform all of the pdf files on the pdf folder into __txt format__. It will generate two files into the __input folder : documents and document_ids__ both of them are used in the next step.

## Parsing the text

The next step is __Parsing__ . Running the command __python parse.py__ will parse de text, which means, it will analyze each word and it´s meaning (Part of Speech) in the sentence. This is necessary for the final test. This step will create a __Parsed Text__ located in the __data/processed/parsed__ folder.

## Unigrams , Bigrams, Trigrams and Scoring



