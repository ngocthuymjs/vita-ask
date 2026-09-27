# VitaAssist - Product Backlog (Detailed)

---

## EPIC 1: Authentication & User Management

### Job to be Done
"I need to securely access the platform with my company credentials and have my personal settings remembered"

---

### Feature 1.1: User Registration & Login
**Job to be Done**: Users want to quickly sign up and log back in without remembering complex passwords

**User Story**: 
As a new user, I want to register with email/password or company SSO, so I can access the platform

**Definition of Done**:
- [ ] Email/password registration form works
- [ ] Form validation for email format and password strength
- [ ] SSO integration with company auth system
- [ ] Confirmation email sent (if needed)
- [ ] User redirected to dashboard after login
- [ ] Error messages clear and helpful
- [ ] Works on mobile and desktop
- [ ] Tested by QC on Chrome, Firefox, Safari

---

### Feature 1.2: User Profile
**Job to be Done**: Users want a place to see and update their personal info

**User Story**:
As a user, I want to create and edit my profile (name, avatar, email), so others recognize me

**Definition of Done**:
- [ ] Profile page displays current user info
- [ ] Edit form for name, email, avatar
- [ ] Avatar upload works (JPG, PNG max 5MB)
- [ ] Changes save to database
- [ ] Profile updates in chat history
- [ ] Confirmation message on save
- [ ] Password change functionality
- [ ] QC tested profile editing workflow

---

### Feature 1.3: Role & Permissions
**Job to be Done**: System needs to differentiate between free users (low-code) and power users (high-code) with different access levels

**User Story**:
As an admin, I want to assign roles to users, so they access only their tier's features

**Definition of Done**:
- [ ] Role types defined: LOW_CODE_USER, HIGH_CODE_USER, ADMIN
- [ ] Role assignment in admin panel
- [ ] Low-code users see only chat features
- [ ] High-code users see API keys, webhooks
- [ ] Admin sees analytics dashboard
- [ ] Role-based UI rendering works
- [ ] Database stores role per user
- [ ] QC verified permission restrictions

---

## EPIC 2: Chat Core Features

### Job to be Done
"I need to have natural conversations with an AI and access my chat history whenever I need it"

---

### Use Cases Supported by This Epic

| Use Case | Description | Required Features |
|----------|-------------|-------------------|
| **1. Search Information** | Find documents and answers to specific questions | 2.5 (Search), 2.3 (File Upload), 2.2 (History), 2.4 (Share) |
| **2. Ask Common Knowledge Questions** | Ask general questions and get answers | 2.1 (Chat Interface), 2.2 (History), 2.4 (Share) |
| **3. Draft/Write Text** | Collaborate with AI to draft documents | 2.1 (Chat), 2.3 (File Upload), 2.4 (Share) |
| **4. Summarize Documents** | Upload docs and get summaries | 2.3 (File Upload), 2.1 (Chat), 2.2 (History) |

**⚠️ Dependencies from other Epics:**
- File Download: Epic 3.3 (needed for Draft/Summarize use cases)
- File Preview: Epic 6.4 (needed for Search/Summarize use cases)
- Model Selection: Epic 8.2 (needed for all use cases)
- Response Formatting: Epic 3 (needed for all use cases)

---

### Feature 2.1: Real-Time Chat Interface
**Job to be Done**: Users want to send messages and get quick responses in a familiar chat format

**User Story**:
As a user, I want to type questions and see answers appear, so I can have a conversation

**Definition of Done**:
- [ ] Chat input field with send button
- [ ] Message appears immediately after send
- [ ] Typing indicator shows "AI is typing..."
- [ ] Response appears in < 2 seconds (99% of time)
- [ ] Scroll to latest message automatically
- [ ] Message timestamps visible
- [ ] Chat bubbles clearly show user vs AI
- [ ] Works on mobile (responsive)
- [ ] No message loss on connection issues
- [ ] QC tested message sending, edge cases

---

### Feature 2.2: Chat History
**Job to be Done**: Users want to revisit old conversations without starting over

**User Story**:
As a user, I want to see all my past conversations and load them, so I can continue old chats

**Definition of Done**:
- [ ] Left sidebar shows conversation list
- [ ] List shows conversation title (auto-generated or user-named)
- [ ] List shows last message preview
- [ ] List shows timestamp (e.g., "2 days ago")
- [ ] Click to load full conversation
- [ ] Conversation messages load correctly
- [ ] Pagination/infinite scroll for 1000+ conversations
- [ ] No data loss after logout/login
- [ ] Search conversation by title/content works
- [ ] QC tested load performance with 100+ conversations

---

### Feature 2.3: File Upload & Attachment
**Job to be Done**: Users want to provide context documents for the AI to reference

**User Story**:
As a user, I want to upload files (PDF, DOC, TXT), so the AI can read and reference them

**Definition of Done**:
- [ ] Upload button in chat interface
- [ ] Drag & drop file upload works
- [ ] File type validation (PDF, DOC, DOCX, TXT, MD only)
- [ ] File size limit enforced (max 50MB)
- [ ] Upload progress bar shown
- [ ] File appears in chat with name and size
- [ ] File parsing extracts text correctly
- [ ] Error messages for unsupported files
- [ ] Files stored in database/blob storage
- [ ] Up to 10 files per conversation
- [ ] QC tested all file types and error cases

