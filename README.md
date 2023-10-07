# Introduction

Jupyter Notebooks are widely used in the field of data science for interactive data analysis, visualization, and model development. However, one of the major challenges in using Jupyter Notebooks is the lack of automatic documentation generation. Currently, users have to manually write and format documentation for their notebooks, which can be time-consuming and error-prone.

The goal of this project is to develop a tool that automatically generates documentation for Jupyter Notebooks. The tool will extract information from the notebook, specifically the code cells, and generate documentation for the code that was passed to the tool. Ultimately, the tool can be used by a programmer to write documentation automatically which they will only have to proof-read instead of manually writing it themselves. 

# Tool usage
All of the code that is needed to run this code can be found on the GitHub repository for this project (incl. the requirements file). In order for the tool to work, the user will need to have an OpenAI API key from [OpenAI](https://platform.openai.com/account/api-keys). This key should be stored in a file called `api_key.txt` in the same directory as the project. The key should be the only thing in the file. 

First, the user will have to install the requirements.txt file. This can be done by running the following command in the terminal (virtual environment recommended):

```bash	
pip install -r requirements.txt
```

The project can then be run in two ways: Locally, by running the main.py file, or via streamlit:

```bash	
python3 main.py testbook.ipynb # testbook.ipynb is the name of the notebook that should be used as input
```

```bash	
streamlit run app.py
```

Using the streamlit version, the user selects a local .ipynb file and uplaods it to the web-application. The webapp then queries GPT-3.5 with the different code chunks and returns the output by GPT 3.5, and writes them into a code chunks in a new document. This new document can then be downloaded once all code-cells have been queried. To ensure ease-of-use, we have included a preview of both the input and output files so that the user can see the comments generated by GPT 3.5 before deciding to download the new file.

# Input preparation
Our tool works best with code chunks that do not contain any documentation or comments in them. For this reason, preparing any input and cleaning them of these elements is highly recommended. Also, due to the token limit of the GPT 3.5 model, some codes might need to be shortened for the tool to work. Further improvement could focus on how to split code cells to ensure that all notebooks independent of code cell length can be run. 

# Notebook for testing
We have added a sample jupyter notebook that can be used as an input. It is called "testbook.ipynb".

# Final remarks
Since this project was about building a tool that automatically writes code documentation, we used our own tool to write most of our documentation, with some small human adjustments. All of the Docstrings for the functions were generated using our tool on our own code. 