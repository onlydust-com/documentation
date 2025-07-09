# Best Practices - must read

If you're contributing to open source through OnlyDust, here's how to do it right -for maintainers, for the community, and for your own learning.

#### 1. Pick a project that you care about

Choose a project that interests you technically or helps you grow. You'll stick with it longer, do better work, and get better feedback.

#### 2. Start with the Docs and Issues

Before touching any code:

* Read the **README**, **contribution guidelines**, and setup instructions
* This may sound like a no brainer, but READ THE ISSUE before saying that you can work on it. Pick issues that fit your skills or else you're wasting everyone's time.
* Ask questions if something’s unclear. Maintainers appreciate it when you check before diving in

#### 3. Communicate, communicate, communicate

Super important. It's collaborative work. Always keep maintainers and the community up to date with where things are at:&#x20;

* Comment on the issue you’re picking up
* Open a draft PR early if possible - helps maintainers follow your thinking
* If you get blocked or need more time, say so
* If you stop working on something, let others know

#### 4. Use AI Responsibly

AI can definitely boost your productivity - but you’re still responsible for what you submit. Don't abuse it.&#x20;

**Good uses of AI (to help out):**

* Exploring unfamiliar frameworks or tools
* Generating boilerplate, test scaffolding, or starter code
* Summarizing large files or docstrings
* Reviewing PRs for structure and clarity

**Not acceptable:**

* Copy-pasting AI output without reviewing or testing
* Submitting work you don’t fully understand
* Generating meaningless or bloated PRs for visibility

Maintainers and other devs will notice when work is AI-generated and low-quality. It's tiresome and just overall reflects badly upon you.

#### 5. Quality > Quantity

* One well-crafted PR beats five rushed ones
* Stick to the repo’s conventions
* Add tests when it makes sense
* Write good commit messages
* Keep your changes scoped and purposeful

Remember that you’re contributing to something others rely on!

#### 6. Link your PR to an issue (why it's important)

When you’re working on an issue, always link your pull request to it. This helps maintainers track progress, understand context, and close things cleanly once your work is merged.

In your PR description, include:

```
nginxCopyEditFixes #123
```

or

```
nginxCopyEditCloses #123
```

Where `123` is the issue number.

You can also use:

* `Resolves #...`
* `Related to #...` (if it’s not directly solving the issue)

Once your PR is merged, GitHub will automatically close the linked issue

**Bonus tip:** Add a short description of what the PR does and _why_ it matters. Maintainers appreciate the context.

[More info here on GitHub](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue).

#### 7. Be a Good Teammate

* Respect that many maintainers are volunteers
* Stay open to feedback
* Help onboard others when you can
* Be clear, direct, and kind in all communication

#### 8. Track Your Work During OSS Waves

If you’re contributing during an OSS Wave, you have 10 days to push your work. Even if it’s not done, submit a draft PR by Day 10 so the maintainer can see what you’ve been working on. They'll have two extra days to review.

