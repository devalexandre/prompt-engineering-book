# Chapter 5: Few-Shot Learning

## Teaching Through Examples

Few-shot learning is one of the most powerful techniques in prompt engineering. Instead of describing what you want, you show the AI through carefully selected examples. This chapter explores how to use examples effectively to train AI models on your specific style, format, and approach.

## Understanding Few-Shot Learning

Few-shot learning works by providing the AI with examples of input-output pairs that demonstrate the pattern you want it to follow. The AI learns from these examples and applies the same pattern to new inputs.

**Structure:**
```
Here are examples of the task:

Example 1:
Input: [example input]
Output: [desired output]

Example 2:
Input: [example input]
Output: [desired output]

Now do the same for:
Input: [your actual input]
Output: [AI generates this]
```

## Basic Few-Shot Implementation

### Example: Email Classification

#### ❌ Ineffective Prompt
```
Classify this email as urgent, normal, or low priority:

"Hi team, the quarterly reports are due next Friday. Please submit them by Thursday so I can review before the deadline. Thanks!"
```

**Problems:**
- No examples of what constitutes each priority level
- Unclear classification criteria
- No context for decision-making

#### ✅ Few-Shot Optimized Prompt
```
Classify emails by priority level based on these examples:

**Example 1:**
Email: "URGENT: Server is down, customers can't access our website. Need immediate attention!"
Priority: Urgent
Reason: System outage affecting customers

**Example 2:**
Email: "Reminder: Team meeting tomorrow at 2 PM in conference room B."
Priority: Normal  
Reason: Standard business communication with clear timeline

**Example 3:**
Email: "FYI: New coffee machine installed in break room. Enjoy!"
Priority: Low
Reason: Informational only, no action required

**Now classify this email:**
Email: "Hi team, the quarterly reports are due next Friday. Please submit them by Thursday so I can review before the deadline. Thanks!"
Priority: ?
```

**Improvements:**
- Clear examples for each category
- Reasoning provided for each classification
- Consistent format demonstrated
- Pattern established for AI to follow

**Expected Output:**
```
Priority: Normal
Reason: Work deadline with reasonable timeline, requires action but not urgent
```

## Advanced Few-Shot Techniques

### Technique 1: Progressive Complexity

Start with simple examples and build to more complex ones:

```
Transform casual language into professional business communication:

**Example 1 (Simple):**
Casual: "Hey, can you send me that file?"
Professional: "Could you please send me the requested file at your earliest convenience?"

**Example 2 (Medium):**
Casual: "The meeting was a total disaster. Nothing got decided and everyone was arguing."
Professional: "The meeting presented several challenges, with differing viewpoints that require further discussion to reach consensus."

**Example 3 (Complex):**
Casual: "I think John's idea is pretty stupid and won't work because he doesn't understand our customers at all."
Professional: "While I appreciate John's creative approach, I have concerns about the proposal's alignment with our customer research findings. I'd like to discuss alternative strategies that better address our target market's documented needs."

**Now transform:**
Casual: "This project is way behind schedule and the client is going to be super mad."
Professional: ?
```

### Technique 2: Format Training

Teach specific output formats through examples:

```
Convert product features into benefit-focused marketing copy:

**Example 1:**
Feature: "256GB storage capacity"
Marketing Copy: "Store thousands of photos, videos, and apps without ever worrying about running out of space"

**Example 2:**
Feature: "Waterproof to 50 meters"
Marketing Copy: "Dive into adventure with confidence—swim, surf, or shower without fear of damage"

**Example 3:**
Feature: "12-hour battery life"
Marketing Copy: "Power through your entire day and into the night without searching for an outlet"

**Pattern:** [Feature] → [Emotional benefit + specific use case + peace of mind]

**Now convert:**
Feature: "Dual-camera system with portrait mode"
Marketing Copy: ?
```

### Technique 3: Style Mimicking

Train the AI to match specific writing styles:

```
Write product descriptions in the style of Apple's marketing:

**Example 1:**
Product: Wireless Headphones
Apple Style: "Immersive sound that moves with you. Advanced noise cancellation meets effortless connectivity. Simply magical."

**Example 2:**
Product: Fitness Tracker
Apple Style: "Your health, reimagined. Precision sensors track every heartbeat, every step, every moment that matters. Beautifully simple."

**Example 3:**
Product: Smart Speaker
Apple Style: "Intelligence that listens. Voice control that understands. Music that fills every corner of your world. Remarkably intuitive."

**Style Elements:**
- Short, impactful sentences
- Emotional language
- Focus on user experience
- Ends with a powerful adjective

**Now write for:**
Product: Wireless Charging Pad
Apple Style: ?
```

## Few-Shot for Different Tasks

### Task 1: Data Extraction

