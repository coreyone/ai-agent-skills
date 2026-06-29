# TEST DRIVEN DEVELOPMENT (TDD)
*The Architect’s Guide to Building Defensible Systems.*

If you want your code to be anti-fragile, you have to stop thinking of testing as an "after-the-fact" verification step. In this shop, we follow the philosophies of legends like **Kent Beck**, **Uncle Bob**, and **Martin Fowler**. Testing is the heartbeat of development.

---

### I. THE PHILOSOPHY: "Clean Code That Works"
As Kent Beck says, the goal is "clean code that works." TDD is not about testing; it is about **Design**. 
- **Pressure to Decouple**: If code is hard to test, it is poorly designed. TDD forces you to write small, loosely coupled functions because they are the only ones you can easily "Arrange" in a test.
- **Documentation by Example**: Tests are the only documentation that never lies. They tell us exactly how the system is intended to behave.
- **The Safety Net**: You cannot refactor (improve design) without tests. Without tests, you aren't "cleaning up," you're just "praying it doesn't break."

### II. THE THREE LAWS (Robert C. Martin)
We do not write production code until we have reached a stalemate with a test.
1. **You may not write any production code** until you have written a failing unit test.
2. **You may not write more of a unit test than is sufficient to fail** (and not compiling is failing).
3. **You may not write more production code than is sufficient to pass** the currently failing test.

### III. THE RHYTHM: RED-GREEN-REFACTOR
This is the "Nano-cycle" of development. Stick to the beat.
1. **🔴 RED**: Write a small test for a specific behavior. Run it. Watch it fail. (If it passes, your test is useless).
2. **🟢 GREEN**: Write the *slimiest*, simplest code possible to make the test pass. Hardcode values if you have to. No fancy architecture yet. Just get to green.
3. **🔵 REFACTOR**: Now that you have a green light, clean up the mess. Remove duplication, improve names, extract methods. You know you're safe because the test stays green.

### IV. TACTICS & VALUES
- **AAA (Arrange -> Act -> Assert)**: Every test should follow this structure. Set up the world, perform the action, verify the result. 
- **The Transformation Priority Premise**: As the tests get more specific, the code becomes more generic. Don't add an `if` statement for a specific case; add a rule that handles the general pattern.
- **Mocking vs. Reality**: Mock your external dependencies (APIs, Databases) to keep unit tests fast (<10ms). But remember: "Don't mock what you don't own." Test behavioral boundaries.
- **Tell, Don't Ask**: Tests should verify what a component *does*, not what it *is*. Avoid inspecting private internal state.

---

### V. THE ANTI-FRAGILE PORTFOLIO
Your test suite is your system's immune system. SURPRISES BECOME TESTS.

1. **Unit Tests (The Foundation)**: Test core logic and edge cases in isolation. Fast, deterministic, frequent.
2. **Contract Tests**: Ensure your API request/response shapes don't drift. Use these at the boundaries.
3. **Integration Tests**: Verify that your code actually talks to the Database or Proxy. Use sandboxes, not mocks here.
4. **E2E Smoke Tests**: The "Happy Path." If these fail, the business is losing money.
5. **“Failure Tests” (The Anti-Fragile Edge)**:
   - Simulate **Timeouts** (Does the system hang or report?).
   - Simulate **500 Errors** from dependencies (Does the circuit breaker trip?).
   - **Malformed Inputs** (Does the boundary reject the mess?).
   - **High Latency** (Is the UX resilient or blocked?).

### THE FINAL RULE
**Every production bug produces: a fix, a test, and a monitor.** 
If a bug reaches production, it means our test suite had a hole. We don't just fix the code; we build a cage around the bug so it can never happen again. This is how the system learns. This is how it becomes anti-fragile.