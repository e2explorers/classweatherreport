# ☀️ Class Weather Report — GitHub + Google Version

This version uses:

- **GitHub Pages** for the website students and teachers open.
- **Google Apps Script + Google Sheets** as a lightweight temporary classroom relay.
- **Open-Meteo** for city search and weather data.

There is no Supabase requirement.

## Student workflow

1. Enter the teacher's class code.
2. Enter a first name/classroom display name.
3. Search for a city/town.
4. Generate a weather report for now and tomorrow.
5. Write a prediction.
6. Print/save the individual report for the science notebook.
7. Submit it to the class dashboard.

## Teacher workflow

1. Create a class and private PIN.
2. Share only the generated `WX....` class code.
3. Open the dashboard and see student reports.
4. Refresh as students submit.
5. Print the class comparison if desired.
6. Click **Clear Class Reports** after class to remove all student reports for that code.

## Google setup

### 1. Create the backing Google Sheet

Create a blank Google Sheet. You can name it:

`Class Weather Report - Temporary Data`

### 2. Open Apps Script

In the Sheet:

**Extensions → Apps Script**

Delete the starter code and paste the contents of `Code.gs`.

### 3. Initialize the sheets

In Apps Script, select the function:

`setupSheets`

Click **Run** and approve access.

This creates:
- `Classes`
- `Reports`

### 4. Deploy as a Web App

Choose:

**Deploy → New deployment → Web app**

Use:

- Execute as: **Me**
- Who has access: **Anyone**

Deploy and copy the Web App URL.

### 5. Connect the GitHub page

Open `index.html`.

Find:

```js
const APP_SCRIPT_URL = "PASTE_YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE";
```

Replace it with your Apps Script Web App URL.

### 6. Publish on GitHub Pages

Create a GitHub repository such as:

`Class-Weather-Report`

Upload the finished `index.html`.

Enable:

**Settings → Pages → Deploy from a branch → main → /(root)**

The URL should then be similar to:

`https://e2explorers.github.io/Class-Weather-Report/`

## Data clearing

Reports remain in the Google Sheet until the teacher clicks **Clear Class Reports**.

The class-code record itself remains so the teacher can still reopen that code. If you want a completely disposable class later, an additional "Delete Class" button can be added.

## Student privacy

The app:
- does not request device geolocation,
- uses only the city/town the student types,
- can use first names or classroom display names,
- stores submissions only in your Google Sheet until you clear them.
