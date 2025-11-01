# Copilot Instructions for kb-app

## Project Overview
Knowledge base application similar to IT Glue - provides IT documentation and knowledge management with AI-powered assistance via Anthropic Claude. Currently in initial setup phase with core dependencies installed but minimal implementation.

## Tech Stack
- **Runtime**: Node.js
- **Framework**: Express.js 5.x
- **Language**: TypeScript (planned migration from JS)
- **AI Integration**: Anthropic SDK for intelligent search, documentation assistance
- **Environment**: dotenv for configuration
- **CORS**: Enabled for cross-origin requests

## Architecture & Patterns

### Entry Point
- `index.js` is the main application entry point (currently empty, awaiting implementation)
- Expected to create Express server with routes for:
  - Knowledge base CRUD operations (articles, categories, documentation)
  - AI-powered search and query endpoints
  - Document generation and summarization via Claude
  - User authentication/authorization

### Environment Configuration
- Use `.env` file for sensitive configuration (API keys, ports, etc.)
- Required environment variables (not yet created):
  - `ANTHROPIC_API_KEY` - for Claude API access
  - `PORT` - server port (default to 3000 if not set)
  - `DATABASE_URL` - connection string for knowledge base storage
  - `JWT_SECRET` or similar for authentication
  - Additional vars as needed for deployment/features

### Expected Domain Model
Similar to IT Glue, expect entities like:
- **Organizations/Companies** - Multi-tenant structure
- **Documentation/Articles** - Core knowledge content
- **Categories/Types** - Organizational hierarchy
- **Assets/Configuration Items** - IT infrastructure tracking
- **Users/Permissions** - Access control

### Typical Express + Anthropic Setup Pattern
When implementing `index.js`, follow this structure:
```javascript
require('dotenv').config();
const express = require('express');
const cors = require('cors');
const Anthropic = require('anthropic');

const app = express();
const client = new Anthropic({ apiKey: process.env.ANTHROPIC_API_KEY });

app.use(cors());
app.use(express.json());

// Routes here

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
```

## Development Workflow

### Running the Application
- `node index.js` - Start the server
- No test framework configured yet; tests use placeholder script

### Adding Dependencies
- Use `npm install <package>` for runtime dependencies
- Use `npm install --save-dev <package>` for dev dependencies

### Environment Setup
1. Create `.env` file (not tracked in git)
2. Add required API keys and configuration
3. Reference via `process.env.VARIABLE_NAME`

## Code Conventions
- CommonJS module system (require/module.exports) - **planned migration to TypeScript/ES modules**
- TypeScript configuration present (`@ljharb/tsconfig`) - setup TS compilation when implementing
- Express 5.x async error handling - use try/catch in async route handlers
- Plan for structured project layout: routes/, controllers/, models/, services/, middleware/

## Key Integration Points
- **Anthropic Claude API**: Powers intelligent features:
  - Smart search across documentation
  - Content summarization and generation
  - Query assistance (natural language → structured data)
  - Documentation suggestions and improvements
- **Database**: Knowledge base storage (DB not yet selected - consider PostgreSQL, MongoDB)
- **CORS**: Configured for cross-origin API access (frontend consumption)
- **REST API**: JSON request/response for KB operations and AI queries

## AI-Powered Features to Implement
- Natural language search across knowledge base
- Auto-summarization of long documentation
- AI-assisted documentation creation
- Smart categorization and tagging
- Query refinement and suggestions

## Important Notes
- Project is in bootstrap phase - main implementation pending
- TypeScript migration recommended before major feature development
- No database layer configured yet - choose based on query patterns (relational vs document)
- Authentication/authorization strategy not yet defined
- Consider: error handling middleware, logging (Winston/Pino), input validation (Joi/Zod)