---

### Feature 2.4: Share Conversation
**Job to be Done**: Users want to show conversations to teammates without giving access to their account

**User Story**:
As a user, I want to generate a shareable link to my conversation, so others can view it

**Definition of Done**:
- [ ] Share button in chat interface
- [ ] Generates unique shareable URL
- [ ] Shared link works without login (read-only)
- [ ] Shows all conversation messages
- [ ] Shared link can be revoked/disabled
- [ ] Expiration option (7 days, 30 days, never)
- [ ] Copy link to clipboard button
- [ ] Shared link doesn't show user email
- [ ] Shared view has no edit/delete buttons
- [ ] Database tracks share metadata (created, expires, revoked)
- [ ] QC tested sharing, revoking, expiration

---

### Feature 2.5: Search Conversations
**Job to be Done**: Users want to find old conversations by content without scrolling through all history

**User Story**:
As a user, I want to search my conversations by keyword, so I can quickly find relevant chats

**Definition of Done**:
- [ ] Search box in sidebar
- [ ] Search across conversation titles and messages
- [ ] Results show matching conversations with preview
- [ ] Results ranked by relevance
- [ ] Highlight matching keyword in results
- [ ] Filter by date range (optional)
- [ ] Filter by bot/model (optional)
- [ ] Search returns results in < 1 second
- [ ] No results message is helpful
- [ ] Works with 1000+ conversations
- [ ] QC tested search performance and accuracy

---

## EPIC 3: UI Component Rendering

### Job to be Done
"AI responses should be formatted appropriately for different content types (code, tables, files, etc.) not just plain text"

---

### Use Cases Supported by This Epic

| Use Case | Description | Required Features |
|----------|-------------|-------------------|
| **1. Get Readable Answers** | Display Q&A responses in clear, formatted text with proper typography | 3.1 (Q&A Component) |
| **2. Read Code Properly** | View code with syntax highlighting and copy functionality | 3.2 (Code Component) |
| **3. View Data in Tables** | See structured data as formatted, sortable tables | 3.4 (Table Rendering) |
| **4. Browse Search Results** | View lists of documents/results as organized cards | 3.5 (List & Card Rendering) |
| **5. See Visual Content** | Display images, charts, diagrams inline in responses | 3.6 (Image & Media Rendering) |
| **6. Take Action from Responses** | Click buttons in AI responses to refine or execute actions | 3.7 (Button & Interactive Elements) |
| **7. Download Generated Content** | Export AI responses as files (PDF, CSV, DOC) | 3.3 (File Download) |

**⚠️ Supports other Epics:**
- Required by Epic 2 use cases (Ask Questions, Draft Text, Summarize, Search)
- Required by Epic 5 use cases (bot responses need proper formatting)
- Required by Epic 6 use cases (search results display with cards/lists)
- Integrates with Epic 8 (theme/dark mode affects all component colors)

---

### Feature 3.1: Q&A Component Rendering
**Job to be Done**: Users want clear, readable answers formatted as proper chat messages

**User Story**:
As a user, I want Q&A responses to render as formatted chat bubbles, so they're easy to read

**Definition of Done**:
- [ ] Plain text renders as chat bubble
- [ ] Bold, italic, links formatted correctly
- [ ] Markdown is parsed and rendered (bold, italic, strikethrough, blockquote)
- [ ] Line breaks preserved
- [ ] Code snippets inline render with monospace font
- [ ] **Lists render properly** (bullet points, numbered lists, nested lists)
- [ ] **Links are clickable and styled** with proper hover states
- [ ] **Headings render with proper hierarchy** (h1-h6)
- [ ] Works on mobile (text wrapping, responsive font sizes)
- [ ] Follows design system for colors, typography, shadows
- [ ] QC tested all text formats
- [ ] Accessible: sufficient color contrast, semantic HTML

---

### Feature 3.2: Code Output Component
**Job to be Done**: Developers want to see code with syntax highlighting, not as plain text

**User Story**:
As a developer, I want code outputs to have syntax highlighting, so I can read it easily

**Definition of Done**:
- [ ] Code block renders with language-specific syntax highlighting
- [ ] Language auto-detected or user specifiable
- [ ] Copy button to copy code
- [ ] Line numbers shown
- [ ] Code block scrollable for long code
- [ ] Supports Python, JavaScript, Java, SQL, etc.
- [ ] Dark/light theme support
- [ ] Mobile readable (horizontal scroll)
- [ ] QC tested 10+ languages

---

### Feature 3.3: File Download Component
**Job to be Done**: Users want to download AI-generated content as files (documents, spreadsheets, etc.)

**User Story**:
As a user, I want to download AI responses as files, so I can use them in other tools

**Definition of Done**:
- [ ] Download button appears for downloadable content
- [ ] Generate PDF from text response
- [ ] Generate CSV from table data
- [ ] Generate DOC from formatted content
- [ ] File naming is sensible (e.g., "chat_20260926.pdf")
- [ ] File downloaded to user's computer
- [ ] Works for any response type
- [ ] File format matches content type
- [ ] QC tested PDF, CSV, DOC generation

