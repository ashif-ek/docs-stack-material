# Installation Overview

Since this documentation covers multiple independent projects, installation steps vary by repository. However, most follow a standard pattern.

## General Installation Steps

1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/ashif-ek/<repo-name>.git
    cd <repo-name>
    ```

2.  **Install Dependencies**:
    *   For **JavaScript/Video** projects:
        ```bash
        npm install
        # or
        yarn install
        ```
    *   For **Python** projects:
        ```bash
        python -m venv venv
        source venv/bin/activate  # Windows: venv\Scripts\activate
        pip install -r requirements.txt
        ```

3.  **Environment Configuration**:
    *   Most projects require a `.env` file. Check the specific project documentation or `README.md` for required variables.

4.  **Run the Application**:
    *   JS: `npm run dev`
    *   Python (Django): `python manage.py runserver`
    *   Python (FastAPI): `uvicorn main:app --reload`

## Project-Specific Guides

For detailed instructions, refer to the specific project pages:

*   [Portfolio React Installation](projects/github_repos/portfolio-react.md#installation)
*   [Noirel Ecommerce Installation](projects/github_repos/noirel-ecommerce.md#installation-setup)
*   [Salary Checker Setup](projects/github_repos/salary-checker.md#setup-instructions)
*   [Time Lens Setup](projects/github_repos/time-lens-python.md#run-locally)