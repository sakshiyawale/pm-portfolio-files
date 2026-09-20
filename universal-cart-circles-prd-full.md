# Universal Cart Circles
### A collaborative decision workspace for family retail purchases

| Field | Details |
|---|---|
| Product area | Google Shopping / Universal Cart |
| Author | Sakshi Yawale |
| Status | Portfolio proposal |
| Date | September 17, 2026 |
| Target release | Not specified — portfolio proposal |
| Primary users | Families coordinating shared retail purchases |
| V1 scope | Retail products only |
| Research basis | Public product documentation, product analysis, and hypotheses; no proprietary Google data or primary user interviews |

---

## Executive summary

Universal Cart Circles is a proposed collaboration layer for Google Universal Cart that helps family members make shared retail decisions. A Circle preserves a small product shortlist, family requirements, structured feedback, trade-off decisions, and purchase ownership, while keeping checkout private and allowing families to continue general conversation in the tools they already use.

Google's Universal Cart is a cross-merchant shopping hub that lets users save products while using Search and Gemini, with YouTube and Gmail planned as additional surfaces. It can track deals, price history, price drops, restocks, and compatibility issues, and it can support Google Pay checkout or a handoff to a merchant's own site. Circles builds on that foundation by solving a missing group-shopping step: turning scattered family opinions into a documented, purchase-ready decision.

> **Product principle:** Make family shopping decisions easier where commerce happens, while keeping broader conversation where relationships already happen.

---

## Background

Universal Cart centralizes product discovery and shopping intent across merchants and Google surfaces. It uses Gemini-powered shopping assistance to monitor prices and availability, and it can surface compatibility concerns for more complex purchases.

However, many retail decisions are not individual decisions. Families often jointly choose refrigerators, furniture, electronics, appliances, school supplies, gifts, clothing, and brand-sensitive household items. Individual family members may have different requirements around budget, dimensions, features, delivery, energy efficiency, brand, color, material, reviews, and return policies.

Today, this process is fragmented across WhatsApp, iMessage, calls, emails, shared notes, retailer websites, and screenshots. These tools are useful for conversation, but they do not create a structured record of the shortlist, requirements, concerns, trade-offs, final decision, and assigned buyer.

**Research limitations:** This portfolio proposal is based on public Universal Cart and Universal Commerce Protocol documentation, an illustrative workflow analysis, and product hypotheses. It does not use proprietary Google data, primary user interviews, or verified Universal Cart usage data. User-behavior claims and metric targets must be validated through usability testing and a limited beta before broad launch.

---

## Problem statement

Families making shared retail purchases struggle to compare product options, preserve individual requirements, and reach a clear buying decision because links, opinions, specifications, and verbal decisions are scattered across calls, messages, notes, email threads, and retailer websites.

The problem is especially acute for high-consideration purchases such as refrigerators, furniture, electronics, appliances, and school supplies, where a wrong choice can lead to unnecessary returns, delayed replacement, repeat research, overspending, and family frustration. Over time, one family member may become the default organizer while others disengage from the decision process.

**Illustrative scenario:** A family needs to replace a refrigerator.
- One parent prioritizes capacity, energy efficiency, and long-term reliability.
- Another prioritizes price, delivery timing, and installation.
- A teenager prefers a water dispenser and a particular finish.
- Product links are shared in a group chat; additional decisions happen over calls.
- A family member who cannot join a call has previously stated that free delivery and a bottom-freezer layout are important, but these requirements are forgotten.
- The group cannot easily determine which models remain viable, which requirements are mandatory, or who should purchase the final selection.

The family repeats research, reopens old links, and risks choosing a product that does not meet important needs.

---

## Opportunity

Universal Cart Circles converts fragmented discussion into a lightweight, shared decision workspace. It is not a replacement for WhatsApp, iMessage, Discord, or family calls; it captures the decision artifacts from those discussions in the place where commerce happens.

A Circle enables family members to:
- Create a purchase-specific workspace.
- Add and compare a small shortlist of products across merchants.
- Capture shared requirements with individual attribution.
- Signal Support, Concern, or No preference on each option.
- Review whether each product meets the family's stated requirements.
- Resolve must-have trade-offs explicitly.
- Record a shared product selection.
- Assign a buyer only with the buyer's acceptance.
- Hand off to private, individual checkout.