---

### Feature 3.4: Table Rendering
**Job to be Done**: Users want structured data (tables) displayed as actual tables, not text

**User Story**:
As a user, I want AI-generated tables to render as formatted tables, so I can read data clearly

**Definition of Done**:
- [ ] Markdown tables render as HTML tables
- [ ] Table has headers and rows with proper styling
- [ ] Table header uses **bold font-semibold** with **surface-active background**
- [ ] Table is **sortable by column** (click header to toggle asc/desc)
- [ ] **Striped rows** for readability (alternating bg-surface, bg-surface-alt)
- [ ] **Border/padding** follows design system (border-default, padding 12px)
- [ ] Mobile: table scrollable horizontally with proper spacing
- [ ] Export table to CSV button with design system styling
- [ ] Hover effect on rows (surface-hover)
- [ ] **Data alignment**: numbers right-aligned, text left-aligned
- [ ] QC tested table rendering, sorting, export
- [ ] Accessible: proper semantic HTML (thead, tbody, th, td)

---

### Feature 3.5: List & Card Component Rendering
**Job to be Done**: Users want to view lists of items (search results, recommendations) as visually organized cards or lists, not plain text

**User Story**:
As a user, I want search results and item lists to display as organized cards or list items, so I can scan and interact with them easily

**Definition of Done**:
- [ ] **Unordered lists render as styled list items** with bullet points
- [ ] **Ordered lists render with numbers** (1, 2, 3...)
- [ ] **Nested lists supported** (up to 3 levels deep)
- [ ] **Card list** - search results display as cards with:
  - [ ] Card container: bg-surface-alt, rounded-lg, shadow-3, padding 16px
  - [ ] Card title: text-lg, font-semibold, text-primary
  - [ ] Card description: text-base, text-secondary, truncate at 3 lines
  - [ ] Card metadata: text-sm, text-tertiary (date, source, relevance score)
  - [ ] Card hover: shadow-4, scale 1.01 (optional interactive lift)
- [ ] **List items** display with:
  - [ ] Icon/avatar (optional, if provided)
  - [ ] Title and description
  - [ ] Action buttons (read, share, delete) if applicable
  - [ ] Hover state with bg-surface-hover
- [ ] **Pagination or "Load more" button** for lists > 10 items
- [ ] Search results highlight matching keywords
- [ ] Mobile: single-column layout, full-width cards
- [ ] Follows design system: colors, typography, shadows, spacing
- [ ] QC tested list rendering, card interactions, pagination

---

### Feature 3.6: Image & Media Rendering
**Job to be Done**: Users want to see images, charts, and media in responses, not just text references

**User Story**:
As a user, I want AI responses to display images and media (charts, diagrams), so I can see visual content

**Definition of Done**:
- [ ] **Images render inline** in chat message
- [ ] Image has:
  - [ ] Max-width: 90% of chat width (mobile-friendly)
  - [ ] Rounded corners: rounded-lg (12px)
  - [ ] Shadow: shadow-3
  - [ ] Border: 1px solid border-light (optional)
