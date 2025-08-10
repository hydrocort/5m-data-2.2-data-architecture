# Redis Environment Setup Instructions

## Redis Credential Management Update

- Redis credentials are now stored securely in a `.env` file at the project root.
- The code uses the `python-dotenv` library to load these credentials.
- For reference, a `.env_template` file is provided in the project root. Copy `.env_template` to `.env` and fill in your actual credentials:

  ```
  REDIS_HOST=your_redis_host
  REDIS_PORT=your_redis_port
  REDIS_USERNAME=your_redis_username
  REDIS_PASSWORD=your_redis_password
  ```

- The Python code now loads credentials using:
  ```python
  from dotenv import load_dotenv
  import os
  load_dotenv()
  r = redis.Redis(
      host=os.getenv('REDIS_HOST'),
      port=int(os.getenv('REDIS_PORT')),
      username=os.getenv('REDIS_USERNAME'),
      password=os.getenv('REDIS_PASSWORD'),
      decode_responses=True
  )
  ```
- This approach keeps sensitive information out of your code and supports best practices for secret management.

## Install Required Library

To install the required library using conda, run:

```bash
conda install -c conda-forge python-dotenv
```