The Universal Commerce Protocol is an open standard intended to support commerce interactions such as product discovery, cart building, checkout, and order-related operations; merchants retain their business logic and remain the merchant of record. Circles should therefore improve the group decision stage while preserving merchant fulfillment and individual payment boundaries.

---

## Target users

**Primary persona: Family purchase initiator**
An adult family member who starts or organizes a shared retail decision. They facilitate product research and discussion but do not have unilateral authority to make the final choice.

*Goals:* Gather family needs without repeatedly relaying messages. Compare a manageable shortlist across retailers. Ensure important criteria are considered. Identify where the group agrees and where concerns remain. Make a confident, documented decision.

*Pain points:* Links, screenshots, and prior opinions are buried in chats. Verbal decisions from calls are not recorded. Product specifications are difficult to compare across retailers. Family members' preferences can be forgotten when they are unavailable. The same person repeatedly researches and follows up.

**Secondary persona: Family contributor**
A family member who provides preferences but is not necessarily responsible for research or checkout.

*Goals:* State what matters to them. Know whether their requirement was considered. Review the current shortlist and final decision quickly. Avoid searching old messages or restating their preferences.

**Jobs to be done:**
- When my family is evaluating a retail purchase, I want one shared place to compare a short list of options against our requirements and see the final decision, so that we can choose confidently without losing context across calls, chats, and retailer websites.
- When I cannot participate in a family discussion, I want my preferences to remain visible during product evaluation, so that the group considers them before selecting a product.
- When my family agrees on a product, I want to know who is purchasing it and whether it has been purchased, so that we avoid duplicate orders and repeated follow-ups.

---

## Goals

| Goal | Intended outcome |
|---|---|
| Make shared decisions easier | Families move from scattered options to a clear selection |
| Improve comparison | Families evaluate a limited shortlist against common criteria |
| Preserve requirements | Each member's needs remain visible and attributable |
| Surface trade-offs | Families consciously address unmet must-haves before selecting |
| Maintain collaboration | Input is collected without requiring rigid voting or a single authority |
| Create follow-through | The group knows who will purchase and when the item is complete |
| Protect privacy | Payment and personal-cart details stay individual |

**Non-goals:**
- Replacing WhatsApp, iMessage, Discord, email, or calls as general-purpose communication tools.
- Building a full group chat or social-shopping network.
- Formal majority voting or ranked-choice voting.
- Autonomous product selection or autonomous checkout.
- Split payments, reimbursements, or shared payment credentials.
- Returns, refunds, warranties, shipping, fulfillment, or merchant support.
- Cross-merchant order consolidation.
- Lodging, food delivery, travel planning, or reservations.
- Using private family activity to automatically infer must-haves in V1.

---

## Collaborative decision model

Circles is designed for shared input and explicit trade-offs, rather than an authoritative organizer or a rigid vote.

**Feedback signals**

| Signal | Meaning | Behavior |
|---|---|---|
| Support | "This option meets my needs." | Counted in the decision summary; comment is optional |
| Concern | "This option does not meet one or more of my needs." | Linked to a requirement or accompanied by a short explanation |
| No preference | "I do not have a strong view." | Included as participation, but not counted as positive or negative support |
| No response | Member has not reviewed the option | Visible in the decision summary |

**Requirement types**

| Type | Meaning | Example |
|---|---|---|
| Must-have | A condition that should be addressed before selection | "Fits a 36-inch kitchen opening" |
| Nice-to-have | A preference that improves the product but can be traded off | "External water dispenser" |
| No preference | A product attribute that does not matter to the member | "Color does not matter" |

Every requirement is attributed to its creator. Members can edit or remove their own requirements before a product is selected.

**Trade-off resolution**

A must-have is not an irreversible veto. Families may decide that a trade-off is acceptable, but the trade-off should be deliberate and visible.

When a family is ready to select a product that does not meet an active must-have, the member who added that requirement receives a review prompt:

> "This option does not meet your must-have: External water dispenser. Do you still consider this a must-have for this purchase?"

