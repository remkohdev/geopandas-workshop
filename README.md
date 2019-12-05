# Explore UK Crime Data with Pandas and Geopandas

In this workshop you will learn how to expand your Python data analysis skills to geospatial data. The workshop is aimed at people who are interested in data science and data analysis.

During the workshop we will analyse UK Crime Data with Pandas and GeoPandas in a Jupyter notebook. We first will look at the properties of geospatial data and explore the different commands. After you have learned the basics we will go through some exercises analysing the UK Crime Data to explore patterns and trends and create a few maps of crime rates in London.

## Environment Setup

In this workshop we will use IBM Watson Studio to run a notebook. For this you will need an IBM Cloud account to provision an instance of Watson Studio and Cloud Object Storage. If you do not have a Watson Studio service already provisioned, follow the steps outlined in these [instructions](https://github.com/jrtorres/dsai-workshop-dataprocessing/blob/master/SetupWatsonStudio.md)

### Store this repository on your local computer.

   If you have GIT on your machine, clone this repository locally. Open a terminal and run:

   ```
   $ git clone https://github.com/jrtorres/geopandas-workshop.git
   ```

   If you do NOT have GIT on your machine, you can just download the repository as a ZIP file. From the browser, select the "Download as Zip" option (_Note: The screenshot may show a different respository name, make sure you are downloading the correct repository_):

   ![Download Repo](images/ss0.png)

## Load Notebook in Watson Studio

### 1. Create a new Project

- You should now be in Watson Studio (http://dataplatform.ibm.com)
- Create a new project by clicking on `Get Started` and `New Project`, or `Create Project`
- Give your Project a name.
- Select an Object Storage from the drop-down menu. This is used to store the notebooks and data.
- click `Create`.  

* If no Storage is listed, add a new Data Storage,

	![](../images/project-add-storage.png)

  * On the right half of the window, click the `Add` link to define object storage for the project,
  * A new window or tab will open to create Cloud Object Storage,
  * Select the `Lite` option,
  * Click `Create`,
  * Select the `default` for `Resource group`,
  * For `Service name` enter a name, e.g. `<username>-cloud-object-storage-<random 2 characters>`,
  * Click `Confirm`,

* Click `Refresh`,
  * Make sure an Object Storage is now selected,
  * Click `Create`,

### 2. Create a Project Access token

To load the data into a notebook you need an Access Token.

- Go the Settings tab at the top of the Project and scroll down to `Access tokens`.
- Click `New token`
- Give the new token a name, select `Editor` and click `Create`

   ![Access Token](images/token.png)

### 3. Create a custom Python environment

As geopandas is not installed in the default Python environments you need to create a customized environment. This uses `conda create`. But as the environment is running in the Cloud there are a few steps to go through:

- Go to the environments tab at the top of your project
- Click on `new environment definition`

   ![New Environment](images/new_env.png)

- Give your new environment a name
- Keep the default, select the free hardware configuration `Free - 1 vCPU and 4 GB RAM` and click `Create`

   ![Customize Link](images/customize.png)

- In the next screen you can customize the new environment. Scroll down and click on the `Create` link under Customization

   ![Customize Environment](images/customize_env.png)

- A textfield appears that you can edit. Delete all text and copy and paste the below into the textfield:

   ```# Please add conda channels here
   channels:
   - defaults
   - conda-forge
   
   # Please add conda packages here
   dependencies:
   - geopandas
   - geoplot
   - pysal
   - folium

   # Please add pip packages here
   # To add pip packages, please comment out the next line
   #- pip:
   ```

- Click `Apply`

   ![Apply Environment](images/customize_env2.png)

- Now you can use this new environment to run notebooks

## 4. Load and run a notebook

- Add a new notebook. Click `Add to project` and choose `Notebook`:

   ![Add Notebook](images/newnotebook.png)

- Choose new notebook `From URL`. Give your notebook a name and copy the URL `https://github.com/jrtorres/geopandas-workshop/blob/master/notebooks/geopandas-workshop.ipynb`

   ![Notebook](images/notebookfromurl.png)

- Select the custom runtime enviroment that you created in step 3 and click `Create Notebook`.

-  The notebook will load, use the instructions in the notebook by running through the cells.