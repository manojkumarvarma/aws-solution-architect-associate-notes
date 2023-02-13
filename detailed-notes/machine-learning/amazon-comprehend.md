# Amazon Comprehend
Amazon Comprehend is a natural language processing (NLP) service offered by Amazon Web Services (AWS).

### Amazon Comprehend insights
Amazon Comprehend uses a pre-trained model to examine and analyze a document or set of documents to gather insights about it. This model is continuously trained on a large body of text so that there is no need for you to provide training data.

Amazon Comprehend analyzes the following types of insights:

+ Entities – References to the names of people, places, items, and locations contained in a document.
+ Key phrases – Phrases that appear in a document. For example, a document about a basketball game might return the names of the teams, the name of the venue, and the final score.
+ Personally Identifiable Information (PII) – Personal data that can identify an individual, such as an address, bank account number, or phone number.
+ Language – The dominant language of a document.
+ Sentiment – The dominant sentiment of a document, which can be positive, neutral, negative, or mixed.
+ Targeted sentiment – The sentiments associated with specific entities in a document. The sentiment for each entity occurrence can be positive, negative, neutral or mixed.
+ Syntax – The parts of speech for each word in the document.


### Amazon Comprehend Custom
You can customize Amazon Comprehend for your specific requirements without the skillset required to build machine learning-based NLP solutions. Using automatic machine learning, or AutoML, Amazon Comprehend Custom builds customized NLP models on your behalf, using data you already have.

+ Custom classification – Create custom classification models (classifiers) to organize your documents into your own categories.
+ Custom entity recognition – Create custom entity recognition models (recognizers) that can analyze text for your specific terms and noun-based phrases.

### Document clustering (topic modeling)
You can also use Amazon Comprehend to examine a corpus of documents to organize them based on similar keywords within them. Document clustering (topic modeling) is useful to organize a large corpus of documents into topics or clusters that are similar based on word frequency

### Asynchronous batch processing
1. To analyze large documents and large collections of documents, use the Amazon Comprehend asynchronous operations.
2. To analyze a collection of documents, you typically perform the following steps:
3. Store the documents in an Amazon S3 bucket.
4. Start one or more analysis jobs to analyze the documents.
5. Monitor the progress of the analysis jobs.
6. Retrieve the results of the analysis from an S3 bucket when the job is complete.

### Personally identifiable information (PII)

#### Detecting PII entities :

+ To locate the PII entities in your text, you can quickly analyze a single document using real-time analysis.
+ You also can start an asynchronous batch job on a collection of documents.
+ Amazon Comprehend returns a list of detected PII entities, with the following information for each PII entity:
  1. A score that estimates the probability that the detected text span is the detected entity type.
  2. The PII entity type.
  3. The location of the PII entity in the document, specified as character offsets for the start and the end of the entity.
+ Redaction : To redact the PII entities in your text, you can use the console or the API to start an asynchronous batch job. Amazon Comprehend returns a copy of the input text with redactions for each PII entity.
+ Amazon Comprehend has internal list for PII universal entity types like age, address, pin,bank account number and  country-specific PII entity types like SSN, adhaar card, pan.

#### Labeling PII entities : 
Amazon Comprehend provides the following information for each label:
1. The label name of the PII entity type.
2. A score that estimates the probability that the detected text is labeled as a PII entity type.

#### PII real-time analysis (Console) :
+ You can use the console to run PII real-time detection of a text document using the built-in model.
+ The maximum text size is 100 kilobytes of UTF-8 encoded characters.
+ The console displays the results so that you can review the analysis.
+ In the Insights panel, the PII tab displays results for two analysis modes:
  1. Offsets – identifies the location of PII in the text document.
  2. Labels – identifies the labels of identified PII entity types.

#### PII asynchronous analysis jobs (Console) :
+ You can use the console to create async analysis jobs to detect PII entities.
+ From Output mode, select one of the following choices:
  1. Offsets – The job output returns the location of each PII entity.
  2. Redactions – The job output returns a copy of the input text with each PII entry redacted.If you choose Redactions as the output mode, you can select the PII entity types to redact.
+ Input data : specify where the input documents are located in Amazon S3
+ Input format : specify one of the following formats for your input files:
  1. One document per file – Each file contains one input document. This is best for collections of large documents.
  2. One document per line – The input is one or more files. Each line in a file is considered a document. This is best for short documents, such as social media postings. Each line must end with a line feed (LF, \n), a carriage return (CR, \r), or both (CRLF, \r\n). You can't use the UTF-8 line separator (u+2028) to end a line.
