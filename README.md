# What is this?

*Chat* is an oversimplified Google Gemini-inspired chat user interface. It is a standalone HTML to interact with an LLM API which only supports text messages.

# How it works?

*Chat* expects a mandatory `token` query parameter and accepts an optional `title` query parameter. `token` and `title` will be stored in the session storage which is deleted upon tab/window close. Every message sent to the LLM API includes an authorization bearer token header whose value taken from `token`. The `title` determines the chat window/tab title, which defaults to `Untitled Chat` if nothing is passed. During the chat conversation, response text from the LLM API will be incremented to the UI, except for error responses. This is accomplished by strictly manipulating the DOM **without** storing any array object in the browser local storage or cookies. However, an array variable in the JavaScript keeps track of all the messages which is always sent to the LLM API on every new message request as the context for the LLM.

Currently *Chat* supports parsing Google Gemini's response body via `result.candidates[0].content.parts[0].text;`. For other LLM API like OpenAI or custom models, changes to the code are necessary.

# Which module(s) is used?

*Chat* uses Tailwind CSS `3.4.16` taken from its CDN `https://cdn.tailwindcss.com/3.4.16` then put locally (so it doesn't matter if the CDN breaks as Tailwind suggests not to use its CDN for production).
