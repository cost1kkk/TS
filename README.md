# TS
# Theoretical Study

## Test-Driven Development (TDD)
Test-Driven Development (TDD) is a software development methodology that emphasizes writing tests before implementing the actual code. The core principles of TDD include:

1. **Write a Failing Test:** Before writing any functional code, a test case is created based on the requirements.
2. **Make the Test Pass:** Minimal code is written to make the test pass.
3. **Refactor the Code:** The code is improved while ensuring that tests remain successful.

### Advantages of TDD:
- Ensures code correctness from the beginning.
- Improves code design and modularity.
- Facilitates debugging and regression testing.

### Disadvantages of TDD:
- Can be time-consuming initially.
- Requires developers to have good testing skills.

## Behavior-Driven Development (BDD)
Behavior-Driven Development (BDD) extends TDD by emphasizing human-readable descriptions of software behavior. It involves writing tests in a natural language format using a Given-When-Then structure.

1. **Define a Scenario:** Write user-focused test scenarios.
2. **Implement Code Based on the Scenario:** Develop code that meets the described behavior.
3. **Verify with Automated Tests:** Ensure the implementation matches expected outcomes.

### Advantages of BDD:
- Encourages collaboration between developers, testers, and non-technical stakeholders.
- Ensures clarity in requirements.
- Enhances documentation as test cases are human-readable.

### Disadvantages of BDD:
- Requires learning additional tools/frameworks.
- Writing effective scenarios may require more effort.

## Comparison: When to Use TDD vs. BDD
| Criteria | TDD | BDD |
|----------|-----|-----|
| Focus | Code correctness | Application behavior |
| Audience | Developers | Developers, Testers, Product Owners |
| Test Style | Unit Tests | Acceptance Tests |
| Readability | Technical | Human-readable (Given-When-Then) |
| Best for | Core functionalities, algorithms | User stories, business logic validation |

# Practical Implementation

## TDD Implementation (Python)
1. **Write a failing test:**
   ```python
   import unittest
   from calculator import add
   
   class TestCalculator(unittest.TestCase):
       def test_add(self):
           self.assertEqual(add(2, 3), 5)
   
   if __name__ == '__main__':
       unittest.main()
   ```
2. **Implement minimal functionality:**
   ```python
   def add(a, b):
       return a + b
   ```
3. **Refactor:**
   Since the function is simple, refactoring is not necessary here.

## BDD Implementation (Python - Behave)
1. **Define Feature (calculator.feature):**
   ```gherkin
   Feature: Calculator Addition
       Scenario: Add two numbers
           Given I have a calculator
           When I add 2 and 3
           Then the result should be 5
   ```
2. **Implement Steps (steps/calculator_steps.py):**
   ```python
   from behave import given, when, then
   from calculator import add
   
   @given("I have a calculator")
   def step_given_calculator(context):
       pass
   
   @when("I add {a:d} and {b:d}")
   def step_when_add(context, a, b):
       context.result = add(a, b)
   
   @then("the result should be {expected:d}")
   def step_then_result(context, expected):
       assert context.result == expected
   ```
3. **Run Tests:**
   ```bash
   behave
   ```

# Final Report

## Implementation Process & Challenges
- **TDD:** The biggest challenge was writing tests before implementation, which required carefully defining expected behavior first.
- **BDD:** Writing readable scenarios was straightforward, but setting up the testing framework required additional effort.

## Source Code & Test Results
- **TDD:** All unit tests passed successfully.
- **BDD:** All feature tests executed correctly, confirming expected behavior.

## Conclusion
TDD is best suited for ensuring low-level code correctness, while BDD excels in defining application behavior. Both methodologies improve software quality but cater to different aspects of development.
