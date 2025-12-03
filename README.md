{"variant":"standard","title":"n8n-bluesky-autoposter README","id":"58241"}
n8n-bluesky-autoposter

An automated Bluesky posting workflow built with n8n that pulls content from any RSS feed, uses an AI model (Ollama or other) to reformat it into a short, professional post, and automatically publishes it to Bluesky.

This workflow is fully customizable and can be adapted for:
- News aggregation
- Blog promotion
- Company updates
- Niche content curation
- Educational or research feeds

---

🔧 What this workflow does

1. Runs on a scheduled trigger in n8n
2. Pulls the latest item from an RSS feed
3. Removes duplicate posts (based on the title)
4. Sends the article to an AI agent to rewrite into a short post
5. Logs in to Bluesky using an App Password
6. Publishes the AI-generated post automatically

---

🧩 Workflow Nodes (Overview)

Nodes and purposes:

Schedule Trigger: Runs automatically on a schedule (default: every 1 min) 
RSS Feed Read: Reads articles from the chosen RSS feed 
Remove Duplicates: Prevents reposting previously seen content 
AI Agent + Ollama: Summarizes & rewrites the article 
Code Node: Safely parses AI output 
Set Fields: Adds Bluesky credentials + post text 
Create Session: Logs into Bluesky 
Post to Bluesky: Publishes the post 

---

✅ Requirements

You'll need:

- n8n (self-hosted or cloud, see documentation here: https://docs.n8n.io/hosting/)
- A Bluesky account
- A Bluesky App Password (you can get your's here: https://bsky.app/settings/app-passwords)
- Ollama or other model (optional but recommended, you can get your's here: https://ollama.com/search) for local AI, or a compatible LLM
- An **RSS feed URL**

---

## 🚀 Installation Steps

1. Import the workflow into n8n

- Download the workflow file:  
  "automated-bluesky-post.json"
  
- In n8n:
  - Go to Workflows
  - Click Import
  - Upload the JSON file

---

2. Update the RSS Feed

Open the RSS Feed Read node and add the RSS Feed you want to use (you can find many here: https://rss.feedspot.com/?_src=logo&_origin=cryptocurrency_rss_feeds)

for example:

https://example.com/blog/feed

---

3. Configure Bluesky credentials

In the Set Fields node, update:

$BLUESKY_HANDLE = yourhandle.bsky.social
$BLUESKY_APP_PASSWORD = your-app-password

In the Post to Bluesky node you must also change this line:

"repo\": \"your-handle.bsky.social\"

👉 To get an app password:
1. Go to Bluesky settings
2. Click App Passwords
3. Generate a new one
4. Paste it into the Set Fields node

Do NOT use your main account password.

---

4. Set your AI model

This workflow uses Ollama by default:

phi3_cyber:latest

You can always add any other model, self-hosted or not

You can change this to any model you have installed:

Examples:

llama3
mistral
phi3

Make sure Ollama is running on your system.

---

5. Customize the prompt (optional)

In the AI Agent node you can customize:

- Writing style
- Tone (formal / casual / technical)
- Max length
- Topic focus

It is currently optimized for:
- Professional
- Informative
- Educational
- 250 character limit

---

🕒 Schedule

The workflow currently runs every 1 minute.

To change it:
- Open the Schedule Trigger node
- Change the interval to whatever you prefer

---

📌 Notes & Best Practices

- Keep your RSS feed relevant and high-quality
- Use the Remove Duplicates node to avoid spam
- Monitor the output the first few runs
- Consider adding logging or moderation for production use

---

📄 License

MIT — free to use, modify, and distribute.

---

Built using:
- n8n
- Bluesky AT Protocol
- Ollama / Local LLM
- RSS
