**EMSR Data Crawler**

**Credits**

Forked from Benjamin Jordan, who created the original github post for this combined project.

**Overview**

This Python script automates the retrieval and downloading of EMSR (Emergency Mapping Service Rapid Mapping) data from the Copernicus Emergency Management Service. The script fetches disaster-related data based on user-defined queries (country, city, or disaster type) and downloads available Geographic Reference (GRA) products.

**Features**

- Fetches EMSR disaster codes for a given country, city, or disaster type.

- Extracts relevant information from the Copernicus EMS API.

- Downloads associated disaster-related data files automatically.

- Implements retry logic for handling API errors (e.g., throttling, forbidden access).

- Saves downloaded files with meaningful names for easy identification.

**Requirements**

Before running the script, ensure you have the following installed:

- Python 3.x

- requests library (install with pip install requests)

**Functionality**

_get_emsr_numbers(query)_

- Retrieves a list of EMSR codes based on the search query.

- Queries the Copernicus API and extracts disaster codes.

_crawl_emsr_data(code, download_path)_

- Downloads available Geographic Reference (GRA) products related to the given EMSR code.

- Handles request errors with retry mechanisms.

_crawl_for_data(user_defined_country, dwnld_path)_

- Calls get_emsr_numbers() to fetch EMSR codes and then crawl_emsr_data() to download associated data.

**Error Handling**

The script includes error handling for:

- API request failures: Handles connection errors and timeouts.

- 403 Forbidden errors: Skips files if access is denied.

- 429 Throttle errors: Implements exponential backoff to avoid exceeding request limits.

- File download issues: Checks for download failures and logs them accordingly.