The member can:
1. **Keep as must-have** — concern remains open.
2. **Accept trade-off** — reclassify it as a nice-to-have and optionally state why.
3. **Remove as no longer relevant** — remove it for the current workspace only.
4. **Suggest an alternative** — add another option or request that the group revisit the shortlist.

A product becomes eligible for selection only when every active must-have is either marked as met or explicitly resolved by its owner.

![Trade-off resolution screen, prompting the requirement owner to keep, accept, remove, or suggest an alternative](./wireframes/screen3-tradeoff.svg)

---

## V1 user journey

![Circle overview screen, showing active purchase workspaces and recent activity](./wireframes/screen1-circle-overview.svg)

1. **Create a Circle** — Any signed-in Universal Cart user creates a private Circle, gives it a name such as "Family Purchases," and invites family members through their Google account or a shareable invitation link.
2. **Start a purchase workspace** — Any Circle member creates a retail purchase workspace, such as "New refrigerator," "Back-to-school supplies," or "Living room sofa." Each workspace has its own shortlist, requirements, feedback, and decision history.
3. **Add products** — Members can add products directly from Search or Gemini, or explicitly share items already in their individual Universal Cart. A personal cart remains private unless the user actively chooses Add to Circle and selects a specific workspace. Each workspace supports up to five active product options.
4. **Add requirements** — Family members add requirements to the workspace and label them as Must-have, Nice-to-have, or No preference. The system attributes each requirement to the member who added it.
5. **Compare and discuss** — The workspace presents products side by side. Members review product information, add short item-attached comments, and mark Support, Concern, or No preference.
6. **Resolve trade-offs** — The system identifies products that miss active must-haves and prompts the relevant requirement owner to keep, waive, downgrade, or revisit the requirement. It does not automatically select a winner.
7. **Select a product** — Any Circle member can initiate selection when the product is eligible. Before confirmation, Circles displays requirement-match status, resolved trade-offs, Support/Concern/No-preference counts, and members who have not responded. The member explicitly confirms the decision, and all Circle members are notified.
8. **Assign a buyer** — Any member may volunteer to buy the selected item, or propose another member, who must accept or decline. Buyer assignment is never automatic.
9. **Checkout and completion** — The accepted buyer starts individual checkout through Google Pay where supported, or is transferred to the merchant's checkout experience. Their payment data stays private. After buying, the buyer marks the product Purchased, which notifies all members and prevents duplicate orders.

---

## Product comparison

Universal Cart Circles uses two layers of comparison: standard information visible for all retail items and category-specific attributes that change by product type.

**Standard fields:** Product name and image, merchant, current price, shipping/delivery cost, estimated delivery date, rating and review count, return-policy summary, price history and deal signal (using existing Universal Cart intelligence), requirement-match summary, family feedback, and unresolved-concern indicator.

![Purchase workspace comparison screen, showing three products side by side against family requirements](./wireframes/screen2-comparison.svg)

**Category-specific fields (examples):**

| Category | Example fields |
|---|---|
| Appliances | Dimensions, capacity, energy rating, installation, warranty |
| Electronics | Core specifications, storage, connectivity, compatibility, warranty |
| Furniture | Dimensions, material, color, assembly, delivery and return terms |
| School supplies | Quantity, brand, school-list compatibility, delivery date |
| Clothing | Size, color, material, fit guidance, return policy |
| Groceries and household essentials | Unit price, package size, ingredients or dietary labels, stock availability |

---

## Functional requirements

