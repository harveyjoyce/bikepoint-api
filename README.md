# BikePoint API Data Downloader

This project retrieves live Santander Cycle hire (BikePoint) data from the **Transport for London (TfL) BikePoint API**, logs execution details, and stores the downloaded data locally as timestamped JSON files.

It is based on the public TfL BikePoint API and references the following GitHub repository:  
https://github.com/harveyjoyce/bikepoint-api

---

## Features

- Fetches real-time BikePoint data from TfL  
- Automatic retry logic for failed API requests  
- Saves API responses as timestamped JSON files  
- Generates structured log files for monitoring and debugging  
- Automatically creates required directories (`data/` and `logs/`)  

---

## Project Structure

```
.
├── data/
│   └── YYYY-MM-DD HH-MM-SS.json
├── logs/
│   └── YYYY-MM-DD HH-MM-SS.log
├── extract_bike_points.py
└── README.md
```

---

## Requirements

- Python 3.8+
- Internet connection

### Python Dependencies

Install required packages using:

```
pip install requests
```

(Standard library modules used: `os`, `json`, `datetime`, `time`, `logging`)

---

## How It Works

1. Sends a GET request to the TfL BikePoint API:
   ```
   https://api.tfl.gov.uk/BikePoint
   ```
2. Retries the request up to **3 times** if an unsuccessful response is received.
3. On success:
   - Saves the response as a JSON file in the `data/` directory
   - Creates a timestamped log file in the `logs/` directory
4. Logs system activity at INFO level and above.

---

## Logging

Each script execution creates a log file containing:

- System status messages
- Successful downloads
- Warnings and errors
- Critical failures

Example log entry:

```
2026-01-07 12:30:01 - INFO - Download successful at 2026-01-07 12-30-01 😊
```

---

## Usage

Run the script with:

```
python extract_bike_points.py
```

On successful execution:
- A JSON file will be saved in the `data/` folder
- A log file will be saved in the `logs/` folder
- A success message will be printed to the console

---

## API Reference

TfL BikePoint API documentation:  
https://api.tfl.gov.uk/swagger/ui/#!/BikePoint/BikePoint_GetAll

---

## Error Handling

- HTTP status codes outside the successful range trigger a retry
- Requests time out after 10 seconds
- All errors are logged for troubleshooting

---

## Future Improvements

- Add environment variable support for API credentials
- Schedule automated runs using cron or Task Scheduler
- Store data in CSV format or a database
- Add unit tests and CI/CD integration

---

## License

This project uses public TfL API data and is intended for educational and non-commercial use.  
Please refer to TfL’s API terms and conditions for usage guidelines.
```

