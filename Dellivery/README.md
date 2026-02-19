Mad Restaurant AI Assistant: Technical Documentation & Implementation Guide

🏗 System Architecture
The assistant operates as a coordinated system rather than a linear bot, leveraging a tool-augmented LLM architecture:

Logic Core: AI Agent node utilizing the GPT-4o model.

Memory Management: Simple Memory (Buffer Window) retaining a 30-message context window to ensure continuity in complex order dialogues.

Data Integration: Dual-node Google Sheets integration for real-time menu retrieval (Get_menu) and structured order logging (Order).

Regional Context: Hardcoded logic for Phuket Island operations with a setZone configuration for Asia/Bangkok (ICT).

🛠 Functional Components
1. Menu Retrieval (Get_menu)
The assistant accesses a centralized Google Sheet to provide up-to-date pricing and ingredients.

Data Source: Sheet ID ...xfX9jY.

Mechanism: When a user inquires about food, the assistant queries the "menu" sheet to prevent hallucinations of non-existent items.

2. Order Processing (Order)
Once the assistant confirms the order details, it executes an append operation to the master "Orders" sheet.

Captured Fields: Date/Time, Item Name, Phone Number (+66 format), Address, and Customer Name.

Destination: Sheet ID ...jbl4, Tab: Заказы.

📈 Optimization & Scaling Guide
To transition this assistant from a prototype to a production-grade service, the following refinements are recommended:

Conversational UI (CUI) Enhancements
Command Shortcuts: While the assistant handles natural language, implementing a Reply Keyboard in the Telegram Trigger node for "View Menu" or "Start Order" will reduce user friction.

Formatting Stability: The current setup uses Markdown v1. For better reliability with special characters (common in addresses and prices), consider switching the Telegram output to HTML or MarkdownV2.

Data Integrity & Validation
Strict Phone Validation: Update the System Message to mandate a check for the +66 prefix before triggering the Order tool.

Order Confirmation Step: Modify the workflow instructions to require a "Final Summary" message. The assistant should list all items and the total price, asking for a final "Yes" before writing to the Google Sheet.

Inventory Management
Stock Status: Add a "Status" column to your Menu Google Sheet. Update the Get_menu tool description so the assistant knows to inform customers if a specific roll is currently "Sold Out."

⚙️ Deployment Settings
Telegram Parse Mode: Markdown.

Timezone: Asia/Bangkok.

Prompt Constraints: The assistant is strictly prohibited from altering prices or revealing internal backend functions to the end-user.
