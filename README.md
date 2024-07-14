# URL_SHORTENER

This project is a URL shortener application built with FastAPI. It allows users to shorten long URLs, and manage them through a set of administrative endpoints, and forward to the original URLs.

## Getting Started

Follow these steps to set up your environment:

### 1. Clone the Repository

To get started, clone this repository to your local machine:

```bash
git clone https://github.com/erfanghorbanee/url_shortener.git
cd url_shortener
```

### 2. Install Dependencies

Run the following command to install the necessary dependencies:

```bash
pip install -m requirements.txt
```

### 3. Set Up Environment Variables

We use environment variables to manage configuration and secrets. You'll find a file in the repository named `.env_sample`. This file contains all the required environment variables with placeholder values.

**Here’s how to set up your `.env` file:**

- Copy the `.env_sample` file and rename it to `.env`:

    ```bash
    cp .env_sample .env
    ```

- Open the `.env` file and replace all placeholder values with your actual data. For example:

    ```plaintext
    ENV_NAME="YOUR_ENV_NAME"
    BASE_URL="http://127.0.0.1:8000"
    DB_URL="sqlite:///./shortener.db"
    ```

### 4. Start the Application

Once you have configured your environment variables, you can start the application by running:

```bash
uvicorn shortener_app.main:app --reload
```

Your application should now be running on `http://localhost:8000`.

## Endpoints

| Endpoint             | HTTP Verb | Request Body       | Action                                                      |
|----------------------|-----------|--------------------|-------------------------------------------------------------|
| /                    | GET       |                    | Returns a `Hello, World!` string                             |
| /url                 | POST      | Your target URL    | Shows the created `url_key` with additional info, including a `secret_key` |
| /{url_key}           | GET       |                    | Forwards to your target URL                                  |
| /admin/{secret_key}  | GET       |                    | Shows administrative info about your shortened URL           |
| /admin/{secret_key}  | DELETE    | Your secret key    | Deletes your shortened URL                                   |

## Contributing

If you have suggestions or issues, please open an issue through GitHub. All contributions are welcomed.

## TODO

- Custom URL key: Let your users create custom URL keys instead of a random string.
- Peek URL: Create an endpoint for your users to check which target URL is behind a shortened URL.
- Graceful Forward: Check if the website exists before forwarding.

## Acknowledgements

This project was inspired by and built upon the tutorial from [Real Python](https://realpython.com/). For more details, you can check out the original tutorial [here](https://realpython.com/build-a-python-url-shortener-with-fastapi/).
