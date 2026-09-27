# VitaAssist - Product Backlog

## Epics

### 1. Authentication & User Management
- [ ] **Login/Sign up** - Email + password, SSO (company)
- [ ] **User profiles** - Display name, avatar, preferences
- [ ] **Role management** - Low-code users vs High-code users

### 2. Chat Core Features
- [ ] **Chat interface** - Real-time messaging, typing indicators
- [ ] **Chat history** - Save & view conversation history
- [ ] **File upload/Attachment** - Support PDF, DOC, images
- [ ] **Share chat** - Generate shareable links or send to users
- [ ] **Search conversations** - Find past messages

### 3. UI Component Rendering
- [ ] **Q&A component** - Render as chat bubble UI
- [ ] **Text editor output** - Render as downloadable card/file
- [ ] **Summary output** - Render as formatted text card
- [ ] **Code output** - Syntax highlighting card
- [ ] **File download** - Generate & download content

### 4. High-Code User Features
- [ ] **API key management** - Generate, revoke, manage keys
- [ ] **API documentation** - Usage guide, endpoints, auth
- [ ] **Rate limiting dashboard** - Monitor API usage
- [ ] **Webhooks** - Send events to external systems (optional)

### 5. Bot Builder
- [ ] **Create custom bot** - Name, description, avatar
- [ ] **Document upload** - Upload knowledge base (PDF, TXT, MD)
- [ ] **Bot configuration** - Set system prompt, model, parameters
- [ ] **Bot deployment** - Make bot public/private
- [ ] **Bot analytics** - Usage stats, conversation count
- [ ] **Manage bot** - Edit, delete, duplicate

### 6. Knowledge Base & Search
- [ ] **Document management** - Upload, organize, categorize
- [ ] **Full-text search** - Search across all documents
- [ ] **Semantic search** - Vector search on embeddings
- [ ] **Preview documents** - Show relevant excerpts in chat

### 7. Settings & Admin
- [ ] **User settings** - Preferences, notifications, theme
- [ ] **Model selection** - Switch between available models
- [ ] **Conversation settings** - Temperature, max tokens, etc.
- [ ] **Admin dashboard** - User management, usage stats (if needed)

### 8. Analytics Dashboard
- [ ] **User analytics** - DAU, MAU, usage trends
- [ ] **Bot analytics** - Per-bot stats (views, conversations, avg rating)
- [ ] **API analytics** - Requests, errors, latency for high-code users
- [ ] **Document analytics** - Upload count, most-used docs
- [ ] **Conversation analytics** - Avg length, success rate, user satisfaction
- [ ] **Export reports** - PDF/CSV reports for admins

### 9. Performance & Infrastructure
- [ ] **Caching** - Cache responses, documents, embeddings
- [ ] **Rate limiting** - Per user, per API key
- [ ] **Error handling** - Graceful errors, retry logic
- [ ] **Monitoring** - Uptime, response time, errors

---

## User Stories by Priority

### Phase 1 (Sprint 2): MVP Features

```
As a low-code user,
I want to chat with the AI,
So that I can ask questions and get answers

Acceptance Criteria:
- Send messages and receive responses < 2s
- See typing indicator while waiting
- Display conversation in chronological order
```

```
As a low-code user,
I want to see my chat history,
So that I can revisit past conversations

Acceptance Criteria:
- View list of past conversations
- Click to load conversation
- See all messages in conversation
```

```
As a low-code user,
I want to upload files,
So that the AI can reference them

Acceptance Criteria:
- Upload PDF, DOC, TXT, MD files
- See upload progress
- Display file name in chat context
```

```
As a high-code user,
I want to get API keys,
So that I can use the service in my app

Acceptance Criteria:
- Generate API key from settings
- Copy/show key once
- Can revoke/delete keys
- See usage stats for each key
```

```
As any user,
I want to share conversations,
So that I can collaborate with others

Acceptance Criteria:
- Generate shareable link
- Link works without login (read-only)
- Can turn off sharing
```

