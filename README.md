<p align="center"><img src="https://raw.githubusercontent.com/zumcoin/zum-assets/master/ZumCoin/zumcoin_logo_design/3d_green_lite_bg/ZumLogo_800x200px_lite_bg.png" width="400"></p>

# ZUM Services Python API Interface

This wrapper allows you to easily interact with the [ZUM Services](https://zum.services) 1.0.1 API to quickly develop applications that interact with the [ZumCoin](https://zumcoin.org) Network.


# Table of Contents

1. [Installation](#installation)
2. [Intialization](#intialization)
3. [Documentation](#documentation)
  1. [Methods](#methods)

# Installation

```bash
pip install zumservices-api-py
```

# Intialization

```python
import os
from ZUMservices import ZS

os.environ["ZUM_SERVICES_TOKEN"] = "eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoieW8iLCJhcHBJZCI6MjAsInVzZXJJZCI6MiwicGVybWlzc2lvbnMiOlsiYWRkcmVzczpuZXciLCJhZGRyZXNzOnZpZXciLCJhZGRyZXNzOmFsbCIsImFkZHJlc3M6c2NhbiIsImFkZHJlc3M6ZGVsZXRlIiwidHJhbnNmZXI6bmV3IiwidHJhbnNmZXI6dmlldyJdLCJpYXQiOjE1Mzk5OTQ4OTgsImV4cCI6MTU3MTU1MjQ5OCwiYXVkIjoiZ2FuZy5jb20iLCJpc3MiOiJUUlRMIFNlcnZpY2VzIiwianRpIjoiMjIifQ.KkKyg18aqZfLGMGTnUDhYQmVSUoocrr4CCdLBm2K7V87s2T-3hTtM2MChJB2UdbDLWnf58GiMa_t8xp9ZjZjIg"

os.environ["ZUM_SERVICES_TIMEOUT"] = 2000

```

Generate a token with the ZUM Services [Dashboard](https://zum.services) and store it as the variable ``ZUM_SERVICES_TOKEN`` in your os environment along with ``ZUM_SERVICES_TIMEOUT`` if you wish the change the default timeout of 2000.



# Documentation

API documentation is available at https://zum.services/documentation


## Methods

### createAddress()
Create a new ZUM addresses

```python
ZS.createAddress()
```


### getAddress(address)
Get address details by address
```python
ZS.getAddress("Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC")
```


### deleteAddress(address)
Delete a selected ZUM address

```python
ZS.deleteAdddress("Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC")
```


### getAddresses()
View all addresses.

```python
ZS.getAddresses()
```


### scanAddress(address, blockIndex)
Scan an address for transactions between a 100 block range starting from the specified blockIndex.

```python
ZS.scanAddress("Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC", 899093)
```


### getAddressKeys(address)
Get the public and secret spend key of an address.

```python
ZS.getAddressKeys("Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC")
```


### integrateAddress(address, paymentId)
Create an integrated address with an address and payment ID.

```python
ZS.integrateAddress("Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC", "7d89a2d16365a1198c46db5bbe1af03d2b503a06404f39496d1d94a0a46f8804")
```


### getIntegratedAddresses(address)
Get all integrated addresses by address.

```python
ZS.getIntegratedAddresses("Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC")
```


### getFee(amount)
Calculate the ZUM Services fee for an amount specified in ZUM with two decimal points.

```python
ZS.getFee(1.23)
```


### createTransfer(sender, receiver, amount, fee, paymentId, extra)
Send a ZUM transaction with an address with the amount specified two decimal points.

```python
ZS.createTransfer(
  "Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC",
  "Zum1yhbRwHsXj19c1hZgFzgxVcWDywsJcDKURDud83MqMNKoDTvKEDf6k7BoHnfCiPbj4kY2arEmQTwiVmhoELPv3UKhjYjCMcm",
  1234.56,
  1.23,
  "7d89a2d16365a1198c46db5bbe1af03d2b503a06404f39496d1d94a0a46f8804",
  "3938f915a11582f62d93f82f710df9203a029f929fd2f915f2701d947f920f99"
)
```
#### You can leave the last two fields (paymentId and extra) blank.


### getTransfer(address)
Get a transaction details specified by transaction hash.

```python
ZS.getTransfer("EohMUzR1DELyeQM9RVVwpmn5Y1DP0lh1b1ZpLQrfXQsgtvGHnDdJSG31nX2yESYZ")
```


### getWallet()
Get wallet container info and health check.

```python
ZS.getWallet()
```


### getStatus()
Get the current status of the ZUM Services infrastructure.

```python
ZS.getStatus()
```



# License

```
Copyright (c) 2019 ZumCoin Development Team

Please see the included LICENSE file for more information.
```
