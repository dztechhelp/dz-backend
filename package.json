import express from "express";

const app = express();
app.use(express.json());

app.post("/chat", async (req, res) => {
  const msg = req.body.message;

  const response = await fetch("https://api.openai.com/v1/chat/completions", {
    method: "POST",
    headers: {
      "Authorization": "Bearer " + process.env.OPENAI_KEY,
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      model: "gpt-4o-mini",
      messages: [
        { role: "system", content: "Eres soporte técnico. Si no puedes ayudar, manda a WhatsApp." },
        { role: "user", content: msg }
      ]
    })
  });

  const data = await response.json();
  res.json({ reply: data.choices[0].message.content });
});

app.listen(3000);