---

### Phase 2 (Sprint 2-3): Bot Builder

```
As a power user,
I want to create a custom bot,
So that I can have domain-specific AI

Acceptance Criteria:
- Create bot with name, description, avatar
- Set system prompt
- Choose model
- Bot appears in my bot list
```

```
As a power user,
I want to upload documents to my bot,
So that the AI can reference company info

Acceptance Criteria:
- Upload multiple files (PDF, TXT, MD, DOC)
- See upload progress
- Files indexed for search
- See file list in bot settings
```

```
As a power user,
I want to search my bot's knowledge base,
So that I know what info is available

Acceptance Criteria:
- Search documents by keyword
- See matching results
- Click result to preview
```

```
As a power user,
I want to make my bot public,
So that others can use it

Acceptance Criteria:
- Toggle public/private
- Bot appears in public bot directory
- Share bot link
```

---

### Phase 3 (Sprint 3): Polish & Advanced

```
As any user,
I want to see different UI outputs,
So that responses are properly formatted

Acceptance Criteria:
- Q&A renders as chat bubbles
- Code renders with syntax highlighting
- Tables render as formatted cards
- Files render as downloadable cards
```

```
As any user,
I want to search across conversations,
So that I can find old info

Acceptance Criteria:
- Search by keyword
- Filter by bot/conversation
- Highlight matches
```

```
As any user,
I want to organize conversations,
So that my history is clean

Acceptance Criteria:
- Archive conversations
- Delete conversations
- Star/favorite conversations
```

---

### Phase 3+ (Sprint 3+): Analytics Dashboard

```
As a power user (bot creator),
I want to see analytics for my bots,
So that I can track usage and engagement

Acceptance Criteria:
- View total conversations count
- See conversation trend (last 7/30 days)
- View avg conversation length
- See most popular questions
- Track user satisfaction (ratings/feedback)
- Filter by date range
```

```
As a high-code user,
I want to see my API usage analytics,
So that I can monitor costs and quotas

Acceptance Criteria:
- View total requests count
- See requests per day/hour graph
- Monitor error rate
- Track response time stats
- View top endpoints
- Export usage report (CSV/PDF)
```

```
As an admin,
I want to see platform-wide analytics,
So that I can monitor platform health

Acceptance Criteria:
- View total DAU/MAU
- See bot creation trends
- Track document uploads count
- Monitor system performance (response time, errors)
- View user retention metrics
- See revenue/usage by tier (if applicable)
```

```
As a power user,
I want to see document usage analytics,
So that I know which docs are most helpful

Acceptance Criteria:
- View which docs are referenced most
- See document retrieval success rate
- Track embeddings quality score
- Identify unused documents
```

---

## Additional Features to Consider

| Feature | Priority | Effort | Notes |
|---------|----------|--------|-------|
| **Conversation export** | Medium | 2 days | Export to PDF, Markdown |
| **Multi-language support** | Low | 3 days | Vietnamese, English to start |
| **Conversation tags** | Low | 2 days | Organize chats with tags |
| **Templates** | Medium | 3 days | Pre-built prompts for common tasks |
| **Team/org management** | Low | 5 days | Share bots within team |
| **Billing & credits** | Depends | 5 days | If you want monetization |
| **Integrations** (Slack, Teams) | Very Low | 4 days each | Post-launch feature |
| **Chat moderation** | Medium | 3 days | Filter unsafe content |
| **User feedback** | Low | 2 days | Rate responses, improve AI |

---

## Dependencies
- Backend APIs ready ✅
- Vector embeddings for search
- File parsing library (for PDF, DOC, etc.)
- Authentication system
- Database for storing chats, bots, docs

---

## Metrics to Track
- DAU (Daily Active Users)
- Avg conversation length
- API usage by high-code users
- Bot creation rate
- Document upload rate
- Chat share rate
