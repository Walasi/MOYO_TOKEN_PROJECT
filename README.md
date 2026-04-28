# Moyo Token – Network-Verified Identity Layer for Financial Inclusion

Moyo Token prevents SIM swap fraud in humanitarian aid and UBI programs by using Nokia's CAMARA APIs (SIM Swap Detection, Location Verification, Number Verification) to approve transactions, combined with a transparent blockchain ledger.

## Problem
In Sub‑Saharan Africa, mobile money fraud—especially SIM swap scams—causes billions in losses. Beneficiaries of social programs often lose their monthly stipends when fraudsters intercept OTPs.

## Solution
Moyo Token acts as a **network‑aware smart contract**. Before releasing funds on the blockchain, our backend calls Nokia's network APIs to:
- Verify the SIM card hasn't been recently swapped.
- Confirm the user is at their registered location.
- Silently authenticate the phone number without any SMS OTP.

Only if all checks pass is a token (or UBI voucher) issued on the Stellar blockchain (demo uses mock TX).

## Demo Video
[![Moyo Token Demo](http://img.youtube.com/vi/VIDEO_ID/0.jpg)](https://youtu.be/VIDEO_ID)
*Click the thumbnail to watch a 2‑minute walkthrough.*

## Architecture
![Architecture Diagram](docs/architecture.png)

## Tech Stack
- **Backend:** Python (FastAPI), mock Nokia APIs, Stellar testnet SDK (optional)
- **Frontend:** HTML, CSS, JavaScript (Vanilla)
- **Blockchain:** Stellar testnet (or mock for reliability)
- **Database:** Supabase (planned for logging)
- **GSMA Sandbox:** Tested SIM Swap API (see screenshot in `docs/`)

## Features
- Silent authentication (Number Verification)
- SIM swap detection and block
- Location verification
- Self‑service recovery after a SIM swap using a secret word
- Mock blockchain transaction for demo reliability
- Clear, mobile‑friendly UI

## How to Run Locally
```bash
# Backend (from project root)
cd moyo-token-prototype
pip install -r requirements.txt
uvicorn backend.main:app --reload

# Frontend (in another terminal)
cd frontend
python -m http.server 5500
