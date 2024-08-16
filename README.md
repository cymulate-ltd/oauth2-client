# Cymulate OAuth2 Client

A Python client for OAuth2 authentication with the Cymulate API. This library simplifies the process of authenticating with the Cymulate API using OAuth2, managing tokens, and making secure requests effortlessly.

## Installation

To install the package, use `pip`:

```bash
pip install cymulate-oauth2-client 
```

### Requirements

- **Python Version:** This client supports Python **3.12** and above. Ensure you have Python 3.12 or a later version installed to use this package.

## Usage

Below is an example of how to use the `CymulateOAuth2Client` class to authenticate with the Cymulate API, make secure requests, and manage tokens.

```python
from cymulate_oauth2_client import CymulateOAuth2Client
from typing import Dict, Any

def main() -> None:
    """
    Initialize the Cymulate OAuth2 client and demonstrate making
    authenticated API requests to secure endpoints.
    """
    
    # Instantiate the OAuth2 client with your Cymulate credentials and API base URL
    client: CymulateOAuth2Client = CymulateOAuth2Client(
        client_id='your_client_id',         # Your Cymulate OAuth2 client_id
        client_secret='your_client_secret', # Your Cymulate OAuth2 client_secret
        base_url='https://api.cymulate.com' # The Cymulate API base URL (adjust based on your region)
    )

    try:
        # Example 1: Perform a GET request to a secure endpoint
        response: Dict[str, Any] = client.get('/secure-endpoint')
        print("GET response:", response)

        # Example 2: Perform a POST request to a secure endpoint
        # Uncomment the lines below to send a POST request
        # data = {'key': 'value'}
        # response = client.post('/secure-endpoint', json=data)
        # print("POST response:", response)

    except Exception as e:
        print(f"An error occurred while making the request: {str(e)}")

if __name__ == "__main__":
    main()
```

### API URL Configuration

Cymulate provides different API endpoints depending on your region. Ensure you use the correct base URL for your environment:

- **US:** `https://us-api.cymulate.com`
- **EU:** `https://api.cymulate.com`

For detailed API documentation, refer to the appropriate link based on your region:

- **US API Documentation:** [https://us-api.cymulate.com/docs](https://us-api.cymulate.com/docs)
- **EU API Documentation:** [https://api.cymulate.com/docs](https://api.cymulate.com/docs)

### Key Methods

- `get(url, **kwargs)`: Sends a GET request to a secure resource.
- `post(url, data=None, json=None, **kwargs)`: Sends a POST request to a secure resource.
- `put(url, data=None, **kwargs)`: Sends a PUT request to a secure resource.
- `delete(url, **kwargs)`: Sends a DELETE request to a secure resource.

### Exception Handling

This client handles common HTTP exceptions such as connection errors, timeouts, and authentication errors. It also automatically refreshes or obtains a new token if the current token is expired or invalid, retrying the request up to the configured number of retries.

### Logging

The client leverages Python’s built-in logging module to log important events, such as token refreshes, errors, and warnings. Logs can be configured to suit your needs.

## License

This project is licensed under the MIT License. For more information, see the [LICENSE](LICENSE) file.

## Contributing

Contributions are welcome! If you have suggestions, find a bug, or want to improve the code, please open an issue or submit a pull request.

## Contact

For any inquiries or support, please contact Cymulate at [support@cymulate.com](mailto:support@cymulate.com).
