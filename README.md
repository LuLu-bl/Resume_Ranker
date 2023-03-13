# Resume Screening With NLP
## Introduction
This an application for automated resume screening and ranking using NLP technologies that can help companies and job seekers streamline the recruitment process. The application can analyse job descriptions and resumes and identify the most relevant skills, experience, and education required for the job. It then ranks each resume based on how well it matches the job requirements, allowing companies to focus on the most qualified candidates quickly.  The application can also help reduce human biases, ensuring a fair and consistent screening and ranking process. The use of NLP in resume screening and ranking can improve the efficiency and accuracy of the screening process, enabling companies to focus on the most qualified candidates and helping job seekers to increase their chances of being selected.

## Methodology
### Logical Flow and Methods Used 
![](https://github.com/LuLu-bl/Resume_Ranker/blob/fbe39aa5b4e081081d8ea98a06f118e3c7becdd2/Images/methodology.png?raw=true)

- **Text Extraction:** First, created a function named "extract_pdf_text" that accepts a user-provided folder path containing resumes in PDF format. By utilising the python-pdfbox library, it will convert the .pdfs to .txt files. In environments where the python-pdfbox library is not supported, used the PyPDF2 library. 

	**Libraries used:** 
		[python-pdfbox](https://en.wikipedia.org/wiki/PDFBox), 
		[os](https://en.wikipedia.org/wiki/Operating_system), 
		[glob](https://en.wikipedia.org/wiki/lob_%28programming%29)

- **Loading:** The pdf resumes that were extracted to text were then loaded into a .csv file. Each text file was allocated a unique ID alongside the text extracted and the filename using the text to csv function that created. The load_csv function was then utilised to load the .csv file into a pandas data frame. 

	**Libraries used:** 
	[CSV](https://en.wikipedia.org/wiki/Comma-separated_values)
	[pandas](https://en.wikipedia.org/wiki/Pandas_%28software%29)
	[hashlib](https://en.wikipedia.org/wiki/Cryptographic_hash_function)

- **Preprocessing and Cleaning:** Then utilized the NLTK library to clean the resume text as follows:
	- Regex to remove hyperlinks, special characters, or punctuation.
	- Lowering text
	- Splitting text into arrays based on space
	- Lemmatizing text to its base form for normalisation
	- Removing English stopwords
	The cleaned text was appended as a column to the data frame, respectively.

	**Libraries used:** 
	[NLTK](https://en.wikipedia.org/wiki/Natural_Language_Toolkit)
	[re](https://en.wikipedia.org/wiki/Regular_expression)

- **Extract Skills:** To extract skills, used skillNer, which is a module that allows us to automatically extract skills and certifications from unstructured job postings, texts, and applicant resumes. The extracted skills (both soft and hard skills) were then passed through the data frame 

	**Libraries used:**
	[skillNer](https://en.wikipedia.org/wiki/Named-entity_recognition)
	[spacy](https://en.wikipedia.org/wiki/SpaCy)

- **Ranking:** Once the skills are visualised, the user gets to pass keywords and a mark respective to each keyword mentioned. Developed the function to ensure that points are given to one word only once.
	
	eg: if the score for Java is 2 the points allocated for the candidate will be only 2 irrespective of how many times the word appears in a resume. 
	
	This way the recruiter can prioritise the important skills. Afterwards, the scores for each resume were calculated and sortedwith maximum scorers at the top of the list.

	**Libraries used:** [numpy](https://en.wikipedia.org/wiki/NumPy)

## Implementation
### Web page for resume submission and resume rating
During the implementation phase, created a web application as company career page using Webstorm software, which ran on localhost. Through this application candidates can submit their resumes for jobs and the HR unit can find the best candidate from ranking. The application had a feature to upload resumes in PDF format, which was connected to Google App Script. The resumes were uploaded to our Google Drive and connected to Google Colab.
It ran an automated process to rank the resumes based on a set of criteria, and the results were displayed on the web application in CSV format.

Overall, the implementation of the application was successful, and it was able to achieve the desired functionality of automating the resume ranking process. The use of Google App Script and Google Colab allowed to efficiently process and analyze the resumes, while the integration with web application provided a user-friendly interface for uploading and viewing the results.

### Technologies

| Category                  | Tools/Libraries              | Description                                |
| -------------------------| ----------------------------| -------------------------------------------|
| Programming Languages    | Python 3.7                  | Implementation of the code                 |
|                           | HTML, CSS, JavaScript       | Implementation of the web application      |
| Development Environment   | Google Colab                | Write and execute the model                 |
|                           | WebStorm                    | For integrated development environment      |
| Framework                 | Node.js Express             | To take common structure for web application|
| Deployment                | Google AppScript            | To deploy the final version of application. |
| Python Libraries          | pdfbox                      | Used to extract text from PDF resumes       |
|                           | skillNer                    | Used to extract the skills from the resumes.|
|                           | NLTK                        | It is used for preprocessing text data and removing stopwords.|
|                           | Spacy                       | Used to preprocess the text in the resumes and extract entities using the EntityRuler.|

**The implementation involved the following steps:**
-	Upload the resume: The resumes that are uploaded come through the AppScript forum and are directly saved to a Google folder.
-	Loading the resumes: The resumes were loaded from a folder using the glob library.
-	Extracting the text from the resumes: The text was extracted from the PDF resumes using the python-pdfbox library.
-	Converting the text to a CSV file: The extracted text was then converted to a CSV file.
-	Preprocessing the text: The text in the CSV file was preprocessed using Spacy and NLTK libraries. The text was converted to lowercase, punctuation was removed, stop words were removed, and the remaining words were lemmatized.
-	Extracting the skills: The preprocessed text was then used to extract the skills present in the resumes using the skillNer library.
-	Ranking the resumes based on skills: The resumes were ranked based on the presence of the keywords related job field. example:
	- Data Science - Machine learn, AI,  Data analysis,  R,  Python.
	- Software Engineering – Python, Java, SQL, Linux

Overall, the implementation involved the use of several tools and libraries for data extraction, preprocessing, and visualization. The end result was a set of visualizations and rankings that can be used to gain insights into the skills present in the resumes.


