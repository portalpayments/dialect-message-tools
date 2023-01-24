# Portal Dialect Message Tools - tools and components for Dialect Messaging integrations with Solana

This library contains 3 main parts:

 - A `messaging` library which wraps Dialect and handles common use cases
 - A Svelte component for integrating Dialect's  wallet-based messaging into apps that need chat
 - Receipts for Solana Pay items.

The library is in TypeScript with minimal dependencies.

This is our production transaction parsing code used in [Portal Wallet](https://getportal.app), we're releasing it for the first time here, so bear with us as we get it established as a standalone library!

### Messaging library

Mosy of these are small convenience tweaks to make Dialect easier to use, they'll hopefully be included in a new version of the Dialect SDK, at which point we can delete them!

The library eliminates the need to create the `dialectSDK` item, instead creating the SDK item as needed.

`getOrMakeThread(keyPair, walletAddress)` - creates or retrieves the thread with the user at `walletAddress`

`getMessagesForUser(keyPair, walletAddress)` - retrieves all messages in a thread with the user at `walletAddress`. Will make a thread if needed.

`sendDialectMessage(thread, text)` - send a message to the user on the thread.

`getTransactionsAndMessagesByDays(Array<messages>>)` - people pften want to see their messaging history over time. This takes `messages` - which can be Dialect messsages or anything else with a `date` and `id` key - and  

### A Svelte component for messaging

- New message elements appear at the bottom of the chat area.

- When the chat area isn't scrolled all the way down, existing elements stay on screen (ie, no scrolling happens) when new elements are added

- When the chat area is scrolled all the way down, and new elements are added, the chat area scrolls down.

See the screenshots!

## Receipts for Solana Pay items inside transactions

This library can fetch Solana Pay (ie Decaf Point of Sale) receipts using Dialect, to display inline. See `receipts.ts`.
