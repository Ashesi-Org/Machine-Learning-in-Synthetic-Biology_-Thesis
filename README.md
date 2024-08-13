# Machine-Learning-in-Synthetic-Biology_-Thesis
This is a capstone thesis on the use of machine learning for the optimization of genetic circuits in Synthetic Biology: Focusing on Promoter prediction for gene expression in E.Coli
Overview
This project integrates gene data from a CSV file with operon information fetched from a GraphQL API. It uses Python libraries like requests, pandas, networkx, and sklearn to process and visualize this data. The system also includes a machine learning classifier for predicting gene classes based on gene names.

Features
GraphQL Querying: Fetches operon and gene data from a local instance of RegulonDB hosted in a Docker container.
Data Integration: Merges operon data with gene data from a CSV file, including gene products, promoter sequences, and associated operons.
Machine Learning Classification: Uses a Support Vector Machine (SVM) to classify gene functions.
Graph Visualization: Creates a relational graph of operons, genes, promoters, and regulators.
CSV Data Export: Saves the integrated data into a CSV file.
Prerequisites
Python 3.x with the following libraries:
requests
pandas
networkx
matplotlib
sklearn
Docker and Docker Compose to host the RegulonDB locally.
Ngrok to expose the local instance of RegulonDB to the internet.
Installation
1. Set Up RegulonDB
Docker:

Download or copy the content of the docker-compose.yml file.
In a terminal, navigate to the directory containing the file and run:
bash
Copy code
docker compose pull
docker compose up -d
RegulonDB will now be accessible at http://localhost:7000/ for the Web App or http://localhost:7000/graphql for the GraphQL Playground.
Ngrok:

Install Ngrok and run the following command to expose the local RegulonDB instance:
bash
Copy code
docker run --net=host -it -e NGROK_AUTHTOKEN=<your_ngrok_authtoken> ngrok/ngrok:latest http 7000
Ngrok will provide a public URL that you can use as the GraphQL API endpoint.
2. Install Python Dependencies
Install the required Python libraries:

bash
Copy code
pip install requests pandas networkx matplotlib scikit-learn
Usage
Load Gene Data:
Update the csv_file variable with the path to your gene data CSV file.

Fetch Operon Data:
Provide a gene name when prompted to fetch related operon data from the GraphQL API.

Integrate and Visualize Data:
The script will integrate the gene and operon data, classify genes, and output the results as a CSV file (integrated_data.csv). A relational graph of operons, genes, promoters, and regulators will also be displayed.

Example Usage
bash
Copy code
python script.py
Follow the prompts to enter the gene name, and the script will handle the rest.

Visualization
The graph visualization displays nodes representing operons, genes, promoters, and regulators, with different colors for each type. The nodes are connected by edges that represent relationships like regulation and binding.

New Releases
When a new version of RegulonDB is released, update the Docker images and restart the instance by following the installation guide.

Note
This setup assumes that Docker and Ngrok are properly installed and configured on your system.
Ensure that the CSV file used contains the necessary columns (GeneName, GeneProduct, PromoterSeq, etc.) for the integration to work correctly.
