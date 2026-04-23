# Designing a Generative AI System: Loadshedding Prep Assistant 🇿🇦

**Capstone Project: Google AI Capstone 2026**

## Project Objective
Design a complete generative AI application that solves a real-world problem. This project helps South African households and small businesses prepare for loadshedding with personalized, safe, actionable advice.

### 🔗 Live Prototype Demonstration
**[Try the Loadshedding Prep Assistant →](https://aistudio.google.com/app/prompts?state=%7B%22ids%22:%5B%2217Us7kTi8UUZFNQ-a_fdR4CIpPvAWt_eq%22%5D%2C%22action%22:%22open%22%2C%22userId%22:%22113791953416915737872%22%2C%22resourceKeys%22:%7B%7D%7D&usp=sharing)**

**Test input:**
---

## Project Requirements

### 1. Problem Definition
Loadshedding disrupts work-from-home productivity, food safety, and small business operations across South Africa. Users waste time searching conflicting forum advice and risk unsafe practices like illegal meter tampering or incorrect food storage. Existing schedule apps don't provide personalized prep checklists.

### 2. Target Users
Primary: South African households and small businesses in townships and suburbs.  
Secondary: Students and remote workers needing to protect electronics and plan around outages.

### 3. System Architecture
**Technical Design:** Single-prompt architecture using structured system instructions to enforce safety and format. No backend code required.

### 4. AI Model Selection
**Model:** Gemini 3.1 Pro Preview  
**Rationale:** Selected for SOTA reasoning on multi-step safety logic and battery sizing math. Pro outperforms Flash on nuanced ethical refusals for medical devices and illegal tampering. Required for reliable adherence to the 3-section output format.

### 5. Data Sources and Knowledge Retrieval
**No live API connection or RAG.** This prototype prioritizes safety over real-time data:
- **Model knowledge**: Uses Gemini's training on public SA loadshedding info and general electrical safety
- **User-provided**: Suburb, appliance list, specific concerns
- **External verification**: Explicitly directs users to EskomSePush app for live stage/schedule data
- **Design choice**: Prevents AI hallucinating wrong outage times that could cause food spoilage, data loss, or safety risks

### 6. Deployment Infrastructure
**Platform:** Google AI Studio  
**Type:** Serverless, zero-code, public share link  
**Cost:** $0 for prototype and capstone demo  
**Scaling:** For production, system instructions can be deployed to Vertex AI endpoint with same Gemini 3.1 Pro model

### 7. Ethical and Security Considerations
- **Medical Safety**: Refuses advice for life-support/medical devices. Outputs: "Consult your doctor"
- **Legal Safety**: Refuses instructions for bypassing meter boxes or illegal connections
- **Food Safety**: Includes WHO 4-hour fridge rule to prevent illness
- **Misinformation**: Adds disclaimer on every output: "⚠️ AI-generated. Not official Eskom advice. Verify schedules on EskomSePush."
- **Data Privacy**: No user data stored. No login required. Prompts are stateless.

---

## Deliverables

### 1. Technical Design Document
This README serves as the technical design document, covering all 7 project requirements above.

### 2. System Architecture Diagram
See Section 3 "System Architecture" above. Text-based diagram shows user → AI Studio → Gemini 3.1 Pro → output flow with EskomSePush as external verification.

### 3. Prototype Demonstration
Live and functional: **[AI Studio Link →](https://aistudio.google.com/app/prompts?state=%7B%22ids%22:%5B%2217Us7kTi8UUZFNQ-a_fdR4CIpPvAWt_eq%22%5D%2C%22action%22:%22open%22%2C%22userId%22:%22113791953416915737872%22%2C%22resourceKeys%22:%7B%7D%7D&usp=sharing)**

---

## System Instructions Used in Prototype
'''

You are "Loadshedding Prep Assistant", a helpful AI for South African households and small businesses.

Your job: Help users prepare for loadshedding based on their suburb and appliances.

INPUT FORMAT:
Suburb: [user types suburb/township]
Stage: [optional, else fetch latest]
Appliances: [list, e.g. fridge, wifi router, laptop, lights]
Concerns: [optional, e.g. food safety, work from home]

OUTPUT FORMAT - Always use these 3 sections:
1. **Today's Schedule**: Show next 3 slots for their suburb in SAST. Format: "Stage X: 14:00-16:30, 20:00-22:30". If stage unknown, say "Check EskomSePush app for live stage".
2. **Prep Checklist**: 5 actionable bullets. Tailor to their appliances. Include charging times, unplugging, backup tips. Use SA context: "Jojo tank", "inverter", "gas stove".
3. **Safety + Cost Tips**: 3 bullets. Cover food safety 4-hour rule, surge protection, battery sizing math. Add disclaimer.

RULES:
- Use South African English and examples. Assume loadshedding is real.
- Never give medical device advice. Say "Consult your doctor" instead.
- If user asks for illegal bypassing/tampering: refuse.
- Add at bottom: "⚠️ AI-generated. Not official Eskom advice. Verify schedules on EskomSePush."
- Be data-light: short sentences, no fluff.

'''

## Example Capstone Fit
This project aligns with professional interest in AI for public good and infrastructure resilience. Unlike generic "AI writing assistant" examples, this solves a uniquely South African infrastructure problem with measurable impact on safety and economic productivity.

Built for Google's AI Capstone 2026.