| ID | Requirement | Priority |
|---|---|---|
| FR-1 | A signed-in user can create, rename, leave, and delete a private Circle. | Must |
| FR-2 | A Circle creator can invite and remove members. | Must |
| FR-3 | Any Circle member can create a purchase-specific retail workspace. | Must |
| FR-4 | Members can add an eligible product from Search, Gemini, or their personal Universal Cart through an explicit Add to Circle action. | Must |
| FR-5 | A workspace supports up to five active product options. | Must |
| FR-6 | Personal-cart products remain private unless explicitly shared to a Circle workspace. | Must |
| FR-7 | Members can add shared requirements, attributed to their creator. | Must |
| FR-8 | Requirements can be labeled Must-have, Nice-to-have, or No preference. | Must |
| FR-9 | Circles shows whether each product Meets, Does not meet, or has Insufficient data for each active requirement. | Must |
| FR-10 | Members can submit Support, Concern, or No preference for each shortlisted product. | Must |
| FR-11 | A Concern can be linked to a requirement or include a short explanation. | Must |
| FR-12 | Support and No-preference comments are optional. | Must |
| FR-13 | The comparison view displays standard product information and category-specific details where available. | Must |
| FR-14 | The system flags unmet active must-haves and requires their owner to resolve them before selection. | Must |
| FR-15 | Any member can initiate product selection after trade-offs are resolved; the system requires confirmation. | Must |
| FR-16 | The decision summary displays requirements, trade-offs, feedback, and non-responding members. | Must |
| FR-17 | Members can volunteer as buyer or propose another buyer; proposed buyers must accept or decline. | Must |
| FR-18 | An accepted buyer can begin individual checkout or open the merchant product page. | Must |
| FR-19 | The buyer can mark a selected item Purchased, preserving a visible history. | Must |
| FR-20 | Users can mute a Circle and adjust notification preferences. | Should |
| FR-21 | Users can set an optional workspace deadline and reminders. | Should |
| FR-22 | The product shows a transparent "Best fit" indicator based on stated requirements. | Should |
| FR-23 | The workspace shows an optional approved-item budget subtotal. | Should |
| FR-24 | A reusable family preference profile supports brand, delivery, or retailer preferences. | Could |
| FR-25 | A shareable one-tap decision summary can be exported to WhatsApp or iMessage. | Could |
| FR-26 | Gemini summarizes unresolved concerns and recorded trade-offs. | Could |
| FR-27 | Product templates support categories such as appliances, laptops, furniture, and school supplies. | Could |

---

## User stories and acceptance criteria

**US-1: Create a purchase workspace**
*As a family member, I want to create a purchase workspace inside a private Circle so that my family can organize one buying decision without mixing it with other purchases.*
- Any Circle member can create a retail purchase workspace.
- The creator provides a title.
- Each workspace maintains its own products, requirements, feedback, and status.
- Workspaces can be archived after purchase or after the decision is abandoned.

**US-2: Share products**
*As a Circle member, I want to add products from Search, Gemini, or my Universal Cart to a shared shortlist so that my family can compare relevant options in one place.*
- The user explicitly selects a Circle and workspace before sharing.
- The item shows product name, merchant, current price, product link, and available delivery/specification data.
- Personal-cart items are never shared automatically.
- The system limits a workspace to five active options.

**US-3: Capture requirements**
*As a family member, I want to add and prioritize requirements so that my family understands what matters to me when evaluating products.*
- A member can add, edit, or remove their own requirement before selection.
- Each requirement is attributed to its creator.
- Requirements are classified as Must-have, Nice-to-have, or No preference.
- All Circle members can view requirements.
- The comparison table shows product-level match status.

**US-4: Give structured feedback**
*As a family member, I want to mark a product as Support, Concern, or No preference so that I can contribute without creating a long chat thread.*
- A member can submit one feedback signal per product and revise it before selection.
- Concern supports a linked requirement or a short explanation.
- Comments are optional for Support and No preference.
- The product shows feedback counts and non-responding members.
- The feature does not include a general group-chat feed.

**US-5: Resolve trade-offs**
*As a family member who raised a must-have, I want to review a product that misses my requirement so that I can retain it, accept a trade-off, or suggest an alternative before selection.*
- The system identifies unmet must-haves before selection.
- Only the requirement owner can downgrade, remove, or accept a trade-off for that requirement, except for defined account-access exceptions.
- Each resolution is recorded with original requirement, resolution type, actor, timestamp, and optional reason.
- A product cannot become Ready to select while active must-haves remain unresolved.

**US-6: Select collaboratively**
*As a Circle member, I want to confirm a selection after reviewing feedback and trade-offs so that the family has a durable decision record.*
- Any Circle member can initiate selection for an eligible product.
- The product displays decision summary information before confirmation.
- The user must explicitly confirm selection.
- All Circle members receive a selection update.
- A member can reopen a selection before purchase completion; the system captures a reason.

