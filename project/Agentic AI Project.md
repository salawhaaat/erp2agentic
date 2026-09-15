Week 1

Amazon AWS
Context
Global cloud computing and digital infrastructure provider. Millions of customers across 190+
countries and regions, offering 200+ services spanning compute, storage, databases,
networking, analytics, AI, and security. FY2025 revenue approximately $130B;
consumption-based services delivered through AWS regions, availability zones, and edge
locations worldwide.
Net income 2025 - $77.7B
Operating margin 2025- 11.2%
Amazon’s cloud-computing platform
Backbone
ERP + bespoke internal systems + data warehouses/lakes + BI tools + spreadsheets
Customer Accounts → Service Provisioning → Usage/Metering → Pricing → Billing → Payment →
Financial Systems
- no fully unified data model yet. Single source of truth = the controlled general ledger and
consolidation record for financial reporting; operational truth remains distributed across
service-level systems, cost-allocation pipelines, planning tools, and spreadsheets.
Place it
AWS is clearly cloud-based and operates a globally distributed infrastructure. Its services serve
many industries rather than being designed for only one vertical. AWS supports startups,
enterprises, government organizations, and academic institutions across many industries.
AWS should therefore be viewed as a Tier 1, generalist, cloud-service platform.
Trace one flow
(O2C):
Customer creates AWS account
↓
Valid payment method? ← DECISION POINT
(No → can't activate / Yes → account live)
↓
Customer turns on a service

(e.g. spins up a server)
↓
AWS tracks usage every second ← CONTROL POINT
(fact born: this usage is now recorded and owned)
↓
End of month: AWS adds it all up
↓
Invoice sent automatically
↓
Payment collected automatically
↓
Payment go through? ← DECISION POINT
(No → warning → service shut off / Yes → done)
Classify the model
AWS’s model best fits the unification stance (high standardization, high integration)
Process standardization is high, they operate in the same, standardized way across geographic
locations
AWS’s processes are also highly integrated through customer, account, usage, security, and
billing information. E.g. usage is monitored, the customer’s account and permissions are verified
Name the leverage gap: Cost Allocation & Transparency
AWS automatically records usage and generates detailed billing data at scale. However, AWS
documentation shows that customers must define, create, apply, and activate cost allocation
tags to organize resource costs into meaningful business categories. This adds management
effort and may reduce cost transparency when costs need to be attributed across teams,
projects, or business units.

Week 2

Company: Sweetgreen
Breakout 1
Backbone Process: Order-to-Cash
Customer places order → Payment authorized → Order sent to kitchen → Meal prepared
→ Order checked/packed → Pickup or delivery → Customer receives order → Revenue
captured
Order → Payment → Preparation → Quality Check → Pickup/Delivery → Complete
| Lens  | Value Leak  | Why it matters  | Thread  |
| ----- | ----------- | --------------- | ------- |
Frustration  Customer's order is  Customer may complain,  Customer
|     | incorrect or missing an  | request a remake/refund, or be  |     |
| --- | ------------------------ | ------------------------------- | --- |
|     | ingredient               | less likely to return           |     |
Time  Orders pile up during lunch  Creates congestion, slows  Customer +
rush and customers wait  throughput, and hurts the  Operations
|     | longer than promised  | customer experience  |     |
| --- | --------------------- | -------------------- | --- |
Cost  Incorrect orders have to be  Sweetgreen loses ingredients,  Operations +
|     | remade  | labor time, packaging, and  | Cash  |
| --- | ------- | --------------------------- | ----- |
potentially delivery costs
Quality  Employee prepares the  Reduces order accuracy and  Customer +
|     | wrong customization or  | consistency  | Operations  |
| --- | ----------------------- | ------------ | ----------- |
leaves out an ingredient
Biggest overlap: Order accuracy during preparation
This leak appears under multiple lenses.
Frustration: The customer receives something different from what they ordered.
Time: Employees have to stop and remake the meal, while the customer waits longer.
Cost: Ingredients, labor, and packaging are used twice.
Quality: The final product does not match the customer's specifications.

Threads affected
Customer + Operations + Cash
One fix that pays three times
Sweetgreen could improve the way customized orders are displayed and verified during
preparation—for example, clearer digital kitchen screens or a quick final-order verification
before handoff.
Better order visibility → fewer preparation errors → fewer remakes → faster throughput
→ lower food/labor waste → happier customers
Conclusion
The largest value leak in Sweetgreen's Order-to-Cash process is order
accuracy during meal preparation. It affects Frustration, Time, Cost, and
Quality while touching all three threads: Customer, Operations, and Cash.
Improving order visibility and verification at the preparation stage would
reduce remakes, shorten wait times, lower waste, and improve customer
satisfaction.
This one is also easy to defend in class because everyone understands the process
immediately, without needing specialized knowledge of the company.
Breakout 2
Leak 1 — Order accuracy during preparation
What happens: A customized salad/bowl is prepared incorrectly, an ingredient is missed, or the
wrong order reaches the customer.
Why this one matters: This is where Sweetgreen's value proposition is actually delivered.
Customers are paying for a fast, customized, consistent meal. If the physical meal doesn't
match the digital order, most of the value created by the ordering experience disappears.

It hits all three threads:
Customer: dissatisfaction and lost trust
Operations: remakes and workflow disruption
Cash: wasted ingredients, packaging, labor, refunds/credits
Leak 2 — Peak-period kitchen congestion
What happens: During lunch rush, digital, delivery, and walk-in orders compete for the same
kitchen capacity. Orders accumulate faster than employees can complete them.
Why this one matters: Sweetgreen's business depends heavily on throughput. A bottleneck
during the most valuable hours means the company isn't just making customers wait—it is
limiting how many orders the restaurant can economically fulfill.
It hits:
Customer: longer-than-promised waits
Operations: queues, employee pressure, bottlenecks
Cash: lost throughput and potentially abandoned/canceled orders
Our backbone fails to leverage at kitchen execution: Sweetgreen generates demand
digitally faster than its kitchens can reliably absorb it, costing throughput, operating
margin, and customer trust.
Breakout 3
Who co-designs it
The redesign must be co-designed by the frontline team members and shift managers who
currently absorb the stress of the lunch rush and the frustration of remaking incorrect bowls.
Because this redesign replaces manual, memory-based assembly with an event-driven,
tech-enabled make-line, the people navigating the current bottlenecks must help reshape the
process. They will define how fresh ingredients are prepped for the new system and how the
final human touches—like adding avocado or handing off the bag—are managed without
creating new queues.
The standardization tax
This redesign imposes a steep standardization tax: it strips line workers of their physical
autonomy over portioning and pacing. The new system dictates the exact ingredient quantities

and the strict speed of assembly. To soften this tax, the transition must explicitly redefine their
roles. By removing the repetitive stress of the assembly line, Sweetgreen can shift these
workers into higher-value roles focused on culinary prep quality and front-of-house hospitality.
Rollout phasing
A progressive, phased rollout is mandatory. Implementing a fundamentally new physical and
digital make-line in a "Big Bang" would make every hidden operational problem simultaneous
across the company. Sweetgreen must phase the rollout by deploying the redesigned make-line
in a handful of net-new store builds or retrofitting just a few high-volume urban locations first.
This bounds the blast radius and proves the lift in throughput and order accuracy against the
baseline before committing capital across the rest of the footprint.
The leverage case
Fund the phased rollout of a tech-enabled make-line to eliminate manual assembly errors at the
source—shifting labor from repetitive portioning to hospitality, cutting peak-hour wait times, and
structurally increasing throughput capacity without expanding the kitchen footprint.
