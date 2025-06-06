# Примеры кода для API Tonguard

## Аутентификация

### Получение JWT токена

```python
import requests

def get_auth_token(email, password):
    url = "https://api.tonguard.org/v1/auth/login"
    payload = {
        "email": email,
        "password": password
    }
    response = requests.post(url, json=payload)
    return response.json()["token"]
```

```javascript
async function getAuthToken(email, password) {
    const response = await fetch('https://api.tonguard.org/v1/auth/login', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            email: email,
            password: password
        })
    });
    const data = await response.json();
    return data.token;
}
```

## Получение оценки риска кошелька

### Python

```python
import requests

def get_wallet_risk_score(wallet_address, token):
    url = "https://api.tonguard.org/v2/reports/wallet_risk_score"
    headers = {
        "Authorization": f"Bearer {token}"
    }
    params = {
        "wallet_address": wallet_address
    }
    response = requests.get(url, headers=headers, params=params)
    return response.json()
```

### JavaScript

```javascript
async function getWalletRiskScore(walletAddress, token) {
    const response = await fetch(
        `https://api.tonguard.org/v2/reports/wallet_risk_score?wallet_address=${walletAddress}`,
        {
            headers: {
                'Authorization': `Bearer ${token}`
            }
        }
    );
    return await response.json();
}
```

## Мониторинг кошельков

### Добавление кошелька в мониторинг

```python
import requests

def add_wallet_to_monitoring(wallet_address, rule_id, token):
    url = "https://api.tonguard.org/v1/monitoring/address_under_rule"
    headers = {
        "Authorization": f"Bearer {token}",
        "Content-Type": "application/json"
    }
    payload = {
        "wallet_address": wallet_address,
        "rule_id": rule_id
    }
    response = requests.post(url, headers=headers, json=payload)
    return response.json()
```

### JavaScript

```javascript
async function addWalletToMonitoring(walletAddress, ruleId, token) {
    const response = await fetch('https://api.tonguard.org/v1/monitoring/address_under_rule', {
        method: 'POST',
        headers: {
            'Authorization': `Bearer ${token}`,
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            wallet_address: walletAddress,
            rule_id: ruleId
        })
    });
    return await response.json();
}
```

## Визуализация транзакций

### Получение графа транзакций

```python
import requests

def get_transactions_graph(wallet_address, token):
    url = "https://api.tonguard.org/v1/visualizer/get_transactions_graph"
    headers = {
        "Authorization": f"Bearer {token}"
    }
    params = {
        "wallet_address": wallet_address
    }
    response = requests.get(url, headers=headers, params=params)
    return response.json()
```

### JavaScript

```javascript
async function getTransactionsGraph(walletAddress, token) {
    const response = await fetch(
        `https://api.tonguard.org/v1/visualizer/get_transactions_graph?wallet_address=${walletAddress}`,
        {
            headers: {
                'Authorization': `Bearer ${token}`
            }
        }
    );
    return await response.json();
}
```

## Обработка ошибок

### Python

```python
import requests
from requests.exceptions import RequestException

def handle_api_request(url, method="GET", headers=None, params=None, json=None):
    try:
        response = requests.request(method, url, headers=headers, params=params, json=json)
        response.raise_for_status()
        return response.json()
    except RequestException as e:
        if response.status_code == 401:
            raise Exception("Ошибка аутентификации. Проверьте ваш токен.")
        elif response.status_code == 404:
            raise Exception("Ресурс не найден.")
        else:
            raise Exception(f"Произошла ошибка: {str(e)}")
```

### JavaScript

```javascript
async function handleApiRequest(url, options = {}) {
    try {
        const response = await fetch(url, options);
        if (!response.ok) {
            if (response.status === 401) {
                throw new Error('Ошибка аутентификации. Проверьте ваш токен.');
            } else if (response.status === 404) {
                throw new Error('Ресурс не найден.');
            }
            throw new Error(`HTTP ошибка! статус: ${response.status}`);
        }
        return await response.json();
    } catch (error) {
        console.error('Ошибка при выполнении запроса:', error);
        throw error;
    }
}
``` 