```
Extract key information from customer feedback:

**Example 1:**
Feedback: "I love the product quality but the shipping took forever. Customer service was helpful when I called though."
Extracted Data:
- Product Quality: Positive
- Shipping Speed: Negative  
- Customer Service: Positive
- Overall Sentiment: Mixed

**Example 2:**
Feedback: "Amazing experience! Fast delivery, great packaging, and the product exceeded my expectations."
Extracted Data:
- Product Quality: Positive
- Shipping Speed: Positive
- Packaging: Positive
- Overall Sentiment: Positive

**Now extract from:**
Feedback: "The item works fine but the instructions were confusing and setup took hours."
```

### Task 2: Creative Writing

```
Write opening lines for mystery novels in different subgenres:

**Cozy Mystery:**
"Martha discovered the body while deadheading her prize-winning roses, and her first thought wasn't about calling the police—it was about whether the blood would stain her new gardening gloves."

**Hard-boiled Detective:**
"The rain hammered the city like bullets, and I had a feeling this case would leave me just as full of holes."

**Psychological Thriller:**
"I knew someone was watching me, but every time I turned around, the street was empty—except for the sound of footsteps that matched my own."

**Now write an opening for:**
**Police Procedural:**
```

### Task 3: Technical Documentation

```
Write API endpoint documentation following this pattern:

**Example 1:**
```
GET /api/users/{id}

Description: Retrieves detailed information for a specific user
Parameters:
- id (required): User's unique identifier
Response: User object containing id, name, email, created_date
Example: GET /api/users/123 returns {"id": 123, "name": "John Doe", "email": "john@example.com", "created_date": "2024-01-15"}
```

**Example 2:**
```
POST /api/orders

Description: Creates a new order in the system
Parameters:
- user_id (required): ID of the ordering user
- items (required): Array of product IDs and quantities
Response: Order object with confirmation number and total
Example: POST /api/orders with {"user_id": 123, "items": [{"product_id": 456, "quantity": 2}]} returns {"order_id": 789, "total": 29.99, "status": "confirmed"}
```

**Now document:**
```
PUT /api/products/{id}
(Updates existing product information)
```

## Few-Shot Best Practices

### 1. Choose Representative Examples

Select examples that cover the range of inputs you expect:

**Good Example Set:**
- Simple case
- Complex case  
- Edge case
- Common variation

**Poor Example Set:**
- Three very similar examples
- Only simple cases
- Unrealistic scenarios

### 2. Maintain Consistent Format

Keep the same structure across all examples:

```
**Consistent Format:**
Input: [clear input]
Output: [desired output]
Explanation: [why this output]

**Inconsistent Format:**
Example 1: Input → Output
Example 2: Question: X, Answer: Y
Example 3: [Input] produces [Output] because [reason]
```

### 3. Include Edge Cases

Show how to handle unusual or boundary conditions:

```
Convert temperatures with appropriate precision:

**Normal Case:**
Input: 72°F
Output: 22°C

**Decimal Case:**
Input: 98.6°F  
Output: 37.0°C

**Extreme Case:**
Input: -40°F
Output: -40°C (same in both scales)

**Invalid Case:**
Input: "hot outside"
Output: Error - please provide numeric temperature
```

### 4. Provide Reasoning

Explain the logic behind each example:

```
Classify customer inquiries:

**Example 1:**
Inquiry: "How do I return this item?"
Category: Support
Reasoning: Customer needs help with existing purchase

**Example 2:**
Inquiry: "Do you have this in blue?"
Category: Sales
Reasoning: Customer interested in making new purchase

**Example 3:**
Inquiry: "My order hasn't arrived yet"
Category: Shipping
Reasoning: Customer tracking existing order status
```

## 🎯 Practice Exercises

### Exercise 1: Create Few-Shot Examples
Design a few-shot prompt to teach AI how to write social media captions for a fitness brand. Include examples for:
- Motivational posts
- Product features
- Workout tips
- Community engagement

### Exercise 2: Format Training
Create examples to teach AI your preferred format for meeting notes. Consider:
- How to structure action items
- How to capture decisions
- How to note attendees and roles
- How to prioritize follow-ups

### Exercise 3: Style Matching
Choose a brand or publication you admire and create few-shot examples that capture their writing style. Analyze what makes their style distinctive and demonstrate it through examples.

## 💡 Key Takeaways

- Few-shot learning teaches through examples rather than descriptions
- Use 2-4 examples for most tasks (more examples don't always improve results)
- Include diverse examples that cover your expected input range
- Maintain consistent format across all examples
- Provide reasoning to help AI understand the logic
- Progress from simple to complex examples when teaching difficult concepts
- Edge cases and error handling examples prevent unexpected outputs
- Few-shot learning is particularly effective for style, format, and pattern-based tasks

## 🔗 Next Steps

In Chapter 6, we'll explore chain-of-thought reasoning—how to get AI models to show their work and think through complex problems step by step.

---

*"Show, don't tell—few-shot learning turns examples into expertise."*