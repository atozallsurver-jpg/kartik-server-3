# Flask Safe Deployment Package

This is a minimal, **safe** Flask app you can deploy to most hosting platforms (Render, Railway, Heroku clones, Bot Hosting Net, etc.).

## What it does
- Serves a simple contact form at `/`.
- Saves submitted messages to `messages/messages.txt` (append-only).
- Does **not** perform any automated messaging or platform abuse.

## Files
- `main.py` - Flask application
- `templates/index.html` - Form HTML
- `requirements.txt` - Python dependencies
- `Procfile` - For process managers (gunicorn)
- `runtime.txt` - Python runtime hint
- `.gitignore` - common ignores
- `messages/messages.txt` - stored messages (created empty)

## To run locally
```bash
python -m venv venv
source venv/bin/activate   # on Windows: venv\Scripts\activate
pip install -r requirements.txt
python main.py
```
Then open http://127.0.0.1:5000

## To deploy
- Upload the whole folder to your host.
- Ensure a `PORT` environment variable is provided by the host (most hosts do this automatically).
- Set `FLASK_SECRET` env var to a random value for production.
- Use the provided `Procfile` (if your host supports it) to run with gunicorn.

## Important
This package purposefully avoids automating activity on other platforms. Use official APIs and follow platform policies when building integrations.