+ Output data : choose Browse S3. Choose the Amazon S3 bucket or folder where you want Amazon Comprehend to write the output data that is produced by the analysis.
+ Encryption : To encrypt the output result from your job. Choose whether to use a choose the key alias or ID for KMS key ID associated with the current account or ARN for the key alias or ID under KMS key ID from another account:
+ Access permissions :  Provide an IAM role that:
  1. Grants read access to the Amazon S3 location of your input documents.
  2. Grants write access to the Amazon S3 location of your output documents.
  3. Includes a trust policy that allows the comprehend.amazonaws.com service principal to assume the role and gain its permissions.

#### PII real-time analysis (API) :
Amazon Comprehend provides real-time synchronous API operations to analyze personally identifiable information (PII) in a document. Locating PII real-time entities (API) : DetectPiiEntities and Labeling PII real-time entities (API)
: ContainsPiiEntities

#### PII asynchronous analysis jobs (API) :
You can use asynchronous API operations to create analysis jobs to locate or redact PII entities. 


### Use Cases:

+ Sentiment Analysis: Determine the sentiment expressed in a piece of text as positive, negative, neutral, or mixed.
+ Keyphrase Extraction: Identify the main topics and phrases discussed in a piece of text.
+ Named Entity Recognition: Identify people, organizations, locations, and other entities mentioned in a piece of text.
+ Language Detection: Determine the language in which a piece of text is written.
+ Topic Modeling: Automatically group related documents based on the topics they discuss.


### Benefits:

+ Scalability: Comprehend can process a large volume of text data and is designed to scale as your data grows.
+ Ease of Use: Comprehend is integrated with other AWS services and can be easily integrated into your existing workflows.
+ Accuracy: Comprehend uses machine learning algorithms to deliver high accuracy results.
+ Cost-Effective: Comprehend is a pay-per-use service, so you only pay for what you use, making it cost-effective for businesses of all sizes.


### When to Use:

+ When you need to analyze large amounts of text data, such as customer reviews, social media posts, or survey responses.
+ When you need to automate the process of extracting insights from unstructured text data.
+ When you need to quickly build NLP applications without having to train your own machine learning models.

### Why to Use:

+ To save time and resources: Comprehend automates the process of extracting insights from text data, freeing up time and resources for other tasks.
+ To make data-driven decisions: Comprehend provides accurate and actionable insights from text data, enabling you to make data-driven decisions.
+ To improve customer experiences: Comprehend can help you understand customer sentiment and feedback, allowing you to improve customer experiences.

### Best Practices:

+ Ensure Data Quality: Make sure your text data is of high quality and is preprocessed to remove noise and irrelevant information.
+ Fine-Tune the Model: Use the Comprehend evaluation tools to fine-tune the model for better accuracy.
+ Use Multiple Models: Use multiple models and algorithms to address different NLP tasks, such as sentiment analysis and named entity recognition.
+ Monitor Performance: Regularly monitor the performance of your Comprehend models and adjust as necessary to maintain accuracy.
+ Secure Data: Ensure that your text data is securely stored and processed to protect sensitive information.


### Anti Pattern

+ Using Low-Quality Data: Comprehend's accuracy is directly tied to the quality of the text data it processes. Low-quality data, such as text with many spelling and grammar errors, can reduce the accuracy of the results.
+ Not Preprocessing Text Data: Text data should be preprocessed to remove noise and irrelevant information, such as HTML tags and special characters, before it is fed into Comprehend.
+ Overreliance on Default Settings: While Comprehend's default settings are often sufficient for many use cases, it's important to fine-tune the model for better accuracy. Using the Comprehend evaluation tools, you can adjust settings to achieve the best results for your specific use case.
+ Ignoring Security and Compliance Requirements: When working with sensitive text data, it's important to follow security and compliance requirements, such as encrypting data at rest and in transit.
+ Not Monitoring Performance: Regular monitoring of Comprehend's performance is critical to maintaining accuracy. Over time, text data may change, and the performance of the model may degrade. Regular monitoring will allow you to identify and address any performance issues.
+ Not Integrating with Other AWS Services: Comprehend is designed to be integrated with other AWS services, such as Amazon S3, Amazon Kinesis, and Amazon Lambda. By taking advantage of these integrations, you can build more sophisticated NLP applications and automate workflows.
+ Not Taking Advantage of Batch Processing: Comprehend provides batch processing capabilities, which allow you to process large amounts of text data in parallel, reducing processing times and improving efficiency.
+ Overusing Keyphrase Extraction: While keyphrase extraction is a useful feature, it should be used with caution. In some cases, keyphrases may not accurately reflect the context of the text, leading to incorrect results.