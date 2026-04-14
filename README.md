# SaaS — Business Idea Generator

Full-stack app from Week 1 production: [Next.js](https://nextjs.org) **Pages Router** (TypeScript, ESLint, Tailwind) with a **FastAPI** backend under `api/`, deployed on [Vercel](https://vercel.com).

## Prerequisites

- [Node.js](https://nodejs.org/) (LTS recommended)
- A [Vercel](https://vercel.com) account
- An OpenAI or OpenRouter API key (for the Python API)
- [Vercel CLI](https://vercel.com/docs/cli): `npm install -g vercel`, then `vercel login`

## Create the project (Pages Router)

From the directory where you want the folder `saas` to appear, run:

```bash
npx create-next-app saas --typescript --eslint --tailwind --no-src-dir --no-app --no-agents-md --no-react-compiler --no-import-alias
```

This scaffolds **Pages Router** (`--no-app`), TypeScript, ESLint, Tailwind, files at the project root (no `src/`), and no custom import alias.

Then open the `saas` folder in your editor. Typical layout:

- `pages/` — routes and `_app.tsx` / `_document.tsx`
- `styles/globals.css` — global styles (including Tailwind)
- `public/` — static assets

If you use a **Python FastAPI** backend at `/api`, delete the sample Next.js route handlers so they do not conflict: remove the `pages/api` folder. Add `api/` at the repo root with `requirements.txt` and your FastAPI app (`api/index.py`).

## Local development

```bash
cd saas
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000). The course often validates the **deployed** preview so the Next.js frontend and Python backend match production routing.

## Deploy on Vercel

1. **Link the directory** (once per clone or machine):

   ```bash
   cd saas
   vercel link
   ```

   Answer the prompts: set up and link → your scope → **no** to linking an existing project (first time) → project name (for example `saas`) → code location = current directory (press Enter).

2. **Add the OpenAI key** (required for the sample API):

   ```bash
   vercel env add OPENAI_API_KEY
   ```

   Paste the key and select all environments (development, preview, production) when asked. 
   
   **NB:** Even though keys are sensitive, do not indicate they are sensitive when adding to Vercel's secret manager, else the key addition will fail.

3. **Preview deploy**:

   ```bash
   vercel .
   ```

   If you already ran `vercel link`, choose **no** when asked to set up a new project again.

4. **Production**:

   ```bash
   vercel --prod
   ```

   Use the printed URL to open the live app.