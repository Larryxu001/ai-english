# AI English

An AI-assisted English-learning web app with personalized study content, a vocabulary notebook, spaced repetition, quizzes, conversation practice, and grammar tools. The repository also includes reading and listening practice pages.

## Features

- Learning profiles with CEFR levels A1–C2 and age-group preferences
- AI-generated vocabulary, phrases, and sentences
- A saved-word notebook with FSRS spaced-repetition scheduling
- Quizzes, AI conversation practice, and grammar analysis
- Reading, listening, and text-to-speech tools
- Multiple AI providers: OpenAI, Anthropic, Google, DeepSeek, Kimi, MiniMax, and GLM
- Supabase authentication and storage, with localStorage used before login

The application currently uses a primarily Chinese interface for English learners.

## Technology Stack

Next.js 16 App Router, React 19, TypeScript, Tailwind CSS v4, shadcn/ui, Vercel AI SDK, Supabase, and `ts-fsrs`.

## Getting Started

Install the dependencies:

```bash
npm install
```

Configure the Supabase project values in `.env.local`:

```dotenv
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
```

The client initializes Supabase during startup. Authenticated storage expects the `words`, `profiles`, and `api_keys` tables used by `lib/storage/supabase.ts`; database schema migrations are not included in this repository.

Start the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000). In Settings, choose a learning level and configure an AI provider before using AI-powered features.

## Storage and API Keys

Guest data uses browser localStorage. When a user is signed in, the Supabase adapter stores the learning profile, saved words, and configured API keys in the connected Supabase project. AI requests pass through the application's API routes to the selected provider.

Review the Supabase schema, access policies, and credential-storage behavior before using real provider keys or deploying for other users. Never commit credentials to the repository.

## Development Commands

```bash
npm run dev
npm run build
npm start
npm run lint
```

## Project Structure

- `app/`: Pages and server API routes
- `components/`: Layout and UI components
- `contexts/` and `hooks/`: Profile, learning, speech, and notebook state
- `lib/ai/`: AI provider configuration and model creation
- `lib/prompts/`: Learning prompt templates
- `lib/storage/`: Local and Supabase storage adapters
- `lib/supabase/`: Supabase client setup

## Framework Resources

This project was bootstrapped with [Next.js](https://nextjs.org) and [create-next-app](https://nextjs.org/docs/app/api-reference/cli/create-next-app).

- [Next.js Documentation](https://nextjs.org/docs)
- [Learn Next.js](https://nextjs.org/learn)
- [Next.js GitHub repository](https://github.com/vercel/next.js)
- [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying)
- [Next.js font optimization](https://nextjs.org/docs/app/building-your-application/optimizing/fonts)
- [Geist font](https://vercel.com/font)
- [Vercel deployment platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme)
