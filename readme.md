# Decision Support System for Medication Necessity


## Fuzzy Logic
Fuzzy logic deals with imprecise or uncertain information, allowing for degrees of truth between 0 and 1, rather than just true or false. It provides flexibility in reasoning where traditional binary logic is too restrictive.

In fuzzy logic, a membership function defines how much an input belongs to a set, with values between 0 (non-membership) and 1 (full membership). Fuzzy rules, expressed as if-then statements, relate input variables to output variables.

Fuzzy logic is widely used in applications such as control systems, image processing, natural language processing, medical diagnosis, and artificial intelligence. It accounts for partial truths, where statements can be partially true and false, providing a more nuanced approach to decision-making compared to the Boolean system's absolute true or false values.

![Fuzzy Logic image](https://media.geeksforgeeks.org/wp-content/uploads/fuzzy-logic_1.png)

### **ARCHITECTURE**

Its Architecture contains four parts :

- RULE BASE: It contains the set of rules and the IF-THEN conditions provided by the experts to govern the decision-making system, on the basis of linguistic information. Recent developments in fuzzy theory offer several effective methods for the design and tuning of fuzzy controllers. Most of these developments reduce the number of fuzzy rules.
- FUZZIFICATION: It is used to convert inputs i.e. crisp numbers into fuzzy sets. Crisp inputs are basically the exact inputs measured by sensors and passed into the control system for processing, such as temperature, pressure, rpm’s, etc.
- INFERENCE ENGINE: It determines the matching degree of the current fuzzy input with respect to each rule and decides which rules are to be fired according to the input field. Next, the fired rules are combined to form the control actions.
- DEFUZZIFICATION: It is used to convert the fuzzy sets obtained by the inference engine into a crisp value. There are several defuzzification methods available and the best-suited one is used with a specific expert system to reduce the error.




![Fuzzy architecture](https://media.geeksforgeeks.org/wp-content/uploads/fuzzylogic_architecture.png)