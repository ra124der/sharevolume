# SEC Common Stock Shares Outstanding Viewer

This is a single-file, responsive web application built with Tailwind CSS that displays the highest and lowest reported Common Stock Shares Outstanding for a given company, fetched from the SEC EDGAR API.

## Features

*   Displays company name and the max/min shares outstanding for fiscal years (FY) after 2020.
*   Uses Tailwind CSS for a modern, responsive design.
*   Dynamically loads data based on a CIK (Central Index Key) provided in the URL.
*   Default CIK for Campbell's Company is loaded if no CIK is specified.

## How to Run

1.  Save the `index.html` file to your local machine.
2.  Open `index.html` in your web browser.

### Viewing Data for Campbell's Company (Default)

Simply open `index.html`.

### Viewing Data for a Specific Company

You can specify a CIK (Central Index Key) as a URL parameter to fetch data for a different company.

**Example:**

To view data for Apple Inc. (CIK: 0000320193), open your browser to:

`index.html?CIK=0000320193`

**Note:** The application uses a proxy (`api.allorigins.win`) to bypass CORS restrictions when fetching data from the SEC API. While `fetch` includes a `User-Agent` header, this is sent to the proxy and may not be forwarded to the SEC endpoint. For production applications, a dedicated server-side proxy is recommended to ensure full compliance with SEC API guidelines regarding `User-Agent` identification.

## Data Source

Data is retrieved from the SEC EDGAR API: `https://data.sec.gov/api/xbrl/companyconcept/{CIK}/dei/EntityCommonStockSharesOutstanding.json`.

Only entries with a fiscal year (`fy`) greater than `2020` and a valid numeric `val` are considered for the min/max calculation.