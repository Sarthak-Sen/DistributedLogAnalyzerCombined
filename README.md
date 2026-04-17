# DistributedLogAnalyzerCombined

A combined repo for Frontend and Backend of Distributed Log Analyzer

## Working Link: [Link](https://log-analyzer-frontend-one.vercel.app/)

Built a distributed log analysis backend in ASP.NET Core (.NET 8) — JWT-authenticated uploads are chunked and queued in Redis, processed in parallel by 4 background workers with distributed locking, with results passed back via an in-process Channel to a gRPC-Web server-streaming service that delivers real-time anomaly detection to the browser, persisted to MongoDB Atlas.


## FrontEnd Repo: [Link](https://github.com/Sarthak-Sen/log-analyzer-frontend)

A React-based frontend that provides real-time log analysis using React, TypeScript, and gRPC-Web that streams live anomaly detection results from a distributed backend as files are processed.

#### Tech Stack:-

1. React + TypeScript
2. Vite
3. CSS Modules
4. gRPC-Web (grpc-web)
5. Protocol Buffers (protobufjs)
6. Deployed on Vercel

#### Local Setup:-

1. Clone the repository
2. Run npm install
3. Create .env.local in the project root
```
   VITE_BACKEND_URL=http://localhost:5001/api
```
4. npm run dev


## Backend Repo: [Link](https://github.com/Sarthak-Sen/LogAnalyzerBackend)

An ASP.NET Core gRPC-Web backend that receives log uploads, distributes processing across background workers via Redis, and streams real-time anomaly detection results to the browser.

#### TechStack:-
1. .NET 8 (ASP.NET Core)
2. gRPC-Web (Grpc.AspNetCore.Web)
3. Redis (Upstash)
4. MongoDB (Atlas)
5. JWT Authentication
6. Docker
7. Hosted on Render

#### Core Features:-
1. Chunked log upload via REST endpoints
2. Redis task queue with distributed locking across 4 background workers
3. Real-time anomaly detection (ERROR_SPIKE, HIGH_LATENCY, LOGIN_FAILURE)
4. gRPC-Web server streaming for live results
5. Persistent storage of jobs, logs, and anomalies in MongoDB

#### Local Setup:-
1. Clone the repository
2. Add appsettings.json with MongoDB, Redis, and JWT config
3. Run dotnet restore
4. Run dotnet run

#### Log Format:-
Fields: timestamp | level (INFO/WARN/ERROR/FATAL) | service | message | duration_ms
Example: 2024-01-15 10:23:41.234 INFO UserService User logged in user_id=4821 duration_ms=120

## Deployment Architecture:-
```
Browser (React)
↓ REST (chunk upload)
ASP.NET Core API (Docker, Render)
↓ Redis Task Queue (Upstash)
Background Workers (x4)
↓ gRPC-Web Server Stream
Browser (React)
↓
MongoDB Atlas
```

## Demo:-


