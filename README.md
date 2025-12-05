# Bayes' Theorem & Its Applications

## 1. Introduction
Bayes’ Theorem helps us update our beliefs when new information becomes available. It is foundational in statistics, decision-making, AI, and machine learning.

---

## 2. Basic Terms
### **2.1 Experiment**
An action that leads to an outcome.

### **2.2 Sample Space (S)**
All possible outcomes.

### **2.3 Event**
A desired outcome from the sample space.

### **2.4 Conditional Probability**
Probability of event A given event B has already occurred:
```
P(A|B) = P(A ∩ B) / P(B)
```

---

## 3. Bayes’ Theorem
Bayes’ theorem reverses conditional probability:
```
P(A|B) = [P(B|A) * P(A)] / P(B)
```

Where:
- **P(A|B)** = Probability of A after observing B
- **P(B|A)** = Probability of B if A happened
- **P(A)** = Prior probability of A
- **P(B)** = Prior probability of B

---

## 4. Importance
Bayes’ theorem helps answer questions like:
**"Given a test result or observation, what is the probability of the actual cause?"**

Used in:
- Medical diagnosis
- Machine learning
- Weather forecasting
- Fraud detection
- Quality control

---

## 5. General Bayes’ Theorem (Multiple Events)
```
P(Aₖ | B) = [P(B|Aₖ) * P(Aₖ)] / Σ P(B|Aᵢ) * P(Aᵢ)
```

---

## 6. Step-by-Step Method
1. Identify prior probabilities.
2. Identify conditional probabilities.
3. Use total probability:
```
P(B) = P(B|A)P(A) + P(B|Aᶜ)P(Aᶜ)
```
4. Apply Bayes’ theorem:
```
P(A|B) = [P(B|A)P(A)] / P(B)
```

---

## 7. Applications of Bayes’ Theorem
### **7.1 Medical Diagnosis**
Used for cancer tests, COVID tests, pregnancy tests.

### **7.2 Spam Filtering (Naive Bayes)**
Classifies spam based on word probability.

### **7.3 Weather Forecasting**
Predicts rain using humidity, cloud data.

### **7.4 Fraud Detection**
Banks detect unusual spending patterns.

### **7.5 Quality Control**
Find which machine caused defective products.

---

## 8. Numerical Examples
### **Example 1: Medical Test**
A disease affects 2% of people.
- True positive = 95%
- False positive = 10%

Find: `P(Disease | Positive)`

Given:
```
P(D) = 0.02
P(Dᶜ) = 0.98
P(+|D) = 0.95
P(+|Dᶜ) = 0.10
```

Total probability:
```
P(+) = 0.95*0.02 + 0.10*0.98 = 0.117
```

Apply Bayes:
```
P(D|+) = (0.95*0.02) / 0.117 ≈ 0.162
```
**Final Answer: 16.2%**

---

### **Example 2: Factory Machines**
Machine A produces 40% items, 3% defective.
Machine B produces 60% items, 1% defective.

Find: `P(Item from A | Defective)`

Total probability:
```
P(D) = 0.03*0.40 + 0.01*0.60 = 0.018
```

Bayes:
```
P(A|D) = (0.03*0.40) / 0.018 = 0.6667
```
**Final Answer: 66.67%**

---

## 9. Bayes’ Theorem in Machine Learning (Naive Bayes)
Assumes feature independence and computes class probability.
Used in:
- Sentiment analysis
- Spam detection
- Text classification
- Face recognition

---

## 10. Common Student Mistakes
- Forgetting total probability
- Confusing P(A|B) with P(B|A)
- Using percentages instead of decimals
- Assuming independence without information

---

## 11. Summary Table
| Term | Meaning |
|------|----------------------|
| Prior | Initial belief |
| Likelihood | Probability of data given condition |
| Posterior | Updated belief |
| Evidence | Total probability |

Formula:
```
Posterior = (Likelihood × Prior) / Evidence
```

---