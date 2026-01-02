# Markdown → Google Doc (Google Docs API)

This project converts the provided meeting notes written in Markdown into a newly created Google Doc using the Google Docs API. The notebook formats the document to match the Markdown structure (headings, nested bullets, checkboxes, @mentions styling, and footer styling).

## 1) Brief description
The notebook reads the given Markdown meeting notes and creates a Google Doc that looks the same:
- Headings are applied as H1/H2/H3
- Bullets are nested correctly
- Action Items are converted to checkboxes
- @mentions and the footer are styled

## 2) Setup instructions
1. Open the `.ipynb` file in Google Colab.
2. Run the install cell (Dependencies section below).
3. Run the authentication cell (you will be prompted to sign in).
4. Run the remaining cells to create and format the Google Doc.

## 3) Required dependencies
Install in Colab:
```bash
pip install google-api-python-client google-auth-httplib2 google-auth-oauthlib
```

## 4) How to run in Colab
1. Authenticate in Colab:
```python
from google.colab import auth
auth.authenticate_user()

import google.auth
creds, _ = google.auth.default(scopes=[
    "https://www.googleapis.com/auth/documents",
    "https://www.googleapis.com/auth/drive.file"
])
```
2. Run the remaining notebook cells. The notebook will create a new Google Doc, insert the Markdown content, and apply headings, nested bullets, checkboxes, @mention styling, and footer styling using Docs API `batchUpdate`.
3. Output at the end of a successful run:
```
✅ Created & formatted doc.
Doc ID: <doc_id>
Open in browser: https://docs.google.com/document/d/<doc_id>/edit
```
Open the printed link to view the final formatted document.

## Notes / Troubleshooting
- You may see warnings like `google_auth_httplib2: httplib2 transport does not support per-request timeout`. These are not blocking. If the doc is created and the link opens, everything is working.
- If you run the notebook multiple times, it will create multiple Google Docs in your Drive (expected behavior).
