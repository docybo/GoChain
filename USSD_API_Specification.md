# 📡 GoChain – USSD API Specification

> Enables blockchain access (check balance, send tokens, stake, vote) via USSD for basic phones.

---

## ✅ Endpoint

**POST** `/ussd`

### Headers:

```
Content-Type: application/x-www-form-urlencoded
```

### Request Body (Africa’s Talking format):

| Field         | Type   | Description                            |
| ------------- | ------ | -------------------------------------- |
| `sessionId`   | string | Unique ID per session                  |
| `serviceCode` | string | USSD short code (e.g., `*123#`)        |
| `phoneNumber` | string | User's MSISDN (e.g., `+2250701234567`) |
| `text`        | string | User input as a concatenated string    |

---

## 🧾 Sample Request (User starts session):

```bash
POST /ussd
Content-Type: application/x-www-form-urlencoded

sessionId=12345&serviceCode=*123#&phoneNumber=+2250701234567&text=
```

---

## 📋 Menu Structure

```plaintext
CON Welcome to GoChain 🌍
1. Check Balance
2. Send Tokens
3. Stake Tokens
4. Vote
```

---

### 1. Check Balance

```plaintext
User Input: 1

Response:
END Balance: 7.25 GOX
```

---

### 2. Send Tokens

```plaintext
Step 1: text = 2  
→ CON Enter recipient phone or address:

Step 2: text = 2*+2250709998888  
→ CON Enter amount to send:

Step 3: text = 2*+2250709998888*5  
→ END Sending 5 GOX to +2250709998888...
```

---

### 3. Stake Tokens

```plaintext
text = 3  
→ CON Enter amount to stake:

text = 3*20  
→ END You have staked 20 GOX. You'll start earning rewards next epoch.
```

---

### 4. Vote (Governance)

```plaintext
text = 4  
→ CON Proposal #1: "Fund rural kiosks"  
Vote:  
1. Yes  
2. No

text = 4*1  
→ END Vote recorded. Thank you for participating in governance!
```

---

## 🛠 Backend Logic Overview

| Action        | Logic                                      |
| ------------- | ------------------------------------------ |
| Balance Check | Call `api.query.system.account(address)`   |
| Send Tokens   | Sign tx via private key / custodial wallet |
| Stake Tokens  | Call `api.tx.staking.bond(...)`            |
| Vote          | Call `api.tx.democracy.vote(...)`          |

---

## 🔐 Security Notes

* Sessions are stateless; phone number maps to a custodial key pair (for now).
* PIN/OTP auth can be added in later iterations.
* Supports **offline queuing** for remote sync.

---

## 🧪 Sample cURL Test

```bash
curl -X POST http://localhost:3000/ussd \
     -d "sessionId=abc123&serviceCode=*123#&phoneNumber=+2250701234567&text=1"
```

Response:

```
END Balance: 7.25 GOX
```
