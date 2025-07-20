# replit.md

## Overview

Drawing Finder is a full-stack technical drawing management system built with modern web technologies. It provides secure access to engineering drawings with role-based permissions, advanced search capabilities, and comprehensive audit logging. The application is designed for engineering teams to efficiently manage, search, and access technical drawings.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Styling**: Tailwind CSS with shadcn/ui component library
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack React Query for server state management
- **Build Tool**: Vite for fast development and optimized builds

### Backend Architecture
- **Runtime**: Node.js with Express.js REST API
- **Database**: PostgreSQL with Drizzle ORM
- **Authentication**: Replit's OpenID Connect (OIDC) authentication
- **Session Management**: Express sessions with PostgreSQL storage
- **Development**: Hot module replacement with Vite middleware integration

### Data Storage Solutions
- **Primary Database**: PostgreSQL via Neon serverless
- **ORM**: Drizzle ORM with type-safe schema definitions
- **Session Storage**: PostgreSQL-backed session store
- **Schema Management**: Drizzle migrations in `migrations/` directory

## Key Components

### Authentication System
- **Provider**: Replit OIDC integration with automatic user provisioning
- **Session Management**: Secure HTTP-only cookies with PostgreSQL backing
- **Authorization**: Role-based access control (engineer, manager, admin)
- **User Management**: Automatic user creation on first login with profile sync

### Database Schema
- **Users**: Profile management with role-based permissions
- **Projects**: Organizational structure for drawings
- **Drawings**: Core entity with metadata, file information, and access controls
- **Access Logging**: Comprehensive audit trail for drawing access
- **Sessions**: Secure session persistence

### API Architecture
- **RESTful Design**: Clean endpoint structure with consistent error handling
- **Authentication Middleware**: Protected routes with user context
- **Data Validation**: Zod schema validation for all inputs
- **Error Handling**: Centralized error processing with appropriate HTTP status codes

### UI Components
- **Design System**: shadcn/ui components with consistent styling
- **Responsive Design**: Mobile-first approach with Tailwind CSS
- **Component Structure**: Modular components with clear separation of concerns
- **State Management**: React Query for server state, local state for UI

## Data Flow

1. **Authentication Flow**:
   - User accesses application → Redirected to Replit OIDC
   - Authentication success → User session created
   - Profile sync → Database user record updated/created
   - Role assignment → Access permissions determined

2. **Drawing Access Flow**:
   - User searches/browses → API validates permissions
   - Drawing selection → Access logging recorded
   - File serving → Role-based access control applied
   - Audit trail → All actions logged for compliance

3. **Data Management Flow**:
   - CRUD operations → Validation with Zod schemas
   - Database queries → Drizzle ORM with type safety
   - Response formatting → Consistent API responses
   - Error handling → Graceful degradation with user feedback

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: PostgreSQL database connection
- **drizzle-orm**: Type-safe database operations
- **express**: Web application framework
- **react**: Frontend library
- **@tanstack/react-query**: Server state management
- **tailwindcss**: Utility-first CSS framework

### Authentication Dependencies
- **openid-client**: OIDC authentication client
- **passport**: Authentication middleware
- **express-session**: Session management
- **connect-pg-simple**: PostgreSQL session store

### UI Dependencies
- **@radix-ui/***: Accessible UI primitives
- **class-variance-authority**: Component styling variants
- **lucide-react**: Icon library
- **wouter**: Lightweight routing

## Deployment Strategy

### Development Environment
- **Local Development**: Vite dev server with Express API
- **Hot Module Replacement**: Real-time code updates
- **Environment Variables**: `.env` file for local configuration
- **Database**: Development database with seeded data

### Production Build
- **Frontend**: Vite build to `dist/public/` directory
- **Backend**: ESBuild compilation to `dist/` directory
- **Static Assets**: Served by Express in production
- **Environment**: Production environment variables required

### Database Management
- **Migrations**: Drizzle migrations for schema changes
- **Seeding**: Initial data setup for development
- **Backup Strategy**: Regular database backups recommended
- **Connection Pooling**: Neon serverless handles connection management

### Deployment Requirements
- **Environment Variables**:
  - `DATABASE_URL`: PostgreSQL connection string
  - `SESSION_SECRET`: Session encryption key
  - `REPLIT_DOMAINS`: Allowed domains for OIDC
  - `ISSUER_URL`: OIDC issuer URL (defaults to Replit)
- **Node.js Version**: Compatible with ES modules
- **SSL**: HTTPS required for secure authentication
- **Session Storage**: PostgreSQL table for session persistence

## Changelog
- July 09, 2025. Enhanced authentication, added access history, user profiles, and improved search functionality
- July 07, 2025. Initial setup

## User Preferences

Preferred communication style: Simple, everyday language.