- [ ] **Image alt text** displayed below or on hover
- [ ] **Caption/description** rendered below image in text-secondary
- [ ] Image is **clickable to expand** (light box/modal view)
- [ ] **Charts and diagrams** render with proper spacing and legends
- [ ] **Video thumbnails** display with play icon overlay
- [ ] Lazy loading for images (don't load all images on page load)
- [ ] Responsive: images scale properly on mobile and desktop
- [ ] Follow design system spacing and shadows
- [ ] QC tested image rendering, lightbox, lazy loading
- [ ] Accessible: alt text, captions for screen readers

---

### Feature 3.7: Button & Interactive Element Rendering
**Job to be Done**: Users want to interact with suggested actions and buttons within chat responses

**User Story**:
As a user, I want to click action buttons in AI responses (e.g., "Learn More", "Try Now", "Refine Search"), so I can take next actions directly

**Definition of Done**:
- [ ] **Primary buttons** render with brand-primary color, white text, proper styling
- [ ] **Secondary buttons** render with surface-alt, border, proper styling
- [ ] **Link buttons** render as colored text with hover underline (text-accent)
- [ ] Button text is **semibold, base size** (font-semibold, text-base)
- [ ] Button padding: **10px 16px** (height 40px, min-width 100px)
- [ ] Button hover state: **shadow-3, scale 1.02, color transition 150ms ease-out**
- [ ] Button active state: **shadow-2, color darkened**
- [ ] Button disabled state: **opacity-50, cursor-not-allowed**
- [ ] **Button groups** (multiple buttons in row) have proper spacing (gap-2)
- [ ] Buttons follow design system radius (rounded-base 8px)
- [ ] **Icon buttons** (ghost style) for common actions (share, copy, delete)
- [ ] Icon buttons: transparent bg, text-primary, hover bg-surface-hover
- [ ] QC tested button interactions, hover states, disabled states
- [ ] Accessible: proper button semantics, keyboard navigation, focus indicators

---

## EPIC 4: High-Code User Features

### Job to be Done
"Developers want to integrate VitaAssist into their own apps via API and track their usage"

---

### Feature 4.1: API Key Management
**Job to be Done**: Developers need secure API keys to authenticate their API requests

**User Story**:
As a developer, I want to generate and manage API keys, so I can use the platform in my app

**Definition of Done**:
- [ ] API keys page in settings
- [ ] Generate new API key button
- [ ] Key shows once after creation (copy warning)
- [ ] List all active keys with creation date
- [ ] Revoke/delete key button (with confirmation)
- [ ] Last used timestamp for each key
- [ ] Usage quota display per key
- [ ] Key name/description editable
- [ ] Can rotate keys (generate new, deactivate old)
- [ ] QC tested key generation, revocation, security

---

### Feature 4.2: API Documentation
**Job to be Done**: Developers want clear docs on how to use the API

**User Story**:
As a developer, I want API documentation with examples, so I can integrate quickly

**Definition of Done**:
- [ ] /docs or dedicated docs page
- [ ] Authentication section (API key usage)
- [ ] Endpoint list with method and path
- [ ] Request/response examples for each endpoint
- [ ] Error codes documented
- [ ] Rate limits clearly stated
- [ ] Code samples (curl, JavaScript, Python)
- [ ] Interactive API explorer (Swagger/OpenAPI)
- [ ] Mobile readable
- [ ] QC checked examples work

---

### Feature 4.3: Usage Dashboard (High-Code)
**Job to be Done**: Developers want to monitor their API usage to avoid overages

**User Story**:
As a high-code user, I want to see my API usage stats, so I know if I'm approaching limits

**Definition of Done**:
- [ ] Dashboard shows total requests (today, this month)
- [ ] Graph of requests over last 30 days
- [ ] Error rate percentage
- [ ] Avg response time in milliseconds
- [ ] Top 10 endpoints by request count
- [ ] Filter by date range
- [ ] Breakdown by response status (2xx, 4xx, 5xx)
- [ ] Current month quota vs limit shown
- [ ] Export usage report (CSV/PDF)
- [ ] QC tested dashboard accuracy, data refresh

---

### Feature 4.4: Rate Limiting
**Job to be Done**: System needs to prevent abuse and ensure fair usage for all users

**User Story**:
As admin, I want rate limiting per API key, so no single user overloads the system

**Definition of Done**:
- [ ] Rate limit enforced: X requests per minute per key
- [ ] Rate limit enforced: Y requests per day per user
- [ ] 429 Too Many Requests error returned
- [ ] Retry-After header included
- [ ] Limit configurable per user tier
- [ ] Whitelist for internal/trusted keys
- [ ] Rate limit resets daily/monthly as specified
- [ ] Admin can override limits
- [ ] QC tested rate limiting with stress test

---

## EPIC 5: Bot Builder

### Job to be Done
"Power users want to create custom AI bots trained on their company's specific knowledge"

---

### Use Cases Supported by This Epic

| Use Case | Description | Required Features |
|----------|-------------|-------------------|
| **1. Create Domain-Specific Bot** | Build a custom bot with specialized knowledge | 5.1 (Create), 5.2 (Document Upload), 5.4 (Config) |
| **2. Train Bot on Company Data** | Upload documents to make bot company-aware | 5.2 (Document Upload), 5.3 (KB Search) |
| **3. Manage Multiple Bots** | Organize and maintain several bots | 5.6 (Manage Bots), 5.4 (Config) |
| **4. Share Bot with Team** | Make bot available to others | 5.5 (Make Public), 5.6 (Manage) |
| **5. Monitor Bot Usage** | Track how bot is being used | 7.2 (Bot Analytics) - *from Epic 7* |

**⚠️ Dependencies from other Epics:**
- Bot Analytics: Epic 7.2 (needed to track bot usage)
- Chat Interface: Epic 2.1 (needed to actually chat with bot)

---

### Feature 5.1: Create Custom Bot
**Job to be Done**: Users want to create their own bot instead of using the default one

**User Story**:
As a power user, I want to create a custom bot with a name and avatar, so it feels like my own assistant

**Definition of Done**:
- [ ] Create Bot button on dashboard
- [ ] Form: bot name (required, max 50 chars)
- [ ] Form: bot description (optional, max 200 chars)
- [ ] Form: avatar upload or emoji selector
- [ ] Form: choose base model (GPT-4, Claude, etc.)
- [ ] Form: set system prompt (optional)
- [ ] Bot created and saved to database
- [ ] Bot appears in "My Bots" list
- [ ] Can immediately chat with new bot
- [ ] Unique ID generated for bot
- [ ] QC tested bot creation, all fields

---

### Feature 5.2: Document Upload to Bot
**Job to be Done**: Users want to upload company documents so the bot knows domain-specific info

**User Story**:
As a bot owner, I want to upload documents to my bot, so it can answer company-specific questions

**Definition of Done**:
- [ ] Upload button in bot settings
- [ ] Drag & drop or file picker
- [ ] Support PDF, TXT, MD, DOCX (max 100MB total)
- [ ] Multiple file upload at once
- [ ] Upload progress bar for each file
- [ ] File list shows name, size, upload date
- [ ] Delete file button with confirmation
- [ ] Files indexed for vector search
- [ ] Embedding generation happens in background
- [ ] Notification when indexing complete
- [ ] Max 500 documents per bot
- [ ] QC tested file upload, deletion, indexing

---

### Feature 5.3: Knowledge Base Search
**Job to be Done**: Users want to know what documents their bot has access to

**User Story**:
As a bot owner, I want to search my bot's knowledge base, so I know what info is available

**Definition of Done**:
- [ ] Search box in bot settings → Knowledge Base tab
- [ ] Search by keyword across all documents
- [ ] Results show matching documents with excerpt
- [ ] Click result to preview full document
- [ ] Relevance score shown (percentage)
- [ ] Filter by document type
- [ ] Sort by relevance or date
- [ ] Shows total documents indexed
- [ ] Search results in < 1 second
- [ ] QC tested search accuracy

---

### Feature 5.4: Bot Configuration
**Job to be Done**: Users want to tune how the bot behaves (tone, detail level, model)

**User Story**:
As a bot owner, I want to configure bot settings (model, temperature, etc.), so it behaves how I want

**Definition of Done**:
- [ ] Settings page for each bot
- [ ] Model dropdown (switch to different models)
- [ ] Temperature slider (0-1, explained)
- [ ] Max tokens setting
- [ ] System prompt editor
- [ ] Description editor
- [ ] Avatar change button
- [ ] Bot name editable
- [ ] Save button with confirmation
- [ ] Changes apply immediately to new conversations
- [ ] QC tested all settings

---

### Feature 5.5: Make Bot Public
**Job to be Done**: Bot owners want to share bots with others or make them discoverable

**User Story**:
As a bot owner, I want to make my bot public, so others can find and use it

**Definition of Done**:
- [ ] Toggle: Public/Private in bot settings
- [ ] Public bots appear in bot directory
- [ ] Bot directory searchable
- [ ] Each public bot has showcase page (name, description, creator, stats)
- [ ] Public bot link sharable
- [ ] Anyone can chat with public bot (no auth needed)
- [ ] Public bot usage doesn't count against user's quota
- [ ] Creator gets credit/attribution
- [ ] Like/star button on public bot
- [ ] QC tested making bot public/private, sharing

---

### Feature 5.6: Manage Bots
**Job to be Done**: Users want to organize and manage multiple bots they've created

**User Story**:
As a user, I want to edit, delete, or duplicate my bots, so I can keep my bot list organized

**Definition of Done**:
- [ ] My Bots list shows all user's bots
- [ ] Each bot shows: name, created date, last used, status (public/private)
- [ ] Click bot to open chat
- [ ] Edit button opens settings
- [ ] Delete button with confirmation
- [ ] Duplicate button creates copy of bot + docs
- [ ] Star/favorite button
- [ ] Sort by name, date, usage
- [ ] Search bot by name
- [ ] QC tested all bot management actions

---

## EPIC 6: Knowledge Base & Search

### Job to be Done
"Users want to search company documents and policies directly through the chatbot"

---

### Use Cases Supported by This Epic

| Use Case | Description | Required Features |
|----------|-------------|-------------------|
| **1. Search Company Information** | Find policies, benefits, procedures across company docs | 6.1 (Document Mgmt), 6.2 (Full-Text Search), 6.3 (Semantic Search) |
| **2. Access Document Details** | View full documents or relevant excerpts | 6.4 (Document Preview), 6.1 (Document Mgmt) |
| **3. Stay Updated on Company Policies** | Reference latest company-wide documents in chat | 6.1 (Document Mgmt), 6.4 (Document Preview) |

**⚠️ Dependencies from other Epics:**
- Chat Integration: Epic 2.1 (needed to reference docs in conversation)
- Document Upload Interface: Epic 2.3 or 5.2 (users upload docs via chat or bot builder)

---

### Feature 6.1: Global Document Management
**Job to be Done**: Company admins want to upload shared company documents that all bots can reference

**User Story**:
As an admin, I want to upload company-wide documents, so all bots have access to policies

**Definition of Done**:
- [ ] Admin document upload section
- [ ] Drag & drop or file picker
- [ ] Support PDF, TXT, MD, DOCX
- [ ] Bulk upload multiple files
- [ ] Document list with name, upload date, size
- [ ] Category/tag assignment per document
- [ ] Delete document with confirmation
- [ ] Document versioning (keep history)
- [ ] Search across all company docs
- [ ] Documents indexed for vector search
- [ ] QC tested upload, deletion, search

---

### Feature 6.2: Full-Text Search
**Job to be Done**: Users want to find specific information in documents by searching keywords

**User Story**:
As a user, I want to search company documents by keyword, so I find the info I need

**Definition of Done**:
- [ ] Search box in knowledge base section
- [ ] Keyword search across document text
- [ ] Results show matching documents with excerpt
- [ ] Highlight matching keyword in excerpt
- [ ] Results ranked by relevance
- [ ] Filter by document type/category
- [ ] Filter by date range
- [ ] Pagination for many results
- [ ] Search results in < 500ms
- [ ] QC tested search speed and accuracy

---

### Feature 6.3: Semantic Search (AI-Powered)
**Job to be Done**: Users want to find documents by meaning, not just keywords (e.g., "vacation policy" finds "time off" doc)

**User Story**:
As a user, I want to search by meaning (not just keywords), so I find relevant docs even with different wording

**Definition of Done**:
- [ ] Vector embeddings generated for all documents
- [ ] Semantic search works in search box
- [ ] "vacation policy" finds "time off" document
- [ ] "leave request" finds "PTO" document
- [ ] Results ranked by semantic similarity score
- [ ] Fallback to keyword search if no semantic results
- [ ] Embeddings updated when documents change
- [ ] Works in multiple languages (EN, VN)
- [ ] QC tested semantic accuracy

---

### Feature 6.4: Document Preview in Chat
**Job to be Done**: Users want to see relevant document excerpts when the bot references documents

**User Story**:
As a user, I want the bot to show document excerpts in responses, so I can see the source

**Definition of Done**:
- [ ] Bot search results include source document name
- [ ] Click document name to preview full doc
- [ ] Preview shows relevant excerpt with highlight
- [ ] Preview shows page number (if PDF)
- [ ] Download original document button
- [ ] Close preview to go back to chat
- [ ] Preview doesn't interrupt chat flow
- [ ] QC tested preview for PDFs and text files

---

## EPIC 7: Analytics Dashboard

### Job to be Done
"Users and admins want visibility into platform usage and bot performance to make decisions"

---

### Feature 7.1: User Analytics Dashboard (Admin)
**Job to be Done**: Admin needs to see platform-wide user engagement to track growth

**User Story**:
As an admin, I want to see user analytics (DAU, MAU, trends), so I can track platform growth

**Definition of Done**:
- [ ] Dashboard shows total DAU (Daily Active Users)
- [ ] Shows total MAU (Monthly Active Users)
- [ ] Graph: user growth over last 30 days
- [ ] Filter by date range
- [ ] Show breakdown by user type (low-code, high-code)
- [ ] Show retention metrics (day 7, day 30)
- [ ] Show churn rate
- [ ] Show new user signups over time
- [ ] Export data as CSV/PDF
- [ ] QC tested data accuracy

---

### Feature 7.2: Bot Analytics (Power Users)
**Job to be Done**: Bot creators want to see how their bots are being used

**User Story**:
As a bot owner, I want to see bot analytics (conversations, ratings), so I know if my bot is useful

**Definition of Done**:
- [ ] Bot detail page shows total conversations
- [ ] Show conversation count by date (last 30 days)
- [ ] Show average conversation length
- [ ] Show most common questions
- [ ] Show user satisfaction (avg rating)
- [ ] Show avg response rating (thumbs up/down)
- [ ] Filter by date range
- [ ] Show bot creator and creation date
- [ ] Export bot report (CSV/PDF)
- [ ] QC tested analytics calculation

---

### Feature 7.3: API Usage Analytics (High-Code Users)
**Job to be Done**: API users want to monitor their usage to avoid overages and track costs

**User Story**:
As a high-code user, I want detailed API usage analytics, so I can track costs and quotas

**Definition of Done**:
- [ ] Dashboard shows total requests this month
- [ ] Show requests by day (line graph)
- [ ] Show error rate (percentage)
- [ ] Show avg response time (ms)
- [ ] Show breakdown by status code (2xx, 4xx, 5xx)
- [ ] Show top 10 endpoints by requests
- [ ] Current quota vs limit displayed
- [ ] Estimated cost calculation
- [ ] Filter by date range
- [ ] Export usage report (CSV)
- [ ] Alert when approaching quota
- [ ] QC tested data accuracy

---

### Feature 7.4: Document Performance Analytics
**Job to be Done**: Bot owners want to know which documents are most valuable

**User Story**:
As a bot owner, I want to see which documents are most referenced, so I know what matters

**Definition of Done**:
- [ ] Show all documents in bot's knowledge base
- [ ] Show reference count per document
- [ ] Show hit rate (% of conversations that use doc)
- [ ] Show avg rating when used
- [ ] Identify unused documents
- [ ] Embedding quality score
- [ ] Last referenced date
- [ ] Document size and type
- [ ] Sort by references or rating
- [ ] QC tested calculation accuracy

---

### Feature 7.5: Platform Health Dashboard (Admin)
**Job to be Done**: Admin needs to monitor system performance and errors

**User Story**:
As an admin, I want to see platform health (response time, errors), so I can catch issues

**Definition of Done**:
- [ ] System uptime percentage (last 30 days)
- [ ] Avg response time by endpoint (graph)
- [ ] Error rate (percentage)
- [ ] Top errors by frequency
- [ ] Database performance metrics
- [ ] API rate limit hits
- [ ] Active concurrent users
- [ ] Response time percentiles (p50, p95, p99)
- [ ] Alerts for threshold breaches
- [ ] QC tested dashboard rendering

---

### Feature 7.6: Reports & Export
**Job to be Done**: Users want to export analytics data for external reporting

**User Story**:
As a user, I want to export analytics reports, so I can share data with stakeholders

**Definition of Done**:
- [ ] Export button on each analytics page
- [ ] Export to CSV format
- [ ] Export to PDF format (formatted nicely)
- [ ] Choose date range for export
- [ ] File naming includes date (e.g., "bot_analytics_20260926.pdf")
- [ ] Email report option
- [ ] Schedule recurring reports (weekly/monthly)
- [ ] Custom report builder (select metrics)
- [ ] QC tested CSV and PDF export

---

## EPIC 8: Settings & Admin

### Job to be Done
"Users need a place to control their preferences and admins need to manage the platform"

---

### Feature 8.1: User Preferences
**Job to be Done**: Users want to customize their experience

**User Story**:
As a user, I want to customize my settings (theme, language, notifications), so the app fits my needs

**Definition of Done**:
- [ ] Settings page with tabs: Profile, Preferences, Privacy, Security
- [ ] Theme toggle: Light/Dark/Auto
- [ ] Language selection (EN, VN, more)
- [ ] Notification settings (email, in-app)
- [ ] Auto-save preferences to database
- [ ] Settings persist across sessions
- [ ] Reset to defaults option
- [ ] Save confirmation message
- [ ] QC tested all settings persistence

---

### Feature 8.2: Model Selection
**Job to be Done**: Users want to choose which AI model powers their conversations

**User Story**:
As a user, I want to select which model to use (GPT-4, Claude), so I can choose based on my needs

**Definition of Done**:
- [ ] Model selector dropdown in settings
- [ ] List available models with descriptions
- [ ] Show model pricing/cost (if applicable)
- [ ] Show model capabilities (speed, accuracy)
- [ ] Selection saved to user preferences
- [ ] Default model for new conversations
- [ ] Per-bot model selection in bot settings
- [ ] Model switch works mid-conversation
- [ ] QC tested model selection, switching

---

### Feature 8.3: Admin Dashboard
**Job to be Done**: Admins need a control panel to manage users and platform

**User Story**:
As an admin, I want an admin dashboard, so I can manage users, review content, and monitor platform

**Definition of Done**:
- [ ] Admin panel accessible only to admins
- [ ] User management: view all users, search, filter
- [ ] User details: email, role, created date, last login
- [ ] Ban/unban user buttons
- [ ] Change user role (low-code → high-code)
- [ ] View user's conversations (audit)
- [ ] Content moderation: flag/review conversations
- [ ] System settings: rate limits, model availability
- [ ] Announcements: post notifications to users
- [ ] QC tested admin actions security

---

## EPIC 9: Performance & Infrastructure

### Job to be Done
"System needs to be fast, reliable, and secure to serve 100K users"

---

### Feature 9.1: Response Caching
**Job to be Done**: System needs to reduce load and improve speed by caching common queries

**User Story**:
As admin, I want API responses cached, so the platform stays fast under heavy load

**Definition of Done**:
- [ ] Cache layer implemented (Redis or similar)
- [ ] Identical queries return cached results (< 100ms)
- [ ] Cache invalidates after 24 hours
- [ ] Cache hit rate monitored (target > 40%)
- [ ] Cache doesn't return stale docs
- [ ] User-specific data not cached
- [ ] Cache size limits enforced
- [ ] QC tested cache performance and accuracy

---

### Feature 9.2: Database Optimization
**Job to be Done**: Database queries need to be fast for millions of messages

**User Story**:
As admin, I want database queries optimized, so chats load instantly

**Definition of Done**:
- [ ] Database indexes on frequently searched columns
- [ ] Query optimization for conversation retrieval
- [ ] Pagination enforced (don't load 1000+ messages at once)
- [ ] Archive old conversations to separate storage
- [ ] Query execution time monitored
- [ ] Slow query alerts
- [ ] Database backups automated daily
- [ ] QC load tested with 100K users

---

### Feature 9.3: API Rate Limiting
**Job to be Done**: System needs to prevent abuse and ensure fair resource usage

**User Story**:
As admin, I want rate limiting enforced, so no user can overload the system

**Definition of Done**:
- [ ] Rate limit: 100 requests/min per user
- [ ] Rate limit: 1000 requests/day per user
- [ ] Rate limit: 50 requests/min per API key
- [ ] Rate limit errors return 429 status
- [ ] Retry-After header included
- [ ] Whitelist for internal services
- [ ] Admin can adjust limits per tier
- [ ] Rate limit metrics tracked
- [ ] QC tested with stress testing

---

### Feature 9.4: Error Handling & Resilience
**Job to be Done**: System should handle failures gracefully and recover quickly

**User Story**:
As user, I want the system to handle errors gracefully, so I know what went wrong

**Definition of Done**:
- [ ] All API errors return meaningful messages
- [ ] Retry logic for failed API calls (exponential backoff)
- [ ] Circuit breaker for failing downstream services
- [ ] Error logging to monitoring system
- [ ] User-friendly error messages (not stack traces)
- [ ] Timeout handling (no requests hang > 30s)
- [ ] Fallback responses when dependencies fail
- [ ] QC tested error scenarios (network, timeout, 500s)

---

### Feature 9.5: Monitoring & Alerts
**Job to be Done**: Admin needs real-time alerts when something goes wrong

**User Story**:
As admin, I want monitoring and alerts, so I can fix issues before users notice

**Definition of Done**:
- [ ] Uptime monitoring (ping every 5 min)
- [ ] Alert if > 5 min of downtime
- [ ] Response time tracking per endpoint
- [ ] Alert if avg response time > 3 seconds
- [ ] Error rate monitoring
- [ ] Alert if error rate > 1%
- [ ] Database performance monitoring
- [ ] Alert channels: email, Slack, SMS
- [ ] Dashboard shows live metrics
- [ ] QC tested monitoring accuracy

---

### Feature 9.6: Security & Data Protection
**Job to be Done**: User data and conversations must be secure and private

**User Story**:
As user, I want my data encrypted and private, so I feel safe sharing info with the bot

**Definition of Done**:
- [ ] HTTPS enforced everywhere
- [ ] Data encrypted in transit (TLS)
- [ ] Data encrypted at rest (DB encryption)
- [ ] API keys never logged or exposed
- [ ] User conversations not shared between accounts
- [ ] CORS properly configured
- [ ] XSS protection enabled
- [ ] CSRF tokens on all state-changing forms
- [ ] SQL injection prevention (prepared statements)
- [ ] Rate limiting prevents brute force
- [ ] Regular security audits
- [ ] QC security tested (OWASP top 10)

---

## Summary Table

| Epic | Features | Phase | Effort |
|------|----------|-------|--------|
| 1. Auth | 3 features | Sprint 1 | 8 days |
| 2. Chat | 5 features | Sprint 2 | 12 days |
| 3. UI Components | **7 features** | Sprint 2-3 | **16 days** |
| 4. High-Code | 4 features | Sprint 2-3 | 10 days |
| 5. Bot Builder | 6 features | Sprint 2-3 | 15 days |
| 6. Knowledge Base | 4 features | Sprint 2-3 | 12 days |
| 7. Analytics | 6 features | Sprint 3+ | 18 days |
| 8. Settings | 3 features | Sprint 1-2 | 6 days |
| 9. Infrastructure | 6 features | Throughout | 20 days |

**Total Effort**: ~~111~~ **117 developer-days** (6-8 weeks with 4 engineers)

---

## Cross-Epic Use Case Mapping

This section shows which EPICs support each user job and highlights dependencies:

### Epic 2 Use Cases (Chat Core)
```
Search Information
├── Primary: Epic 2 (2.5, 2.3, 2.2, 2.4)
├── Supporting: Epic 6 (6.2, 6.3, 6.4) - semantic search, document preview
└── Supporting: Epic 3 (3.1, 3.4) - response formatting

Ask Common Knowledge Questions
├── Primary: Epic 2 (2.1, 2.2, 2.4)
├── Supporting: Epic 3 (3.1, 3.2, 3.4, 3.6, 3.7) - response formatting, images, buttons
└── Supporting: Epic 8 (8.2) - model selection

Draft/Write Text
├── Primary: Epic 2 (2.1, 2.3, 2.4)
├── Supporting: Epic 3 (3.1, 3.3, 3.7) - text formatting, file download, buttons
├── Supporting: Epic 8 (8.2) - model selection
└── Supporting: Epic 6 (6.4) - document preview (for reference)

Summarize Documents
├── Primary: Epic 2 (2.3, 2.1, 2.2)
├── Supporting: Epic 3 (3.1, 3.3, 3.5, 3.6) - response formatting, file download, lists, images
├── Supporting: Epic 6 (6.4) - document preview
└── Supporting: Epic 8 (8.2) - model selection

Search Information
├── Primary: Epic 2 (2.5, 2.3, 2.2, 2.4)
├── Supporting: Epic 3 (3.1, 3.5, 3.6, 3.7) - text formatting, cards/lists, images, action buttons
├── Supporting: Epic 6 (6.2, 6.3, 6.4) - search, semantic search, document preview
└── Supporting: Epic 8 (8.2) - model selection
```

### Epic 5 Use Cases (Bot Builder)
```
Create Domain-Specific Bot
├── Primary: Epic 5 (5.1, 5.2, 5.4)
├── Supporting: Epic 2 (2.1) - chat interface
└── Supporting: Epic 3 - response formatting

Train Bot on Company Data
├── Primary: Epic 5 (5.2, 5.3)
└── Supporting: Epic 6 - knowledge base search

Share Bot with Team
├── Primary: Epic 5 (5.5, 5.6)
└── Supporting: Epic 7 (7.2) - bot analytics

Monitor Bot Usage
├── Primary: Epic 7 (7.2) - bot analytics
└── Supporting: Epic 5 (5.6) - manage bots
```

### Epic 6 Use Cases (Knowledge Base)
```
Search Company Information
├── Primary: Epic 6 (6.1, 6.2, 6.3)
└── Supporting: Epic 2 (2.1) - chat interface

Access Document Details
├── Primary: Epic 6 (6.1, 6.4)
└── Supporting: Epic 5 (5.3) - bot knowledge base search
```

**Key Insights:**
- Epic 2, 3, 6, 8 are tightly **interdependent** for basic use cases
- Epic 5 is **semi-independent** but relies on Epic 2 for chat and Epic 7 for usage tracking
- Epic 7 (Analytics) serves as **supporting infrastructure** for other Epics
- **Dependency chain**: Epic 2 ← requires → Epic 3, 6, 8
