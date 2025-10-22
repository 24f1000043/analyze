# Data Processing and CI/CD Pipeline

This project demonstrates an automated pipeline for processing a CSV data file using a Python script. It leverages GitHub Actions for continuous integration, including code linting, script execution, and deployment of the results to GitHub Pages.

## Overview

The core of this project is a Python script, `execute.py`, which reads data from `data.csv`, performs calculations, and outputs the result in JSON format. A GitHub Actions workflow automates this entire process on every push to the `main` branch, making the result available on a public-facing website.

## Features

-   **Data Processing**: A Python script (`execute.py`) using the Pandas library for data manipulation.
-   **Automated CI/CD**: A GitHub Actions workflow (`.github/workflows/ci.yml`) that automates testing and deployment.
-   **Code Quality**: `ruff` is used for linting to ensure Python code quality and consistency.
-   **Automated Publishing**: The JSON output (`result.json`) is automatically generated and published to a live GitHub Pages website.

## Project Structure


.
├── .github/workflows/
│   └── ci.yml         # GitHub Actions workflow
├── data.csv             # Input data file
├── execute.py           # Python processing script
├── index.html           # Web page for displaying results
└── README.md            # This file


## Prerequisites

To run this project locally, you will need:

-   Python 3.11 or newer
-   Pip (Python package installer)

## Local Setup and Usage

1.  **Clone the repository:**
    bash
    git clone https://github.com/your-username/your-repository.git
    cd your-repository
    

2.  **Create a virtual environment (recommended):**
    bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    

3.  **Install dependencies:**
    The project requires `pandas` to run and `ruff` for linting.
    bash
    pip install pandas==2.3 ruff
    

4.  **Run the linter:**
    To check the code quality, run `ruff`:
    bash
    ruff check .
    

5.  **Execute the script:**
    To process the data and generate the output file, run the script and redirect its standard output to a file:
    bash
    python execute.py > result.json
    
    This will create a `result.json` file in the root directory. You can view the output by opening `index.html` in your browser.

## CI/CD Pipeline

The CI/CD pipeline is defined in `.github/workflows/ci.yml` and is triggered on every push to the `main` branch.

### Workflow Steps

1.  **Checkout Code**: Checks out the repository's code.
2.  **Set up Python**: Sets up a Python 3.11 environment.
3.  **Install Dependencies**: Installs the required Python packages (`pandas`, `ruff`).
4.  **Lint with Ruff**: Runs the `ruff` linter to check for code style issues and errors.
5.  **Generate Output**: Executes `python execute.py > result.json` to generate the result file.
6.  **Deploy to GitHub Pages**: An artifact containing `index.html` and the generated `result.json` is uploaded and deployed to the GitHub Pages environment.

**Note**: The `result.json` file is intentionally not committed to the repository. It is a build artifact generated exclusively within the CI pipeline.

### Enabling GitHub Pages

To view the live output, you need to enable GitHub Pages in your repository settings:

1.  Go to your repository on GitHub.
2.  Click on **Settings** > **Pages**.
3.  Under "Build and deployment", select **GitHub Actions** as the source.
4.  Your site will be deployed and available at `https://<your-username>.github.io/<your-repository-name>/`.
