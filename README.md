# Gate.io Public API Connector python
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This is a lightweight library that works as a connector to [Gate.io public API](https://www.gate.io/docs/developers/apiv4)

- Supported APIs:
    - `APIv4
    - spot, margin and futures trading
- Inclusion of test cases and examples
- Customizable base URL, request timeout and HTTP proxy
- Response metadata can be displayed

## Installation

```bash
pip install gateio-connector
```

## Documentation

[https://gateio-connector.readthedocs.io](https://gateio-connector.readthedocs.io)

## RESTful APIs

Usage examples:
```python
from gateio.spot import Spot 

client = Spot()

# Get server timestamp
print(client.time())
# Get klines of BTCUSDT at 1m interval
print(client.klines("BTCUSDT", "1m"))
# Get last 10 klines of BNBUSDT at 1h interval
print(client.klines("BNBUSDT", "1h", limit=10))

# api key/secret are required for user data endpoints
client = Spot(key='<api_key>', secret='<api_secret>')

# Get account and balance information
print(client.account())

# Post a new order
params = {
    'symbol': 'BTCUSDT',
    'side': 'SELL',
    'type': 'LIMIT',
    'timeInForce': 'GTC',
    'quantity': 0.002,
    'price': 9500
}

response = client.new_order(**params)
print(response)
```
Please find `examples` folder to check for more endpoints.

### Base URL

If `base_url` is not provided, it defaults to `https://api.gateio.ws/api/v4`.<br/>

### Optional parameters

PEP8 suggests _lowercase with words separated by underscores_, but for this connector,
the methods' optional parameters should follow their exact naming as in the API documentation.

### Proxy

Proxy is supported.

```python
from gateio.spot import Spot as Client

proxies = { 'https': 'http://1.2.3.4:8080' }

client= Client(proxies=proxies)
```

## Contributing

Contributions are welcome.<br/>
If you've found a bug within this project, please open an issue to discuss what you would like to change.<br/>