# Digital Archivist: Legacy Macroseismic Data Processing

This repository contains the data and processing workflows for **"The Digital Archivist: Automating Legacy Macroseismic Data Processing Using Large Language Models"**. This project introduces a novel, automated pipeline for extracting, structuring, and geocoding historical earthquake intensity reports from unstructured legacy documents.

## Project Overview

Macroseismic data (descriptions of shaking and damage) are critical for understanding historical earthquakes, but they are often trapped in inconsistently formatted 20th-century reports. The Digital Archivist workflow uses the **Gemini 2.5 Pro** large language model (LLM) to automate the extraction of these records and the **Google Geocoding API** to provide precise geographic coordinates.

## Repository Structure

The data is organized by the two case study earthquakes analyzed in the manuscript:

### 1. 1957 Daly City, California Earthquake

* **Source Data**: `DalyCity_Original.pdf` (The original 159-page USCGS report).


* **Input Chunks**: `chunk1.pdf` through `chunk7.pdf` (The report divided into smaller segments for LLM processing). Due to the Gemini LLM’s context window limitations, it is important to split the original PDF into smaller documents to ensure complete processing of the source document. Each chunk is approximately 20 pages long. This size was determined based on the context length limit of Gemini and through trial and error to be optimal for preventing incomplete extractions while not being too small.


* **LLM Prompt**: `LLM_Prompt.txt` (The zero-shot prompt used to instruct Gemini to extract locations, MMI ratings, and descriptions).


* **Output Dataset**: `DalyCity_Extract.csv` (The final geocoded dataset containing over 2,300 reports).



### 2. 1971 Sylmar, California Earthquake

* **Source Data**: `Sylmar_Original.pdf` (The original 104-page USCGS report).


* **Input Chunks**: `chunk1.pdf` through `chunk5.pdf` (The segmented reports used for processing).


* **LLM Prompt**: `LLM_Prompt.txt` (A modified prompt from Daly City that also includes the full Modified Mercalli Intensity scale for assigning ratings to entries lacking them).
  
* **Output Dataset**: `Sylmar_Extract.csv` (The final geocoded dataset containing over 1,100 reports).

## Usage Instructions

### 1. API Key Setup
To run the Digital Archivist workflow, you must generate two secure API keys:

* **Gemini API Key**: Obtain this through **Google AI Studio**. This allows the workflow to programmatically communicate with the Gemini 2.5 Pro model.
* **Google Geocoding API Key**: Obtain this via the **Google Cloud Console**. This key is required to convert the extracted text addresses into precise latitude and longitude coordinates.

### 2. Environment Configuration
The workflow can simply run in Google Colab for ease of integration with Google Cloud services. 
* Store the API keys as environment variables within the Colab secrets

### 3. Running the Pipeline
* Refer to the sample code in the Daly City folder for the implementation logic (`DalyCity_Sample_Code.ipynb`).

## Citation

If you use this data or workflow, please cite: [INSERT CITATION]
