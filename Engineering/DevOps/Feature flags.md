---
tags: engineering/devops, feature-flags
author: Pham Duc Thanh
github_id: zlatanpham
date: 2022-09-25
---

Feature flags are a software engineering technique that allows you to enable or disable select functionality during runtime without having to deploy new code. The ability to control the visibility of features enables development teams to manage the full lifecycle of a feature — rather than being constrained by the traditional "code-deploy-test" cycle.

By using feature flags, you eliminate the need to maintain multiple branches for different features in your source code. All your code changes can be made to the primary branch and then enabled via a flag when the new feature is ready. This is an essential practice to ensure that [[Progressive Delivery]] is done correctly. Feature Flags encourage trunk-based development by having developers commit code to a single branch (trunk) rather than long-lived feature or development branches. A single branch of code helps to eliminate merge conflicts, broken builds, and results in a cleaner codebase. Instead of using a feature branch, use a flag to gate features not ready for public viewing.

Feature flags are a valuable tool for software teams, but they can also be leveraged by other teams within the organization. For example, help sales and customer team support employees to provision entitlements; enable product managers to manage beta programs; or allow marketing teams to run A/B tests.

## Core benefits of feature flags

- **Release management**: beta-test a new feature with a select group of users before releasing it to everyone.
- **Operation management**: monitor systems, toggling features on and off to minimize the impact of incidents.
- **Learn from experiment**: greatly support the use of A/B testing to test hypotheses and bring the best ideas to our customers.
- **Provision entitlements**: give a select group of users (normally, "premium" users) an early opportunity to try out a feature.

Feature flags add value to an organization as a whole, not just to the development team.

## Reference

- https://launchdarkly.com/blog/what-are-feature-flags/
- https://martinfowler.com/articles/feature-toggles.html



---
<!-- cta -->
### Contributing

At Dwarves, we encourage our people to read, write, share what we learn with others, and [[CONTRIBUTING|contributing to the Brainery]] is an important part of our learning culture. For visitors, you are welcome to read them, contribute to them, and suggest additions. We maintain a monthly pool of $1500 to reward contributors who support our journey of lifelong growth in knowledge and network.

### Love what we are doing?

- Check out our [products](https://superbits.co)
- Hire us to [build your software](https://d.foundation)
- Join us, [we are also hiring](https://github.com/dwarvesf/WeAreHiring)
- Visit our [Discord Learning Site](https://discord.gg/dzNBpNTVEZ)
- Visit our [GitHub](https://github.com/dwarvesf)