# language-processor-api
Welcome to the Language Processor API, a robust FastAPI application designed to detect the source language of a given text and translate non-English texts to English. This API leverages FastText for language detection and Hugging Face's MarianMT for translations.


language-processor-api/
├── data/
│   └── cleaned data/
│       └── cleaned_data.xlsx
├── models/
│   └── fast_api_model/
│       └── lid.176.bin
├── notebooks/
├── utils/
│   └── language_processor.py
├── __pycache__/
├── app.py
├── requirements.txt
└── README.md





## Features

- **Language Detection**: Identify the language of the input text.
- **Translation**: Translate non-English text to English.
- **Data Upload**: Upload new data files for processing.
- **Processed Data Retrieval**: Retrieve and view processed data.

## Installation

### Prerequisites

- Python 3.7 or above
- pip (Python package installer)
- Git LFS (Large File Storage)

### Steps

1. **Clone the repository**:
    ```bash
    git clone https://github.com/your-username/language-processor-api.git
    cd language-processor-api
    ```

2. **Install Git LFS**:
    - For Windows:
        ```bash
        choco install git-lfs
        ```
    - For Mac:
        ```bash
        brew install git-lfs
        ```
    - For Linux:
        ```bash
        sudo apt-get install git-lfs
        ```
    - You can also download the installer from the [Git LFS website](https://git-lfs.github.com/).

3. **Initialize Git LFS in Your Repository**:
    ```bash
    git lfs install
    ```

4. **Pull the LFS-tracked files**:
    ```bash
    git lfs pull
    ```

5. **Create and activate a virtual environment**:
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

6. **Install the required dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

## Usage

1. **Run the FastAPI application**:
    ```bash
    uvicorn app:app --host 0.0.0.0 --port 8000 --reload
    ```

2. **Access the API documentation**:
   Open your browser and navigate to `http://127.0.0.1:8000/docs` to interact with the API endpoints.

## API Endpoints

- `POST /detect_language`: Detect the language of a given text.
    - **Parameters**: 
      - `text` (str): The text to analyze.
    - **Returns**: 
      - `language` (str): Detected language.
      - `accuracy` (str): Detection accuracy.
      - `time_spent` (float): Time taken for detection (ms).

- `POST /translate`: Translate a given text to English.
    - **Parameters**:
      - `text` (str): The text to translate.
    - **Returns**:
      - `translation` (str): Translated text.
      - `time_spent` (float): Time taken for translation (ms).

- `POST /upload_data/`: Upload a new data file and process it.
    - **Parameters**:
      - `file` (UploadFile): The file to upload.
    - **Returns**:
      - `info` (str): Upload status.
      - `filename` (str): Name of the uploaded file.

- `GET /get_processed_data`: Retrieve the processed data.
    - **Returns**:
      - `data` (list): List of dictionaries containing processed data.

## File Descriptions

- **`app.py`**: The main FastAPI application script.
- **`utils/language_processor.py`**: Custom module for handling language detection and translation.
- **`data/cleaned data/cleaned_data.xlsx`**: Example data file used for processing.
- **`models/fast_api_model/lid.176.bin`**: Pre-trained FastText language detection model.
- **`requirements.txt`**: File listing the Python packages required for the project.

## Contributing

We welcome contributions to enhance this project! To contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Make your changes and commit them (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request.