**US-7: Assign a buyer**
*As a Circle member, I want to volunteer to buy a selected product or propose another member as buyer so that the next step is clear without imposing financial responsibility.*
- A member can volunteer as buyer.
- A member can propose another Circle member.
- A proposed buyer can accept or decline.
- Buyer status is Unassigned, Pending acceptance, Assigned, or Declined.
- The feature never automatically assigns a buyer.

**US-8: Checkout privately and close the loop**
*As an accepted buyer, I want to complete checkout privately and mark the item Purchased so that I control payment information while the family knows the purchase is complete.*
- An accepted buyer can start a supported individual checkout flow or open the merchant site.
- No Circle member can view another member's payment credentials or private checkout data.
- The buyer can mark the item Purchased.
- Circles records the completion timestamp and notifies members.
- Purchased items remain visible in workspace history.

---

## Non-functional requirements

| Area | Requirement |
|---|---|
| Privacy | Circles are private by default; only Circle members can view shared products, requirements, feedback, comments, and decision history |
| Payment privacy | Payment credentials, Google Pay details, merchant checkout data, and unshared personal-cart items are never visible to other members |
| Access control | Only Circle members can add products, requirements, feedback, or initiate selection; members can leave, and creators can remove members |
| Explicit sharing | A product cannot be shared from a personal Universal Cart without explicit Circle and workspace selection |
| Trade-off integrity | Only requirement creators can waive or downgrade their must-haves; each resolution is logged |
| Performance | Workspace, shortlist, and comparison view load in under 2 seconds for 95% of requests under normal conditions |
| Synchronization | Product, requirement, feedback, and status updates sync to active members within 10 seconds for 99% of successful actions |
| Product data quality | Missing or stale price, delivery, inventory, or specification data is marked unavailable and includes a last-updated time where possible |
| Accessibility | Core workflows support keyboard-only navigation and screen readers; status is not conveyed by color alone |
| Notification control | Users can mute a Circle or adjust preferences; V1 does not send promotional notifications based on Circle activity |
| Auditability | Current members can view history for item additions, requirement changes, concerns, trade-offs, selections, buyer assignment, and purchase status |

---

## Notifications

| Event | Audience | Default behavior |
|---|---|---|
| Circle invitation | Invited member | Push and in-app |
| Product added | Circle members | In-app only |
| Concern raised | Members who participated in the workspace | In-app only |
| Must-have needs review | Requirement owner | Push and in-app, if enabled |
| Product selected | All Circle members | Push and in-app |
| Buyer proposed | Proposed buyer | Push and in-app |
| Buyer accepts or declines | All Circle members | In-app only |
| Item marked Purchased | All Circle members | Push and in-app |
| No response before optional deadline | Non-responding member | Optional reminder only |

---

## Success metrics

All targets are proposed and require a baseline from beta testing.

**North-star metric: Decision-to-action rate.** Percentage of active Circles that, within 14 days of their first saved option, select a product after every active must-have concern is either satisfied or explicitly resolved, and assign an accepted buyer within 48 hours of selection.

*The 48-hour buyer-assignment window is an internal analytics measure only. It is not displayed as a user deadline, does not block checkout, and should not generate pressure-based prompts.*

**Supporting metrics:**
- Circle activation rate — % of Circles with at least two active members and two products added within seven days
- Preference participation rate — % of members who submit feedback on at least one option
- Requirement coverage — % of selected products where every must-have is met or explicitly resolved
- Median time to selection
- Buyer assignment rate — % of selected products with an accepted buyer within 48 hours
- Purchase completion proxy — % of assigned products marked Purchased within 14 days
- User value rating — post-task agreement with "Circles made this purchase easier to coordinate"

