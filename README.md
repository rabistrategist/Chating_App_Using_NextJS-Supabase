Project Demo: [Screencast from 02-13-2026 12:31:23 PM.webm](https://github.com/user-attachments/assets/edad0c84-c8d7-420d-8b69-bd34e5e18cd9)

# AI Chat Application

A modern, full-stack AI-powered chat application built with Next.js, Supabase, and Google's Gemini AI. This project provides a seamless chat experience where users can interact with an AI assistant, with all conversations securely stored in the cloud.

## 🚀 Features

- **User Authentication**: Secure login and signup with email/password or Google OAuth via Supabase Auth
- **AI-Powered Conversations**: Integrated with Google's Gemini 3 Flash model for intelligent responses
- **Chat Management**: Create, view, and delete multiple chat sessions
- **Real-time UI**: Responsive design with smooth scrolling and typing indicators
- **Persistent Storage**: All messages and chats stored in Supabase database
- **Modern UI**: Built with Tailwind CSS and Lucide React icons
- **Docker Support**: Containerized deployment with multi-stage Docker build
- **TypeScript**: Full type safety throughout the application

## 🛠 Tech Stack

- **Frontend**: Next.js 16, React 19, TypeScript
- **Backend**: Next.js API Routes, Supabase
- **AI**: Google Generative AI (Gemini 3 Flash)
- **Database**: Supabase (PostgreSQL)
- **Styling**: Tailwind CSS
- **Icons**: Lucide React
- **Deployment**: Docker, Vercel

## 📋 Prerequisites

- Node.js 20+
- npm, yarn, pnpm, or bun
- Supabase account and project
- Google AI API key (for Gemini)

## 🔧 Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd chatapp
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   # or
   pnpm install
   ```

3. **Set up environment variables**

   Create a `.env.local` file in the root directory:

   ```env
   # Supabase Configuration
   NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key

   # Google AI API Key
   GEMINI_API_KEY=your_google_ai_api_key
   ```

4. **Set up Supabase Database**

   Create the following tables in your Supabase project:

   - `chats` table:
     - `id` (uuid, primary key)
     - `user_id` (uuid, foreign key to auth.users)
     - `title` (text)
     - `created_at` (timestamp)

   - `messages` table:
     - `id` (uuid, primary key)
     - `chat_id` (uuid, foreign key to chats)
     - `role` (text: 'user' or 'assistant')
     - `content` (text)
     - `created_at` (timestamp)

   Enable Row Level Security (RLS) and create appropriate policies for user data access.

## 🚀 Running the Application

### Development
```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Production Build
```bash
npm run build
npm run start
```

### Docker
```bash
docker-compose up --build
```

## 📖 Usage Workflow

1. **Authentication**:
   - Visit the application and sign up with email/password or Google OAuth
   - Upon successful authentication, you'll be redirected to the chat interface

2. **Creating Chats**:
   - Click the "+ New Chat" button in the sidebar to start a new conversation
   - Each chat session is stored separately for organization

3. **Chatting with AI**:
   - Type your message in the input field at the bottom
   - Press Enter or click Send to submit
   - The AI (Gemini) will generate a response, which appears in the chat
   - Messages are automatically saved to the database

4. **Managing Chats**:
   - View all your chats in the sidebar
   - Click on any chat to switch between conversations
   - Delete chats using the trash icon next to each chat title

## 🏗 Project Structure

```
chatapp/
├── app/
│   ├── api/chat/route.ts      # AI chat API endpoint
│   ├── chat/page.tsx          # Main chat interface
│   ├── login/page.tsx         # Login page
│   ├── signup/page.tsx        # Signup page
│   ├── layout.tsx             # Root layout
│   └── page.tsx               # Home page
├── components/
│   ├── ChatBox.tsx            # Chat message display and input
│   ├── MessageBubble.tsx      # Individual message component
│   ├── Navbar.tsx             # Top navigation bar
│   └── Sidebar.tsx            # Chat list and management
├── lib/
│   ├── gemini.ts              # Gemini AI configuration
│   ├── supabaseClient.ts      # Supabase client setup
│   └── supabaseServer.ts      # Server-side Supabase utilities
├── types/
│   └── index.ts               # TypeScript type definitions
├── public/                    # Static assets
├── Dockerfile                 # Docker build configuration
├── docker-compose.yml         # Docker Compose setup
└── package.json               # Dependencies and scripts
```

## 🔌 API Endpoints

### POST /api/chat
Generates AI responses using Gemini.

**Request Body:**
```json
{
  "message": "Your message here"
}
```

**Response:**
```json
{
  "reply": "AI generated response"
}
```

## 🚀 Deployment

### Vercel (Recommended)
1. Connect your GitHub repository to Vercel
2. Add environment variables in Vercel dashboard
3. Deploy automatically on push

### Docker
```bash
docker-compose up -d
```

### Manual Deployment
1. Build the application: `npm run build`
2. Start the production server: `npm run start`
3. Ensure environment variables are set in your deployment environment

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Troubleshooting

- **Authentication Issues**: Ensure Supabase URL and keys are correct
- **AI Not Responding**: Check your Gemini API key and quota
- **Database Errors**: Verify table schemas and RLS policies in Supabase
- **Build Issues**: Ensure Node.js version is 20+ and all dependencies are installed

## 📞 Support

For support, please open an issue in the GitHub repository or contact the maintainers.
