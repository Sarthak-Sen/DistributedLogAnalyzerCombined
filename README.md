# DistributedLogAnalyzerCombined

A combined repo for Frontend and Backend of Distributed Log Analyzer

## Working Link: [Link](https://log-analyzer-frontend-one.vercel.app/)

Built a distributed log analysis backend in ASP.NET Core (.NET 8) — JWT-authenticated uploads are chunked and queued in Redis, processed in parallel by 4 background workers with distributed locking, with results passed back via an in-process Channel to a gRPC-Web server-streaming service that delivers real-time anomaly detection to the browser, persisted to MongoDB Atlas.


## FrontEnd Repo: [Link](https://github.com/Sarthak-Sen/log-analyzer-frontend)

A React-based frontend that provides search, filtering, pagination, and result display for the movie catalogue.

#### Tech Stack:-

1. React 18 + TypeScript
2. Vite
3. CSS Modules

#### Local Setup:-

1. Clone the repository
2. Run npm install
3. Create .env.local in the project root
```
   VITE_API_BASE_URL=http://localhost:5001/api
   VITE_OMDB_API_KEY=your_omdb_key
```
4. npm run dev

#### External API:-

OMDb API for poster fetching


## Backend Repo: [Link](https://github.com/Sarthak-Sen/LogAnalyzerBackend)

An ASP.NET Core Web API that provides search and filtering endpoints and ranks results using ML.NET.

#### TechStack:-
1. .NET 8 (ASP.NET Core Web API)
2. Entity Framework Core
3. PostgreSQL (Neon)
4. ML.NET (Regression – FastTree)
5. Docker
6. Hosted on Render

#### Core Features:-
1. Filtering based on genre, rating, etc
2. Pagination support
3. ML-based ranking of filtered results

#### Local Setup:-
1. Clone the repository
2. Run dotnet restore
3. Run dotnet run

#### Data Source:-
1. MovieLens dataset with 9,700 movies [Link](https://files.grouplens.org/datasets/movielens/ml-latest-small-README.html)
2. Uses collaborative filtering to find books liked by similar users

## Deployment Architecture:-
```
React (Vercel)
↓
ASP.NET Core API (Docker, Render)
↓
PostgreSQL (Neon)
↓
ML.NET ranking model (rankingModel.zip)
```
