<img width="548" height="245" alt="image" src="https://github.com/user-attachments/assets/62a65239-8ebe-4b4b-9773-e32e41e0e286" />

# 🚀 GHL → n8n → Vapi Automation Workflow

Automate your lead follow-up process by connecting **Go High Level (GHL)**, **n8n**, and **Vapi**.  
When a new opportunity is created in GHL, this workflow automatically triggers a voice call from your **Vapi AI assistant** 📞🤖.

---

## 🧾 Requirements

### 🏗️ Go High Level (GHL)
- A **Go High Level account**
- **Developer private app** enabled
- **API credentials** added to your n8n instance
- **Webhook URL** from n8n added to your GHL private app

### 🎙️ Vapi
- A **Vapi account** with available credit
- A **connected phone number** to make outbound calls
- An **AI assistant** set up and ready to call
- Your **Vapi API key**

---

## 🔗 Useful Links
- [📘 GHL Docs](https://highlevel.com/docs)
- [🤖 Vapi Docs](https://docs.vapi.ai)
- [⚙️ n8n GHL Credentials Setup](https://docs.n8n.io/integrations/credentials/go-high-level/)

---

## 🔄 Workflow Breakdown

### 1️⃣ Trigger: **GHL Opportunity Created**
- Triggered via a **Webhook (POST)** from Go High Level.
- The webhook URL must be configured in your **GHL Private App**.
- Activates whenever a new **Opportunity** is created.

---

### 2️⃣ Get a **GHL Contact**
- Retrieves the contact details from your GHL CRM using the `contactId` from the opportunity.
- Data includes:
  - 📞 Phone number  
  - 👤 Name  
  - 🧩 Custom fields  

---

### 3️⃣ Wait ⏳ 5 Minutes
- Introduces a short delay before making the call.
- Prevents immediate outreach and allows:
  - Data synchronization  
  - Time for any internal automations or follow-ups  

---

### 4️⃣ Set **Vapi Fields** (Manual Step)
Define your key Vapi fields in n8n before the call:
| Field | Description |
|-------|--------------|
| `vapiPhoneNumberId` | ID of the phone number making the call |
| `vapiAssistantId` | ID of the Vapi assistant handling the call |
| `vapiApi` | Your secure Vapi API key |

---

### 5️⃣ Start **Outbound Vapi Call** 📞
- Sends a **POST** request to:  
  `https://api.vapi.ai/call`
- Payload includes:
  ```json
  {
    "assistantId": "vapiAssistantId",
    "phoneNumberId": "vapiPhoneNumberId",
    "customer": {
      "number": "+1234567890",
      "name": "John Doe"
    }
  }
Once triggered, your Vapi AI assistant will call the lead directly 🤖💬.

✅ Summary
This n8n automation seamlessly connects:

🧠 Go High Level CRM + ⚙️ n8n + 🎙️ Vapi Voice AI

Whenever a new opportunity is created in GHL:

n8n grabs the contact details

Waits a few minutes

Launches a personalized AI voice call via Vapi

🎯 Perfect for instant engagement, higher conversions, and hands-free follow-ups!

💡 Pro Tip
Add additional nodes to:

✉️ Send a confirmation SMS after the call

🗒️ Log call results in GHL or Google Sheets

📊 Track performance in your dashboard