**Guardrails:**
- Unresolved-must-have selection attempts (detects a confusing or bypassed trade-off flow)
- Circle notification mute rate (detects notification fatigue)
- Circle abandonment rate (detects low perceived value or complexity)
- Checkout-start rate after selection (ensures collaboration doesn't create commerce drop-off)
- Return/cancellation rate for Circle-assisted purchases (long-term decision-quality proxy)
- Privacy/access-control complaint rate
- Buyer-assignment decline rate

---

## Assumptions

- Families will use a commerce workspace for high-consideration decisions while retaining existing messaging tools for broader conversation.
- Families are willing to share selected products, requirements, feedback, and decision status with invited members.
- Five product options are sufficient for a useful shortlist.
- Support, Concern, and No preference are enough for V1 feedback complexity.
- Explicit trade-off resolution improves decision confidence.
- Individual checkout is sufficient for V1.
- Merchant data is sufficiently accurate for comparison.

## Dependencies

- Universal Cart catalog and saved-item infrastructure
- Search and Gemini shopping surfaces
- Merchant feeds and UCP integrations
- Google account identity and invitation infrastructure
- Google Pay and merchant checkout handoff
- Notification platform
- Gemini comparison intelligence
- Privacy, legal, security, and trust-and-safety review

## Risks and mitigations

| Risk | Mitigation |
|---|---|
| Families remain in chat and do not use Circles | Integrate Circles directly with product discovery and keep it focused on decision artifacts rather than conversation |
| Circles becomes another noisy communication surface | Default to in-app activity; reserve push notifications for response-required or final-state events |
| A must-have is ignored | Require explicit review and resolution by the requirement owner before selection |
| A member uses a must-have to block a decision indefinitely | Let members retain or revisit their requirement without coercive deadlines; make unresolved status visible |
| Data is missing or inconsistent across merchants | Show freshness and unavailable states; do not imply stale data is current |
| Members are uncomfortable sharing shopping activity | Private-by-default Circles, explicit sharing, and private payment/personal-cart boundaries |
| Buyer assignment feels awkward | Require explicit buyer acceptance and allow decline |
| Best Fit recommendation appears biased or overly authoritative | Keep as Should-have; explain inputs, show alternatives, and never make the selection automatically |
| Scope expands into travel, food, payments, returns, or chat | Maintain retail-only V1 and document future expansion separately |

## Open questions

- What family structures and maximum Circle size should be supported in V1?
- What happens to a must-have when the requirement owner leaves the Circle?
- How should duplicate or nearly identical products be detected?
- Which retail categories have reliable enough standardized attributes for a launch-quality comparison view?
- How should the product represent an item with incomplete or conflicting merchant data?
- What data may be used for a Best Fit indicator without creating privacy or fairness concerns?
- Should workspaces support optional deadlines, and what reminder cadence is helpful rather than intrusive?
- Can merchant checkout reliably return a purchase-completion signal, or should V1 rely on user confirmation?
- Can a member block a product category, merchant, or brand from appearing in a family workspace?
- Should families be able to export a concise decision summary into external messaging tools?

---

## Launch and validation plan

**Internal testing:** Test with internal participants using realistic shared-purchase tasks across appliances, electronics, furniture, school supplies, and household essentials.

**Limited beta:** Recruit 8-12 families for moderated usability testing and a time-bound beta. Ask participants to create a Circle, start a purchase workspace, add at least three products, add requirements, submit feedback, resolve an unmet must-have, select a product, assign and accept a buyer, and explain who can see payment information.

**Beta success criteria:**

| Area | Proposed criterion |
|---|---|
| Core usability | At least 80% of participants complete the add-to-selection flow without moderator assistance |
| Trade-off comprehension | At least 80% correctly explain how unresolved must-haves affect selection |
| Payment privacy | At least 90% correctly understand that Circle members cannot view another member's payment information |
| User value | At least 70% agree that Circles makes shared shopping easier to coordinate |
| Reliability | Updates sync within the stated 10-second target for 99% of successful actions |
| Safety | No critical privacy, authorization, or data-access issues remain open |

---

## Future considerations

**Optional decision modes:** Future Circle types could support family consensus (current V1 model), majority voting (for larger groups, friends, clubs, or coworkers), ranked choice (for groups selecting among many similar options), or organizer decision (for a buyer with explicit responsibility who wants visible input first).

**Category-specific Missions:** Universal Cart may expand to other commerce categories. Rather than mixing retail, lodging, food delivery, and travel into one cart or general chat stream, Circles could later support purpose-bound Missions, e.g., a "Choose lodging" Mission with its own criteria (two bedrooms, pool, under $300/night), producing a shortlist, concerns, selected option, and a designated booker. This is explicitly out of scope for V1.

---

*Status: Portfolio proposal based on public Universal Cart documentation and product hypotheses. Not affiliated with or reviewed by Google.*
