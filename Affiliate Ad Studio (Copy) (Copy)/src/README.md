# 🎯 Affiliate Ad Launch Studio

A professional, AI-powered web application for launching high-performing affiliate advertising campaigns. Built with React, TypeScript, and Tailwind CSS with Google Authentication and Cloudflare Workers integration.

> **🚀 Now powered by Google Gemini API** - Fast, cost-effective AI responses with seamless Cloudflare Worker integration. See [GEMINI_MIGRATION.md](GEMINI_MIGRATION.md) for details.

## 📚 Documentation

- **[ADMIN_SETUP.md](ADMIN_SETUP.md)** - Complete admin setup guide (OAuth, Worker, Environment)
- **[WORKER_SETUP.md](WORKER_SETUP.md)** - Step-by-step Cloudflare Worker deployment with Gemini
- **[GEMINI_MIGRATION.md](GEMINI_MIGRATION.md)** - Migration details, cost comparison, and optimization tips
- **[TROUBLESHOOTING.md](TROUBLESHOOTING.md)** - Common issues and solutions

## ✨ Features

### 🔐 Secure Authentication
- Google OAuth integration
- Secure user sessions
- Profile management

### 🤖 11 Specialized AI Agents
1. **📋 Campaign Setup** - Define product, goals, budget, and constraints
2. **🎯 Marketing Strategist** - Target audiences, hypotheses, budget allocation
3. **💡 Creative Strategist** - Creative briefs, hooks, messaging pillars
4. **🔍 Competitor Analysis** - Market gaps, competitor ads, bid landscape
5. **🎬 Video Director** - Scene-by-scene scripts, pacing, music style
6. **🎨 Designer** - Design specs, layouts, color palettes, thumbnails
7. **✨ AI Prompt Generator** - Prompts for Midjourney, DALL-E, Runway
8. **✍️ Copywriter** - Ad copy, headlines, CTAs, landing page copy
9. **📈 Media Buyer** - Test matrices, bidding strategy, scaling rules
10. **📊 Data & Analytics** - Pixel events, UTM templates, tracking setup
11. **🛡️ Compliance** - Policy review, disclaimers, platform restrictions
12. **📅 Campaign Scheduler** - Launch timelines, scheduling rules, pacing

### 💬 AI Chat Assistant
- **CampaignGPT** - Interactive chat panel on every agent page
- Context-aware responses based on current campaign
- Quick action buttons for common tasks
- Full conversation history

### 🎨 Professional UI
- Modern dark sidebar with progress tracking
- Gradient accents and smooth animations
- Real-time status indicators
- Responsive design for desktop workflows

## 🚀 Quick Setup

### Prerequisites
- Node.js 16+ and npm
- Google Cloud account (for OAuth)
- Cloudflare Worker deployed and configured (see [WORKER_SETUP.md](WORKER_SETUP.md))
- Google AI Studio API key (see [ADMIN_SETUP.md](ADMIN_SETUP.md))

### 1. Clone and Install

```bash
git clone <repository-url>
cd affiliate-ad-studio
npm install
```

### 2. Configure Environment Variables

```bash
# Copy the example file
cp .env.example .env.local

# Edit with your values
nano .env.local
```

Fill in your `.env.local`:
```bash
# Cloudflare Worker (Required)
REACT_APP_AGENT_WORKER=https://your-worker.workers.dev/agent

# Google OAuth (Required)
REACT_APP_GOOGLE_CLIENT_ID=your-client-id.apps.googleusercontent.com

# Optional: Analytics
REACT_APP_GA_ID=
```

### 3. Set Up Google OAuth

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select existing
3. Enable Google Sign-In API
4. Create OAuth 2.0 credentials
5. Add authorized JavaScript origins:
   - `http://localhost:3000` (development)
   - `https://yourdomain.com` (production)
6. Copy the Client ID to `.env.local`

### 4. Run the Application

```bash
npm start
```

Visit `http://localhost:3000` and sign in with Google.

## 🏗️ Architecture

```
Frontend (React + TypeScript)
    ↓
Google OAuth Authentication
    ↓
Campaign Context (State Management)
    ↓
Agent Components
    ↓
Worker Service
    ↓
Cloudflare Worker (Admin-controlled)
    ↓
Google Gemini API
```

## 📦 Tech Stack

- **React 18** - UI framework
- **TypeScript** - Type safety
- **Tailwind CSS v4** - Styling
- **Shadcn/UI** - Component library
- **Lucide React** - Icons
- **React Router** - Navigation
- **Google OAuth** - Authentication
- **Cloudflare Workers** - Edge compute
- **Google Gemini** - LLM API

## 🔒 Security

- ✅ Google OAuth for secure authentication
- ✅ API keys stored in Cloudflare Worker (never exposed to clients)
- ✅ Secure session management
- ✅ HTTPS required for production
- ✅ CORS protection on worker

## 📊 Workflow

1. **Sign In** with Google
2. **Create Campaign** in Data Hub
3. **Sequential Agent Workflow**:
   - Marketing Strategist → Creative Strategist → Video Director → etc.
4. **Use CampaignGPT** chat for assistance on any page
5. **Export Reports** when campaign is complete

## 🛠️ Development

### Project Structure
```
/components
  /agents          - 11 specialized agent pages
  /ui              - Shadcn UI components
  AgentLayout.tsx  - Shared layout
  AgentChatPanel.tsx - AI chat interface
  Header.tsx       - Top navigation with user menu
  Navigation.tsx   - Left sidebar
  LoginPage.tsx    - Google sign-in page
  
/context
  AuthContext.tsx  - Authentication state
  CampaignContext.tsx - Campaign state

/services
  workerService.tsx - Cloudflare Worker integration
```

### Build for Production

```bash
npm run build
```

Deploy the `build` folder to your hosting service.

## 🌐 Deployment

### Frontend Deployment
- Vercel (recommended)
- Netlify
- AWS Amplify
- Any static hosting

### Environment Variables (Production)
Set these in your hosting platform:
- `REACT_APP_AGENT_WORKER` - Your Cloudflare Worker URL
- `REACT_APP_GOOGLE_CLIENT_ID` - Your Google OAuth Client ID

### Google OAuth Setup for Production
1. Add your production domain to authorized JavaScript origins
2. Add your production domain to authorized redirect URIs
3. Verify domain ownership in Google Search Console

## 💰 Cost Estimates

### Infrastructure
- Frontend hosting: $0-20/month (Vercel/Netlify free tier available)
- Cloudflare Worker: Free tier (100k requests/day)

### LLM API (per campaign)
- Gemini Flash: ~$0.10-0.30
- Gemini Pro: ~$0.50-1.50

### Monthly (100 campaigns)
- Gemini Flash: ~$10-30
- Gemini Pro: ~$50-150

## 📝 License

MIT License

## 🙏 Credits

- Built with React + Tailwind CSS
- UI components from Shadcn/UI
- Icons from Lucide React
- Authentication by Google
- AI powered by Google Gemini

---

**For Admin Use Only** - This is a production application with admin-controlled infrastructure.