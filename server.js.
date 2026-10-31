
const express = require("express");
const fs = require("fs");
const path = require("path");

const app = express();
const PORT = process.env.PORT || 3000;

app.get("/", (req, res) => {
  res.json({
    name: "YisusProtect",
    status: "online",
    version: "1.0.0"
  });
});

app.get("/health", (req, res) => {
  res.json({ success: true });
});

app.get("/script/:id", (req, res) => {
  const id = req.params.id;

  if (!/^[a-zA-Z0-9_-]+$/.test(id)) {
    return res.status(400).send("Invalid script ID");
  }

  const file = path.join(__dirname, "scripts", id + ".lua");

  if (!fs.existsSync(file)) {
    return res.status(404).send("Script not found");
  }

  const content = fs.readFileSync(file, "utf8");

  res.type("text/plain").send(content);
});

app.listen(PORT, "0.0.0.0", () => {
  console.log("YisusProtect online on port " + PORT);
});
