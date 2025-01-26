# Enhancing the Resiliency of Automated Web Tests with Natural Language

The paper **"Enhancing the Resiliency of Automated Web Tests with Natural Language"** introduces three core innovations to improve the robustness and accessibility of automated web UI testing:

## 1. **Pseudo-Language Definition Mapping into Selenium Actions**
- A restricted natural language (pseudo-language) simplifies test creation by allowing users to describe actions in plain sentences (e.g., *"Click the login button"*).
- Each sentence is mapped to corresponding Selenium actions, automating the generation of test scripts.
- This approach makes test creation accessible to non-technical users while maintaining structure and consistency.

## 2. **A New Concept for Resilient Locators**
- Traditional locators (like XPATH or CSS selectors) are replaced with **smart locators** based on dynamic similarity scoring.
- The system identifies elements by evaluating:
  - **Textual similarity**: Matches descriptions to element text.
  - **Semantic similarity**: Understands the meaning of text (e.g., "Submit" ≈ "Send").
  - **HTML attributes**: Considers attributes like `id`, `class`, and `style`.
- Smart locators adapt to minor UI changes, reducing script fragility and maintenance overhead.

## 3. **Semantic Understanding System for Translating Natural Language into Assertions**
- An NLP-based system interprets natural language descriptions to generate actionable test assertions.
- It extracts key information (e.g., actions, conditions, and values) and maps them to DOM elements.
- Example: *"Ensure the message 'Order Placed' is displayed"* is converted into a software assertion:
  ```python
  assert "Order Placed" in driver.find_element(By.cssSelector(...)).text
  ```
- This approach integrates validation logic into test scripts in a simple and intuitive manner.

---

### **Summary**
Together, these contributions create a resilient and accessible testing framework that simplifies test creation, enhances script durability, and lowers the technical barrier for web UI testing.

