# van-shakti-vaani
Voice AI prototype for tribal women forest produce collectors in Chhattisgarh
# Van Shakti Vaani

A voice-based AI prototype to help tribal women forest produce collectors in Chhattisgarh find out the official Minimum Support Price (MSP) of minor forest produce (MFP), in a simple way and in their own language.

## Why this project

Many collectors do not have an easy way to know the correct price for the produce they collect. Van Shakti Vaani aims to give them this information by voice, so that reading and writing are not needed.

## What is in this repository

- **data** - Price sheets for Chhattisgarh MFP items under MSP (2024-25 list: 38 items), taken from the Chhattisgarh State Minor Forest Produce Federation (CGMFPFED) website.
- **bot-instructions** - The instructions that guide the AI assistant.
- **screenshots** - Pictures of the prototype in use.

## How it works

1. A collector asks about the price of an item, for example Mahua flower.
2. The assistant looks up the price in the data sheet.
3. The assistant replies in simple Hindi.

## Free tools used

This prototype is built only with free tools.

**AI and language**
- Google Gemini (Gem) - the assistant that answers questions
- Google AI Studio - testing and improving prompts
- Bhashini - Indian language voice and translation
- NotebookLM - research and reading of source documents
- Perplexity (free plan) - research

**Chat and automation**
- Telegram Bot - the chat channel for collectors
- Make.com (free plan) - connects the steps together
- Voiceflow (free plan) - designing the conversation flow
- Google Apps Script - small automations in Google Sheets

**Data and dashboard**
- Google Sheets - price data
- Looker Studio - dashboard to view prices
- KoboToolbox - collecting field feedback and survey data

**Project**
- GitHub - keeping the project files in one place

## Status

Early prototype, in progress. Prototype target date: 5 December 2026.

## Data note

Prices are copied from the CGMFPFED website and should be checked against the live page before use.

## Author

Sujata Singh
