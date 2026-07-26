# Poster Design Competition Management System

A full-stack competition management platform built with **Spring Boot 3 + Vue 3**, designed for university poster design contests. It provides end-to-end management capabilities including competition publishing, team registration, submission handling, judge review, and results announcement.

## Feature Modules

| Module | Description |
|------|------|
| Competition Management | Competition publishing, registration deadlines, status workflow |
| Team Management | Team formation and registration, member invitations |
| Submission Management | Poster upload, showcase, and likes |
| Judge Management | Judge assignment, score entry |
| Announcements / News | Event notifications and news publishing |
| Awards / Certificates | Award configuration, automatic certificate generation |
| User Center | Registration & login (JWT), SMS verification codes, profile management |
| Admin Panel | Full CRUD access to all data for administrators |

## Tech Stack

### Backend (`poster-design-springboot`)

- **Java 17** + **Spring Boot 3.1.5**
- **MyBatis-Plus** data access layer
- **MySQL 8** relational database
- **Redis Sentinel** caching and session management
- **MinIO** object storage (poster images)
- **Alibaba Cloud OSS / SMS** cloud storage and SMS services
- **JWT** stateless authentication
- **Knife4j (OpenAPI 3)** API documentation

### Frontend (`poster-design-vue`)

- **Vue 3** + **Vite 7**
- **Element Plus** UI component library
- **Pinia** state management (with persistence)
- **Vue Router 4** routing
- **ECharts / Vue-ECharts** data visualization
- **GSAP + Swiper + fullpage.js** animations and full-page scrolling
- **Tailwind CSS** styling

## Project Structure

```
poster_design/
├── poster-design-springboot/   # Backend Maven multi-module project
│   ├── common/                 # Common components (config, interceptors, utilities)
│   ├── model/                  # Data models (Entity, DTO, VO)
│   └── server/                 # Business logic and API layer
├── poster-design-vue/          # Frontend Vue 3 project
│   └── src/
│       ├── views/              # Page views
│       ├── apis/               # API request wrappers
│       ├── stores/              # Pinia state
│       └── router/             # Route configuration
└── sql/
    └── poster_design.sql       # Database initialization script
```

## Quick Start

### Prerequisites

- JDK 17+
- Maven 3.8+
- Node.js 18+
- MySQL 8+
- Redis (Sentinel or standalone mode)
- MinIO (optional, for local file storage)

### Database Initialization

```sql
CREATE DATABASE poster_design CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
-- Then run sql/poster_design.sql
```

### Backend Configuration

Copy the configuration template and fill in the real connection info (do not commit this to version control):

```bash
cp poster-design-springboot/server/src/main/resources/application.yaml \
   poster-design-springboot/server/src/main/resources/application-local.yaml
```

Configure the following environment variables (or edit the corresponding values directly) in `application-local.yaml`:

| Environment Variable | Description |
|----------|------|
| `DB_HOST` / `DB_PORT` | Database host and port |
| `DB_USERNAME` / `DB_PASSWORD` | Database credentials |
| `REDIS_HOST` / `REDIS_PASSWORD` | Redis connection info |
| `MINIO_ENDPOINT` / `MINIO_ACCESS_KEY` / `MINIO_SECRET_KEY` | MinIO connection info |

### Run the Backend

```bash
cd poster-design-springboot
mvn spring-boot:run -pl server
```

### Run the Frontend

```bash
cd poster-design-vue
npm install
npm run dev
```

## License

[MIT](LICENSE)
