# SOAP JSON to CSV Transformer

This Python script is designed to transform SOAP JSON-wrapped XML results into a tabular CSV format. It extracts the data section from the JSON, identifies the column names, and flattens the nested structure into a CSV file.

## Features

- **Extract Headers and Rows**: Recursively traverses the JSON structure to extract headers and corresponding data rows.
- **Find Data Section**: Identifies the relevant data section within the SOAP JSON response.
- **Flatten JSON**: Converts nested JSON into a flat structure suitable for tabular representation.
- **Generate CSV**: Outputs the transformed data into a CSV file.

## Prerequisites

- Python 3.x
- pandas library (`pip install pandas`)

## Usage

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name
   ```

2. **Install Dependencies**:
   ```bash
   pip install pandas
   ```

3. **Prepare Your SOAP JSON File**:
   - Place your SOAP JSON response file (e.g., `soap_response.json`) in the same directory as the script.

4. **Run the Script**:
   ```bash
   python transform_soap_json_to_csv.py
   ```

5. **Output**:
   - The script will generate a CSV file named `output_tabular.csv` in the same directory.

## Script Details

### Functions

- **`extract_headers_and_row(data, parent_key="", result=None)`**:
  - Recursively extracts headers and rows from the JSON data.
  - Parameters:
    - `data`: The JSON data to process.
    - `parent_key`: The key prefix for nested structures.
    - `result`: Dictionary to store the extracted data.
  - Returns: A dictionary or list of dictionaries containing the flattened data.

- **`find_data_section(response_json)`**:
  - Recursively searches for the data section within the SOAP JSON response.
  - Parameters:
    - `response_json`: The JSON response from the SOAP service.
  - Returns: The identified data section as a list.

- **`parse_soap_json(response_json)`**:
  - Parses the SOAP JSON response and extracts the data section.
  - Parameters:
    - `response_json`: The JSON response from the SOAP service.
  - Returns: A list of dictionaries containing the flattened data.

- **`load_local_json(file_path)`**:
  - Loads a JSON file from the local filesystem.
  - Parameters:
    - `file_path`: Path to the JSON file.
  - Returns: The loaded JSON data.

### Main Execution

- The script loads the SOAP JSON response from `soap_response.json`.
- It then processes the JSON to extract and flatten the data.
- Finally, it saves the transformed data into `output_tabular.csv`.

## Example

Given a SOAP JSON response like:

```json
{
  "Envelope": {
    "Body": {
      "Response": {
        "Result": [
          {"id": 1, "name": "John Doe", "address": {"city": "New York", "zip": "10001"}},
          {"id": 2, "name": "Jane Smith", "address": {"city": "Los Angeles", "zip": "90001"}}
        ]
      }
    }
  }
}
```

The script will produce a CSV file (`output_tabular.csv`) with the following content:

| id | name       | address.city | address.zip |
|----|------------|--------------|-------------|
| 1  | John Doe   | New York     | 10001       |
| 2  | Jane Smith | Los Angeles  | 90001       |

## Open in Colab

You can also run this script directly in Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/your-username/your-repo-name/blob/main/transform_soap_json_to_csv.py)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

## Acknowledgments

- Thanks to the pandas library for simplifying data manipulation in Python.

---

Feel free to customize this README to better fit your project's needs!
