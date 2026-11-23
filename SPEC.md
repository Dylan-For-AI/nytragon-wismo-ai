# Message Sorter - Spec

1. Input: one customer message (text, French or English).
2. Output: exactly one category: `order_status`, `return_refund` or `other`.
3. Gemini does the sorting and answers in strict JSON (structured output).
4. Unclear messages go to `other`.
5. Each result is saved in a PostgreSQL table `message_log` (id, message, category, created_at).
6. Test data: 30 invented messages written by hand (10 per category), in a CSV file.
7. Success goal: at least 27 correct out of 30 (90%). To adjust after the first run.
8. The model name comes from `.env` (`GEMINI_MODEL`), never from the code.
9. Out of scope: answering the customer, reading orders, web interface, cloud.
10. Done when: one command runs the 30 messages and prints the score.