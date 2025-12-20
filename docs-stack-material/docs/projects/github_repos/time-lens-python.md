# Time Lens — A New Way to See Time

**Time Lens** is a mindset tool that transforms how we perceive time. Instead of thinking in hours and minutes, this tool converts real time into a powerful life-model:

*   **1 real day** = 1 life-year
*   **1 hour** = 1 life-month
*   **1 minute** = 1 life-day
*   **1 second** = 1 life-hour

The goal is simple: **Help you feel the true weight of time so every minute becomes intentional.**

[Live Demo](https://time-lens-python.vercel.app/)

## 🎯 Why This Exists

People say “value your time,” but few explain how to *actually* value a minute. Time Lens reframes every real minute into a life-day—making even micro-actions meaningful.

Suddenly:
*   Wasting a **minute** feels like wasting a **day**.
*   Wasting an **hour** feels like losing a **month**.
*   Using a few minutes wisely feels like real progress.

## What Time Lens Gives You

For any real duration, the tool returns:
*   Life-days, life-months, and life-years.
*   A deep insight.
*   A meaningful action.
*   A psychological explanation.
*   A warning if wasted.
*   A description of who you become if you use it well.

Built with a custom advanced suggestion engine.

## 🛠️ Tech Stack

*   **Python**
*   **FastAPI**
*   **Uvicorn**
*   **HTML + CSS**
*   **JavaScript**
*   **Deployed on Vercel**

## Project Structure

```text
time-lens/
│
├── main.py
├── requirements.txt
├── render.yaml
│
├── templates/
│   └── index.html
│
└── static/
    └── style.css
```

## 📦 Run Locally

1.  **Create virtual environment**
    ```bash
    python -m venv venv
    ```

2.  **Activate it**
    *   Windows:
        ```powershell
        venv\Scripts\activate
        ```
    *   Mac/Linux:
        ```bash
        source venv/bin/activate
        ```

3.  **Install dependencies**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Start server**
    ```bash
    uvicorn main:app --reload
    ```

Visit: http://127.0.0.1:8000

[View on GitHub](https://github.com/ashif-ek/time-lens-python)
