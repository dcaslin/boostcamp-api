# Boostcamp API

An unofficial, asynchronous Python client for the [Boostcamp](https://www.boostcamp.app/) fitness app API. Modeled after the `monarchmoney` client, it provides access to workout data, training history, and program details.

## Features

- Asynchronous client built on `aiohttp`.
- Full lifting history retrieval.
- Program search and discovery.
- Dashboard statistics (streaks, total volume, muscle distribution).
- Session persistence with automatic re-authentication on token expiry.

## Requirements

- Python 3.8+
- `aiohttp>=3.8.0`

## Installation

```bash
pip install -e .
```

## Usage

```python
import asyncio
from boostcampapi import BoostcampAPI

async def main():
    api = BoostcampAPI()

    if not api.load_session():
        await api.login("you@example.com", "your_password")

    summary = await api.get_home_summary()
    print(f"Current streak: {summary['data']['week_streak']} weeks")

    history = await api.get_training_history()
    print(f"Logged {len(history['data'])} days of workouts")

asyncio.run(main())
```

## Authentication (Google/Apple Users)

If you sign in to Boostcamp with Google or Apple, set a password before using this API:

1. Go to the [Boostcamp login page](https://www.boostcamp.app/login).
2. Enter your email and click **Forgot Password?**.
3. Set a new password via the email link.
4. Use that email and password to authenticate.

## API Reference

See [BOOSTCAMP_API.md](./BOOSTCAMP_API.md) for the documented endpoints.

## Contributing

Contributions are welcome. Open a pull request to add endpoints or features.

## Credits

This project began as a fork of [Alex-Keyes/boostcamp-api](https://github.com/Alex-Keyes/boostcamp-api) and has since grown into a standalone repository.

## License

Released under the [MIT License](./LICENSE).

---

*Disclaimer: This is an unofficial project and is not affiliated with Boostcamp.*
