# Excel Worker with LangGraph

Use case: Enable users to analyze Excel data using AI generated queries, automating tasks like data preview, SQL execution, and Pandas-based transformations.

If you have any questions or would like to collaborate, feel free to reach out to me on [LinkedIn](https://www.linkedin.com/in/jenya-stoeva-60477249/). You're more than welcome!

## Workflow

**1. Extracting Excel File Preview**

**_Input:_** Free-form user query (e.g., "Tell me which ticker symbols in the proposed price range $10.00 to $20.00 have an average performance above 20%, given that performance is spread across months 1 through 12."), Excel file.
**_Output:**_ Excel file preview, including column names and data types.

*Manual Step:* Read and extract an Excel file preview, then pass it to the LLM.

**2. LLM Query Generation & Tool Selection**

*Input:* Excel preview.
*Output:* Generated query, selected tool, and LLM-prompt (a refined version of the user query).

*LLM Step:* The LLM analyzes the preview and determines whether to generate a Pandas query or an SQL query. It then selects the appropriate tool for execution.

**3. Query Validation & Execution**
LLM Step: The LLM reviews the generated query and attempts execution.
Error Handling: If the first attempt fails, the LLM analyzes the error and tries to fix the query for a second attempt. The number of retry attempts is configurable.
Input: Output from the previous step + query execution output state.
Output: Execution result from the LLM generated query, answering the user query.

## Intallation

<b>Prerequisites</b>

* Access to <b>JupyterLab, Google Colab</b>, or another interactive computing environment to run this Jupyter Notebook.
* Access to LLM API.

### Step 1: Clone the Repository

Clone this repository to your local machine:
```
git clone <REPOSITORY_URL>
cd <PROJECT_FOLDER>
```

### Step 2: Open Jupyter Notebook in JupyterLab

Ensure that ```<PROJECT_FOLDER>``` is accessible in JupyterLab by setting it as your working directory in JupyterLab.
 * In JupyterLab, use the "Open from Path" option to load ```ExcelWorkerLangGraph.ipynb```.
 * Similarly, load ```.env``` and populate the variable keys with appropriate values.
 * The first cell in the Notebook installs the required libraries: **%pip install langchain langgraph pandas python-dotenv duckdb**

### Step 3: Run the Jupyter Notebook

To execute the notebook, select each cell and press ```Shift + Enter```.
