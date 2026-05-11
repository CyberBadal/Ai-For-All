The Hardest Bug:
I struggled with getting the form to "remember" data when the page refreshed. Since I’m not using a login, I had to rely on localStorage.
The Issue: The UI kept flickering or showing empty fields for a split second because the server and the browser weren't in sync.

The Fix: I realized it was a hydration timing issue with Zustand. I ended up writing a small hook to delay the render until the browser data was fully ready, which made the experience feel way more "premium" and stable.

Decision I ReversedAt:
   
first, I wanted to use AI to figure out all the savings.
The Pivot: I realized pretty fast that people don't trust a "guess" when it comes to their budget. If the AI hallucinations a price, the whole tool looks like a toy.
The Result: I ditched the AI for the math and built a hard-coded engine based on real pricing. It’s less "flashy" under the hood, but the numbers are 100% right every time, which is what actually matters for this kind of product.

AI Usage:
I used tools like Cursor to move fast, but I was careful with how I used them:
The Help: I used AI to build out the basic UI components and the boring TypeScript interfaces for all the tool data.
The Manual Work: I wrote all the actual audit logic and the business strategy myself. AI is great for speed, but it’s bad at "product thinking," so I had to handle the strategy manually to make sure it felt like a real startup.  