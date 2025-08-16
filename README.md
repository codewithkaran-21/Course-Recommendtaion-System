# Course Recommendation System

This project is a web-based course recommendation system that suggests Coursera courses to users based on their interests. The application is built with Flask and uses a content-based filtering approach to provide recommendations.

## Features

-   Select a course from a dropdown list of available Coursera courses.
-   Receive a list of 6 recommended courses similar to the selected one.
-   Click on a recommended course to navigate to its Coursera page.

## How It Works

The recommendation engine is built on a content-based filtering model. Here's how it works:

1.  **Data Preprocessing:** The system uses a dataset of Coursera courses (`Coursera.csv`). The course data, including the name, description, skills, and difficulty level, is combined to create a "tag" for each course.
2.  **Feature Extraction:** The textual data in the tags is converted into numerical vectors using the TF-IDF (Term Frequency-Inverse Document Frequency) technique. This process is handled by `CountVectorizer` from the scikit-learn library.
3.  **Similarity Calculation:** The cosine similarity is calculated between the vector representations of all courses. This results in a similarity matrix where each entry (i, j) represents the similarity between course i and course j.
4.  **Recommendation:** When a user selects a course, the system looks up the similarity matrix and returns the top 6 courses with the highest similarity scores.

The entire data processing and model creation pipeline is documented in the `course.ipynb` Jupyter notebook. The notebook generates two files:

-   `courses.pkl`: A serialized pandas DataFrame containing the course data.
-   `similarity.pkl`: A serialized NumPy array representing the cosine similarity matrix.

These files are then loaded by the Flask application (`app.py`) to serve the recommendations.

## Dataset

The project uses the [Coursera Course Dataset](https://www.kaggle.com/datasets/siddharthm1692/coursera-course-dataset), which contains information about thousands of courses available on Coursera. The dataset includes the following features:

-   Course Name
-   University
-   Difficulty Level
-   Course Rating
-   Course URL
-   Course Description
-   Skills

## Technologies Used

-   **Backend:** Python, Flask
-   **Data Science:** Pandas, NumPy, Scikit-learn, NLTK
-   **Development Environment:** Jupyter Notebook
-   **Frontend:** HTML, CSS

## Setup and Installation

To run this project locally, follow these steps:

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/Course-Recommendation-System.git
    cd Course-Recommendation-System
    ```

2.  **Create a virtual environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install the dependencies:**
    Create a `requirements.txt` file with the following content:
    ```
    flask
    numpy
    pandas
    scikit-learn
    matplotlib
    nltk
    ```
    Then, install the dependencies:
    ```bash
    pip install -r requirements.txt
    ```

4.  **Generate the model files:**
    -   Launch Jupyter Notebook:
        ```bash
        jupyter notebook
        ```
    -   Open `course.ipynb` and run all the cells. This will generate the `courses.pkl` and `similarity.pkl` files in the root directory.

5.  **Run the Flask application:**
    ```bash
    python app.py
    ```
    The application will be available at `http://127.0.0.1:5000`.

## Usage

1.  Open your web browser and navigate to `http://127.0.0.1:5000`.
2.  Select a course from the dropdown menu.
3.  The application will display a list of recommended courses.
4.  Click on any recommended course to open its Coursera page in a new tab.

## License

This project is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for more details.