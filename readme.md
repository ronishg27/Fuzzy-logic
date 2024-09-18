

# Fuzzy Logic-Based Medication Necessity System

## Overview

This Python script uses the `scikit-fuzzy` library to implement a fuzzy logic system for determining the necessity of medication based on several health-related inputs. These inputs include symptom severity, test results, age, weight, and blood pressure. The output is a percentage value that represents the necessity of taking medication.

## Dependencies

Ensure the following Python packages are installed:

```bash
pip install numpy scikit-fuzzy
```

### Importing Necessary Modules

- **NumPy**: Used for handling arrays.
- **Scikit-fuzzy (skfuzzy)**: Provides tools for fuzzy logic in Python.

```python
import numpy as np
import skfuzzy as fuzz
from skfuzzy import control as ctrl
```

## Defining Variables

### Universe of Discourse

The script defines the universe of discourse (i.e., the range of possible values) for each variable:

- **Symptom Severity**: Ranges from 0 (no severity) to 10 (maximum severity).
- **Test Results**: Ranges from 0 (worst) to 100 (best).
- **Age**: Ranges from 0 to 100 years.
- **Weight**: Ranges from 0 to 200 kg.
- **Blood Pressure**: Ranges from 0 to 200 mmHg.
- **Medication Necessity**: The output variable ranges from 0% (no necessity) to 100% (maximum necessity).

### Membership Functions

Membership functions are defined using triangular shapes (`trimf`) for each variable. The membership functions for each input and output variable are as follows:

#### Symptom Severity:
- Low
- Medium
- High

#### Test Results:
- Low
- Medium
- High

#### Age:
- Young
- Middle
- Old

#### Weight:
- Low
- Medium
- High

#### Blood Pressure:
- Low
- Normal
- High

#### Medication Necessity (Output):
- Low
- Medium
- High

```python
# Example for Symptom Severity
severity_lo = fuzz.trimf(symptom_severity, [0, 0, 5])
severity_md = fuzz.trimf(symptom_severity, [0, 5, 10])
severity_hi = fuzz.trimf(symptom_severity, [5, 10, 10])
```

## Fuzzy Variables and Membership Assignment

The fuzzy variables are created using the `ctrl.Antecedent` and `ctrl.Consequent` classes from `scikit-fuzzy`. The membership functions defined earlier are assigned to these variables.

```python
symptom_severity_var = ctrl.Antecedent(symptom_severity, 'symptom_severity')
test_results_var = ctrl.Antecedent(test_results, 'test_results')
age_var = ctrl.Antecedent(age, 'age')
weight_var = ctrl.Antecedent(weight, 'weight')
blood_pressure_var = ctrl.Antecedent(blood_pressure, 'blood_pressure')
medication_necessity_var = ctrl.Consequent(medication_necessity, 'medication_necessity')

# Example of assigning membership functions to variables
symptom_severity_var['low'] = severity_lo
symptom_severity_var['medium'] = severity_md
symptom_severity_var['high'] = severity_hi
```

## Fuzzy Rules

A set of fuzzy rules is defined to simulate the decision-making process regarding medication necessity. These rules take into account symptom severity, test results, age, weight, and blood pressure.

Example rules:

- If symptom severity is low and test results are low, medication necessity is low.
- If age is old, weight is high, and blood pressure is high, medication necessity is high.

```python
rule1 = ctrl.Rule(symptom_severity_var['low'] & test_results_var['low'], medication_necessity_var['low'])
rule2 = ctrl.Rule(symptom_severity_var['low'] & test_results_var['medium'], medication_necessity_var['medium'])
# More rules follow...
```

## Fuzzy Control System

The control system is created using the rules defined above. It is then simulated to compute the output based on given inputs.

```python
medication_ctrl = ctrl.ControlSystem([rule1, rule2, ..., rule12])
medication_sim = ctrl.ControlSystemSimulation(medication_ctrl)
```

## Example Simulation

An example simulation is run with the following inputs:
- **Symptom Severity**: 6
- **Test Results**: 65
- **Age**: 45
- **Weight**: 70 kg
- **Blood Pressure**: 130 mmHg

The system computes the medication necessity based on these inputs.

```python
medication_sim.input['symptom_severity'] = 6
medication_sim.input['test_results'] = 65
medication_sim.input['age'] = 45
medication_sim.input['weight'] = 70
medication_sim.input['blood_pressure'] = 130
medication_sim.compute()
print(f"Medication Necessity: {medication_sim.output['medication_necessity']}%")
```

### Example Output

The computed result will be printed, such as:

```bash
Medication Necessity: 60.1%
```

## Plotting the Membership Functions

The script also includes the option to visualize the membership functions using the `.view()` method. This allows you to inspect how the membership functions for each variable are shaped.

```python
symptom_severity_var.view()
test_results_var.view()
age_var.view()
weight_var.view()
blood_pressure_var.view()
medication_necessity_var.view(sim=medication_sim)
```

## Conclusion

This script demonstrates the use of fuzzy logic in medical decision-making. By incorporating various factors such as symptom severity, test results, age, weight, and blood pressure, the system provides a fuzzy-based recommendation on medication necessity.
