# CampusIQ – College Discovery & Decision Platform

## Project Overview

CampusIQ is a production-grade MVP that helps students discover colleges, compare institutions, and make informed admission decisions. The platform provides real-time search and filtering, detailed college information, college comparison tools, and a predictor system for admission guidance.

Additionally, CampusIQ includes an AI-powered College Advisor built using the Claude API for personalized recommendations and Q&A.

---

# Features Implemented

## 1.  College Listing + Search

### Functionality

* Display college cards with:

  * College Name
  * Location
  * Annual Fees
  * Rating
  * Placement Percentage
  * Average Package
* Live search by:

  * College Name
  * City
* Filters:

  * College Type

    * Engineering
    * Management
    * Liberal Arts
  * State
  * Fee Range
* Sorting Options:

  * Highest Rating
  * Placement Percentage
  * Fees (Low to High)
  * Fees (High to Low)

### Dataset

The platform contains 12 Indian colleges including:

* IIT Delhi
* IIT Bombay
* IIT Madras
* NIT Trichy
* BITS Pilani
* IIIT Hyderabad
* IIM Ahmedabad
* IIM Bangalore
* Ashoka University
* VIT University
* SRM University
* KL University

---

## 2.  College Detail Page

### Overview Section

Displays:

* College Name
* Location
* Fees
* Rating
* Placement Percentage
* Average Package
* Highest Package

### Tabs

#### Overview

* College description
* Key highlights

#### Courses

* Courses offered
* Program duration

#### Placements

* Placement percentage
* Average package
* Highest package
* Top recruiters

#### Reviews

* Student reviews
* Ratings and feedback

### Navigation

* Proper page routing
* Back navigation support

---

## 3.  Compare Colleges

### Functionality

Students can compare up to three colleges simultaneously.

### Comparison Metrics

* Location
* College Type
* Annual Fees
* Rating
* Placement Percentage
* Average Package
* Highest Package
* Available Courses
* Top Recruiters
* Admission Difficulty

### Features

* Floating compare bar
* Add or remove colleges dynamically
* Best-performing metrics highlighted automatically

---

## 4.  JEE Predictor Tool

### Supported Exams

* JEE Advanced
* JEE Main

### Inputs

* Exam Name
* Rank

### Outputs

Recommended colleges with:

* Admission probability
* Cutoff rank
* Annual fees
* Average package

### Admission Probability Categories

#### High Chance

Rank comfortably meets cutoff.

#### Medium Chance

Rank is close to cutoff.

#### Low Chance

Rank slightly exceeds cutoff.

### Prediction Logic

The system uses rule-based rank cutoff matching stored in the dataset.

Example:

JEE Advanced Rank: 1500

Results:

* IIT Bombay
* IIT Delhi
* IIT Madras

JEE Main Rank: 25000

Results:

* NIT Trichy
* VIT University
* SRM University

---

##  Bonus Feature: AI College Advisor

CampusIQ includes a Claude-powered AI assistant.

### Capabilities

* Answers questions about:

  * Fees
  * Placements
  * Courses
  * Best colleges for a rank
  * College comparisons
* Uses the internal college dataset as context
* Provides personalized recommendations

### Example Questions

* Which college has the highest placements?
* Which college should I choose for JEE rank 15000?
* Compare IIT Delhi and BITS Pilani.
* Which colleges have the lowest fees?

---

# Technology Stack

## Frontend

* React.js
* Tailwind CSS
* React Hooks
* Context API

## Backend

* Node.js
* Express.js
* REST APIs

## Database

* PostgreSQL

## AI Integration

* Claude API

## Deployment

### Frontend

* Vercel

### Backend

* Render

### Database

* PostgreSQL (Neon or Render)

---

# Project Structure

```
campusiq/

├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── hooks/
│   │   ├── context/
│   │   ├── services/
│   │   ├── data/
│   │   └── App.jsx
│
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── models/
│   │   └── server.ts
│
├── database/
│   ├── schema.sql
│   └── seed.sql
│
├── .env
├── README.md
└── package.json
```

---

# Database Schema

## Colleges Table

| Field               | Type    |
| ------------------- | ------- |
| id                  | Integer |
| name                | String  |
| city                | String  |
| state               | String  |
| type                | String  |
| fees                | Integer |
| rating              | Float   |
| placementPercentage | Integer |
| averagePackage      | Float   |
| highestPackage      | Float   |
| description         | Text    |

---

## Courses Table

| Field      | Type    |
| ---------- | ------- |
| id         | Integer |
| collegeId  | Integer |
| courseName | String  |
| duration   | String  |

---

## Reviews Table

| Field       | Type    |
| ----------- | ------- |
| id          | Integer |
| collegeId   | Integer |
| studentName | String  |
| rating      | Integer |
| comment     | Text    |

---

# API Endpoints

## Get All Colleges

```
GET /api/colleges
```

## Search Colleges

```
GET /api/colleges?search=iit
```

## Filter by State

```
GET /api/colleges?state=Tamil Nadu
```

## Filter by Type

```
GET /api/colleges?type=Engineering
```

## Get College Details

```
GET /api/colleges/:id
```

## Compare Colleges

```
POST /api/compare
```

Request:

```json
{
  "collegeIds": [1, 2, 3]
}
```

## Predictor

```
POST /api/predict
```

Request:

```json
{
  "exam": "JEE Advanced",
  "rank": 1500
}
```

---

# Installation

## Clone Repository

```bash
git clone https://github.com/RAMYASRIBATTALA/campusiq.git
cd campusiq
```

---

## Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

Runs on:

```
http://localhost:3000
```

---

## Backend Setup

```bash
cd backend
npm install
npm run dev
```

Runs on:

```
http://localhost:5000
```

---

## Environment Variables

Create a `.env` file:

```env
DATABASE_URL=your_postgresql_url
CLAUDE_API_KEY=your_claude_api_key
PORT=5000
```

---

# Deployment

## Frontend

Deploy to Vercel.

Environment Variable:

```env
NEXT_PUBLIC_API_URL=https://your-backend.onrender.com
```

## Backend

Deploy to Render.

Environment Variables:

```env
DATABASE_URL=
CLAUDE_API_KEY=
PORT=5000
```

## Database

Deploy PostgreSQL using:

* Neon
* Render PostgreSQL

---

# Future Enhancements

* User Authentication
* Saved Colleges
* Saved Comparisons
* Discussion Forum
* Cutoff Trends Visualization
* AI-Powered Career Guidance
* College Recommendation Engine using Machine Learning

---

# Project Objective

CampusIQ simplifies the college selection process by enabling students to:

1. Discover colleges efficiently.
2. Explore detailed information.
3. Compare institutions side by side.
4. Predict admission opportunities.
5. Receive personalized guidance through AI.

Built with  using React, Node.js, PostgreSQL, Tailwind CSS, and Claude AI.
