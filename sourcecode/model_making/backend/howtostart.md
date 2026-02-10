# How to Start the Backend Application

Follow these steps to set up and run the image captioning backend.

## Prerequisites
- Python 3.8 or higher installed.

## Setup Instructions

### 1. Navigate to the Backend Directory
Open your terminal or command prompt and navigate to the backend folder:
```cmd
cd sourcecode/model_making/backend
```

### 2. Create a Virtual Environment (Optional but Recommended)
If the `venv` folder does not exist, create it:
```cmd
python -m venv venv
```

### 3. Activate the Virtual Environment
- **Windows (Command Prompt):**
  ```cmd
  venv\Scripts\activate
  ```
- **Windows (PowerShell):**
  ```powershell
  venv\Scripts\Activate.ps1
  ```
- **Linux/Mac:**
  ```bash
  source venv/bin/activate
  ```

### 4. Install Dependencies
Install the required Python packages:
```cmd
pip install -r requirements.txt
```

### 5. Run the Application
Start the Flask server:
```cmd
python app.py
```
*Alternatively, you can double-click `run_app.bat` on Windows.*

> **First Run Note:**  
> When you run the application for the first time, it will automatically download the necessary AI models (BLIP, Kosmos-2, CLIP, etc.) from Hugging Face.  
> - **Download Size:** Approximately 5-10 GB.  
> - **Time:** Depends on your internet speed. Please be patient.  
> - **Internet Required:** Ensure you have an active internet connection.
>
> **Alternative Model Download:**
> If the automatic download fails or is too slow, you can manually download the models from the following Google Drive link:
> [Google Drive Models Folder](https://drive.google.com/drive/folders/1MlD8SRhAOqRFn2L2kGgdSa_RpW56rX65?usp=sharing)
> 
> After downloading, place the model files in the `sourcecode/model_making/backend/models` directory. The application will need to be updated to load from this local directory if you choose this method.

The server will start at `http://127.0.0.1:5000/`.
