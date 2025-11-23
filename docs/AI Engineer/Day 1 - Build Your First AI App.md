# Build Your First AI App

So you finally decided to become an AI Engineer?

Perfect.

Today marks **Day 1** of your journey, and trust me — if you follow this guide step-by-step, by the end of the day you will have built your **first real AI application**, the exact same way developers at top US startups do it.

No theory.

No fluff.

Just real development.

Let’s begin. 🔥

---

# ⭐ **DAY 1 — Your AI Engineering Journey Begins**

AI engineering is not about reading, it's about **building**.
Today you will:

- Set up your developer environment
- Install your tools
- Write your first API call
- Build a reusable `askAI()` function
- Run your own mini assistant

This is Level 0 → Level 1.

Let’s go.

---

# ✅ **STEP 1 — Set Up Your Workspace (10 minutes)**

Before anything else, install these 3 things (if you haven't already):

### ✔ Node.js LTS

### ✔ VS Code

### ✔ Git

These are industry-standard tools — the entire AI dev ecosystem runs smoothly with this trio.

Now, create your project folder:

```bash
mkdir -p ~/ai-roadmap/day1/
cd ~/ai-roadmap/day1/
```

Inside it, create a folder:

```bash
mkdir mini-assistant
cd mini-assistant
npm init -y
npm install openai dotenv
```

You just created your **first AI project environment**.

---

# ✅ **STEP 2 — Get Your OpenAI API Key (5 minutes)**

1. Go to the OpenAI Platform
2. Open **API Keys**
3. Generate a new key
4. Copy it

Now create an `.env` file in your project:

```
OPENAI_API_KEY=your_key_here
```

Congrats — you’ve done what every professional AI engineer does on day one.

---

# ✅ **STEP 3 — Your First API Call (20 minutes)**

Inside your project folder, create a new file:

### `index.js`

Paste this:

```js
import OpenAI from "openai";
import dotenv from "dotenv";
dotenv.config();

const client = new OpenAI({ apiKey: process.env.OPENAI_API_KEY });

async function run() {
  const response = await client.chat.completions.create({
    model: "gpt-4o-mini",
    messages: [
      { role: "system", content: "You are scriptshady's personal AI guide." },
      {
        role: "user",
        content: "Tell me a short motivational line to start my AI journey.",
      },
    ],
  });

  console.log("AI Says:", response.choices[0].message.content);
}

run();
```

Run it:

```bash
node index.js
```

If your terminal prints a motivational message…

🎉 **WELCOME — You just made your first AI call.**
You’re officially an AI developer now.

---

# ✅ **STEP 4 — Build Your First Reusable AI Function (30 minutes)**

This is how real AI products are built — reusable components.

Let’s build yours.

### Create `assistant.js`:

```js
import OpenAI from "openai";
import dotenv from "dotenv";
dotenv.config();

const client = new OpenAI({ apiKey: process.env.OPENAI_API_KEY });

export async function askAI(message) {
  const res = await client.chat.completions.create({
    model: "gpt-4o-mini",
    messages: [
      { role: "system", content: "You are an intelligent helpful assistant." },
      { role: "user", content: message },
    ],
  });

  return res.choices[0].message.content;
}
```

### Now create `test.js`:

```js
import { askAI } from "./assistant.js";

(async () => {
  const reply = await askAI("Explain embeddings in very simple words.");
  console.log("AI:", reply);
})();
```

Run it:

```bash
node test.js
```

If the reply prints →
🔥 **You have officially built a modular AI engine.**

This one concept alone is used in chatbots, RAG systems, assistants, developer tools, and AI startups.
