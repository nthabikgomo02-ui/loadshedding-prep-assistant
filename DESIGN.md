# Loadshedding Safety AI - Technical Design Document
**Google AI Essentials Capstone | Nthabiseng Kgomo**

## 1. Problem Definition
Stage 6 loadshedding in South Africa creates life-threatening risks: insulin spoils for diabetics, families use unsafe gas heaters causing fires, and illegal meter-tampering instructions spread online. Standard LLMs provide generic advice that ignores SA-specific harm patterns.

## 2. Target Users
| User Group | Risk Profile | Need |
| --- | --- | --- |
| SA Households | Townships + suburbs | Safe action during outages |
| High-risk medical | Diabetics, CPAP users | WHO-compliant guidance |
| Community leaders | Sharing info on WhatsApp | Accurate, shareable safety tips |

## 3. System Architecture

## 4. AI Model Selection
**Model**: Google Gemini 1.5 Flash via AI Studio
**Why**: 
1. Strong instruction-following for safety constraints
2. Low latency for crisis queries 
3. Free tier accessible to SA developers
4. Better refusal training than GPT-3.5 on SA-specific illegal requests like "bypass prepaid meter"

## 5. Data Sources & Knowledge Retrieval
| Source | Used For | Method |
| --- | --- | --- |
| WHO Guidelines | 4-hour fridge safety rule | Hardcoded in system prompt |
| EskomSePush patterns | Medical device planning | Referenced in prompts |
| SA incident data | Gas heater + cable theft risks | Context examples in prompt |
**Future**: RAG integration with live Eskom API

## 6. Deployment Infrastructure
**Current**: Prototype in Google AI Studio + Public GitHub docs
**Production path**: 
1. Gemini API → Cloud Run
2. WhatsApp Business API via Twilio for township access
3. Zero user data stored = POPIA compliant

## 7. Ethical & Security Considerations
| Risk | Mitigation |
| --- | --- |
| Illegal requests | Hard refusal: "I can't help bypass meters. That's illegal and risks fire." |
| Medical misinformation | Cite WHO only. Add "Consult clinic" for insulin/diabetes |
| Privacy | No chat logs stored. Demo links sanitized to remove userId |
| Bias | Tested prompts for township vs suburb scenarios. Same safety standard |
| Over-reliance | Responses end with: "If life-threatening, call emergency services" |

## Impact
Distinction-level capstone applying Responsible AI to prevent real harm during South Africa's infrastructure crisis.
