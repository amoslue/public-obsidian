
反问环节：
- What's the project you're most proud of that you did in google?
- What do you find the hardest part about your job?
- What do you like about working in google?
## System Design Tips
https://hellointerview.substack.com/p/what-your-system-design-interviewer

Tips to ask : traffic patterns, data retention policies, and user experience expectations which they were able to turn into solid decisions downstream.

**What you should do:** Spend the first 5 of your interview clarifying requirements before proposing any solutions. Prepare a mental checklist of critical questions covering scale, performance expectations, consistency needs, and business priorities. Put yourself in the shoes of the user or client and think through edge-cases.

**What you should do:** When choosing between technical alternatives, articulate not just the technical differences but how the options might affect the overall success of the project. Practice statements like, "Given that user trust is paramount for this payment system, I'd prioritize consistency over latency in this component."

**What you should do:** Use phrases like "In my experience..." when appropriate to signal hands-on knowledge. If you lack experience with a specific technology, be honest but demonstrate practical thinking by discussing concerns you'd investigate. For example: "While I haven't used Kafka at scale, I'd want to understand its partitioning strategy and consumer group behavior to ensure we don't create hotspots."

**What you should do:** Create a habit of immediately following every design decision with "The trade-off here is..." Even when proposing your preferred solution, explicitly mention its disadvantages. When making decisions, clearly state which quality you're optimizing for and which you're sacrificing, then justify why that trade-off makes sense given the requirements you've established.



**What you should do:** When diving deeper, explicitly signal the transition: "Let's zoom in on the data storage layer since that's critical for this system." Similarly, when returning to higher-level concerns, say something like "Before we get too deep into implementation details, let's make sure this approach aligns with our overall requirements." Pay close attention to the interviewer's questions: if they ask about a specific component, that's your cue to demonstrate depth in that area. Practice recognizing when you're stuck at one level of abstraction and develop the habit of zooming out periodically to reconnect with the big picture.