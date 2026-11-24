# Van Shakti Vaani

**A voice-ready AI price, livelihood and policy assistant for tribal women forest produce collectors in Chhattisgarh**

Author: Sujata Singh
Year: 2026
Status: Academic prototype, built with free tools only. Not yet tested with collectors.

---

## What is this project?

Tribal women collect minor forest produce (MFP) such as mahua flower, chironji, lac, honey and tamarind. The official Minimum Support Price (MSP) is published as a long web table by the Chhattisgarh State Minor Forest Produce Federation (CGMFPFED). It is hard to read on a phone, and it does not say how to store produce, what products can be made from it, which schemes apply, or where to sell.

Van Shakti Vaani turns that table, together with checked guidance on livelihoods and policy, into short answers in simple Hindi on Telegram.

## The two verticals

**Vertical 1: Official MSP price assistant**
Answers "What is the rate for mahua flower?" with the base MSP, the state bonus and the final rate per kg, only from the checked 38-item list. If an item is not on the list, it says so. For the 3 items whose page rate does not add up (see "Data audit" below), it does not quote the rate and asks the user to confirm with the Federation.

**Vertical 2: Livelihood, value-addition and policy guide**
Answers questions on clean harvesting and storage, products Self-Help Groups can make (for example deseeded tamarind), government schemes (MSP for MFP, PM Van Dhan Vikas Yojana, FRA, PESA), where to sell (village or haat, Van Dhan Vikas Kendras, the Federation, Chhattisgarh Herbals) and the rules for selling to private buyers. It covers 15 key MFPs and 6 policy topics. It never gives private trader phone numbers.

## How it works

1. **Google Sheets** holds the 7-tab knowledge base. This is the only source of truth.
2. The checked sheet content is placed **directly in the Gemini prompt**, so the assistant answers only from it.
3. A **Telegram bot** takes the question as text. Voice-note questions are added where they work.
4. **Make.com** connects Telegram to the **Gemini API** (called with a free Google AI Studio key) and sends the answer back.
5. **Looker Studio** reads the same sheet and shows a dashboard for coordinators and trainers.

Telegram text replies are the reliable core. Telegram voice-note questions are added where they work. Hindi voice replies with Bhashini are a stretch goal, and text is always the fallback.

Note: a Gemini Gem is used only to test the prompt, because a Gem cannot be connected to Make.com. The live bot uses the Gemini API.

## The 7-tab knowledge base

| Tab | What it holds |
| --- | --- |
| Summary | Key counts calculated by formula |
| 38 MSP items 2024-25 | Base MSP, state bonus, final rate, bonus flag, arithmetic check, bought in 2024-25 |
| Items bought per year | Number of items bought each year, 2014-15 to 2024-25 |
| Cautions | Audit notes on counts, tendu leaf, other trade and the 3 mismatches |
| Harvesting_and_EndUse | Collection and storage tips, end products and selling rule for 15 key MFPs |
| Govt_Policies_and_Selling_Rules | 6 policy topics with simple Hindi summaries |
| Procurement_Centres_and_Contacts | 4 levels of places to sell and official contacts |

## Key figures from the data

- 38 items on the 2024-25 MSP list: 19 with a state bonus and 19 without
- 14 items bought in 2024-25 (provisional, to 31 December 2024, season still in progress)
- Peak of 38 items bought in 2021-22
- Highest final rates: Kusumi Lac Rs 300/kg and Honey Rs 225/kg. Lowest: Bhelwa Rs 9.75/kg

## Data audit: please read

For three items, the final rate on the Federation page equals base MSP **minus** the state bonus, not plus:

| Item | Base + bonus | Final rate on page |
| --- | --- | --- |
| Van Jeera Seed | Rs 77 | Rs 63 |
| Satavar Root (Dry) | Rs 114 | Rs 100 |
| Van Tulsi Seed | Rs 17.50 | Rs 14.50 |

This may be an entry error on the page. The bot does not quote these rates and advises confirmation with the CGMFPFED.

Also still to be confirmed with the Federation: the Specified or Non-Specified status of each item, and the centre contacts. Any item whose status is not confirmed is marked "pending confirmation" in the sheet, and the bot says so instead of giving a selling rule.

## Free tools used

**Core build**
- Google Sheets (knowledge base)
- Google Gemini API through Google AI Studio (the assistant)
- Telegram Bot, created with BotFather (the chat interface)
- Make.com, free plan (connects Telegram, Sheets and Gemini)
- Looker Studio (dashboard)
- GitHub (project files)

**Used for testing and research**
- Gemini Gem (testing the prompt only)
- NotebookLM (reading and organising sources)
- Perplexity, free (background research)

**Stretch goal**
- BHASHINI (Hindi speech-to-text and text-to-speech)

**Considered but left out of the core build to protect the 5 December 2026 date**
- Voiceflow
- KoboToolbox

Free plans have limits, so please check the current limits of Make.com and Gemini before heavy use.

## Repository contents

```
van-shakti-vaani/
├── README.md
├── data/          the knowledge base files
├── prompts/       every version of the system prompt
├── flow/          notes and screenshots of the Make.com flow
├── screenshots/   bot chats, dashboard, sheet
└── report/        final report and demo video link
```

Folders are added as each part is completed.

## Responsible use of data and AI

- Only public government price data, policy summaries and official institutional contacts are stored.
- No collector's name, phone number, address or ID number is collected. Testing uses sample questions from the project team only, because Telegram messages carry usernames and voice notes are personal data.
- The assistant never lists unverified private trader phone numbers.
- It gives public price and scheme information only. It does not give legal or financial advice and does not promise that a buyer will pay the MSP.
- Every test answer is checked against the sheet and marked correct, wrong or unclear.

## Limitations

- This is a prototype and has not been tested with collectors.
- Prices and rules were read from the Federation page on 8 November 2026 and must be checked against the live page before any real use.
- Answers depend on the checked sheet. The prompt tells the assistant to answer only from it, and testing checks this, but no AI tool is perfect.
- Hindi voice replies are not part of the core build.

## Future scope

- Field validation with tribal women Self-Help Groups and Van Dhan Vikas Kendras
- Chhattisgarhi and tribal languages
- Hindi voice replies through Bhashini, and low-bandwidth or offline voice delivery
- A routine for refreshing rates, rules and contacts whenever a new price list or circular is published

## Sustainable Development Goals

SDG 1 (No Poverty) and SDG 10 (Reduced Inequalities), with secondary links to SDG 5 (Gender Equality) and SDG 9 (Industry, Innovation and Infrastructure).

## Sources

- Chhattisgarh State Minor Forest Produce Federation, Minimum Support Price Scheme page: https://cgmfpfed.org/new/msp_scheme.php (read 8 November 2026)
- Ministry of Tribal Affairs, PIB, inclusion of 23 additional MFP items in the MSP list, 29 May 2020
- Ministry of Tribal Affairs, operational manual for marketing of MFP through MSP, 25 January 2014
- Digital India BHASHINI Division, PIB, 12 March 2026
- Down To Earth, "In Chhattisgarh's forest villages, tribal women carry the labour but middlemen take the margins" (accessed 23 November 2026)

The full reference list is in the project synopsis.
