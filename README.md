# Project Voltage - Team Score Tracking System

A real-time team scoring system with two frontend interfaces and a Flask backend.

## Architecture

- **BE** (Backend): Flask REST API running on port 5000
- **FE-User** (Control Interface): React + TypeScript + Chakra UI on port 3001
- **FE-Display** (Display Interface): React + TypeScript + Chakra UI on port 3002

## Features

- Real-time score tracking for two teams
- Separate control interface with increment buttons
- Live display interface with automatic score updates (polls every 1 second)
- RESTful API endpoints for score management

## Setup Instructions

### Backend (BE)

```bash
cd BE
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

Backend will run on: http://localhost:5000

### Frontend - Control Interface (FE-User)

```bash
cd FE-User
npm install
npm run dev
```

FE-User will run on: http://localhost:3001

### Frontend - Display Interface (FE-Display)

```bash
cd FE-Display
npm install
npm run dev
```

FE-Display will run on: http://localhost:3002

## Usage

1. Start the backend (BE) first
2. Start both frontends (FE-User and FE-Display)
3. Use FE-User (http://localhost:3001) to increment team scores using the "+" buttons
4. View FE-Display (http://localhost:3002) on a separate screen/monitor to see live score updates

## API Endpoints

### GET /api/scores
Get current scores for both teams

**Response:**
```json
{
  "team1": 0,
  "team2": 0
}
```

### POST /api/scores/increment
Increment score for a specific team

**Request body:**
```json
{
  "team": "team1"
}
```

**Response:**
```json
{
  "success": true,
  "team": "team1",
  "newScore": 1,
  "allScores": {
    "team1": 1,
    "team2": 0
  }
}
```

### POST /api/scores/reset
Reset all scores to zero

**Response:**
```json
{
  "success": true,
  "scores": {
    "team1": 0,
    "team2": 0
  }
}
```

## Technology Stack

- **Backend**: Flask, Flask-CORS
- **Frontend**: React, TypeScript, Vite, Chakra UI
- **Styling**: Chakra UI components with custom theming