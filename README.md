# Inventory Management

Inventory and warehouse management starter based on the supplied system design.

## Architecture

- `frontend/`: Next.js, React, and TypeScript dashboard.
- `backend/`: Java 17 and Spring Boot REST API, organized into config, controller, DTO, model, repository, and service packages.
- PostgreSQL is the planned persistence store. The backend reads connection settings from environment variables and defaults to a local development database.
- The API is intended to grow around products, warehouses and locations, receipts, deliveries, transfers, adjustments, stock ledger, authentication, and dashboard summaries.
- Authentication is planned with Spring Security and JWT; inventory mutations should be recorded in the stock ledger and execute transactionally.

## Run locally

Start PostgreSQL, then run the API from `backend/` with `mvn spring-boot:run`. Start the web app from `frontend/` with `npm install` followed by `npm run dev`.

The API listens on port `8080`; the frontend listens on port `3000`.