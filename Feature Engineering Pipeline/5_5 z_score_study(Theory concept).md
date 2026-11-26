# Z-Score (Standard Score)

> **Core Definition (মূল সংজ্ঞা):**  
> **Bengali Note:** *"Mean থেকে ($\sigma$) Standard Deviation কতটুকু দূরে তাই Z-score বলে দেয়।"*  
> **English Meaning:** A Z-score measures how many standard deviations ($\sigma$) a specific data point ($x$) lies above or below the mean ($\mu$) of its distribution.

---

## 1. What is a Z-Score? (Intuition & Subject Comparison)

When comparing raw scores from two different distributions that have different averages and spreads, raw numbers alone can be misleading. Standardizing scores into Z-scores puts them on a single common scale.

### Comparative Example: Bangla vs. Math Marks

Suppose a student scores **$80$ in Bangla** and **$70$ in Math**. Even though $80 > 70$ in raw marks, evaluating each score relative to its class mean ($\mu$) and standard deviation ($\sigma$) reveals which result is actually stronger:

| Subject | Student Score ($x$) | Class Mean ($\mu$) | Std. Dev ($\sigma$) | Distance from Mean | Z-Score ($z$) | Notebook Observation |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **Bangla** | $80$ | $75$ | $5$ | $+5$ marks ($+1\sigma$) | $z = +1.0$ | Avg student থেকে $1$ ঘর এগিয়ে ($1\text{ std}$ দূরে আছে) |
| **Math** | $70$ | $60$ | $5$ | $+10$ marks ($+2\sigma$) | $z = +2.0$ | Avg student থেকে $2\text{ std}$ এগিয়ে আছে — **Better result করছে** ($2\text{ std}$ দূরে আছে) |

* **Key Takeaway:** In **Bangla**, the student is **$1$ standard deviation ($+1\sigma$)** above the average student. In **Math**, the student is **$2$ standard deviations ($+2\sigma$)** above the average student. Therefore, the Math score ($70$) represents a significantly better relative performance.

### Visual Comparison on Number Lines

```text
Bangla Distribution (Mean = 75, SD = 5):
  65        70        75 (Mean)    80 (Score)    85        90
  |---------|---------|------------|-------------|---------|
                      |<-- +1 SD ->|  (z = +1.0)

Math Distribution (Mean = 60, SD = 5):
  50        55        60 (Mean)    65        70 (Score)    75
  |---------|---------|------------|---------|-------------|
                      |<-- +1 SD ->|<- +1 SD ->|  (z = +2.0 -> Better Relative Result!)
```

---

## 2. Variable Notation & Formula Derivation

### Fundamental Parameters

| Symbol | Term | Description & Role |
| :---: | :--- | :--- |
| $x$ | **Data Point** | The individual observed value or student score being evaluated (e.g., Bangla mark $= 80$). |
| $\mu$ | **Mean (Average)** | The central average value of the distribution (e.g., $\text{Avg} = 75$). |
| $\sigma$ | **Standard Deviation (SD)** | The unit step measuring how spread out values are around the mean (e.g., $\text{SD} = 5$). |
| $z$ | **Z-Score** | The signed number of standard deviations $x$ is away from $\mu$. |

### Step-by-Step Derivation

Any data point $x$ can be written as the mean $\mu$ plus $z$ steps of standard deviation $\sigma$:

1. **Position from Mean:**
   $$x = \mu + z\sigma$$

2. **Isolate the Deviation Term:**
   $$z\sigma = x - \mu$$

3. **Master Z-Score Formula:**
   $$z = \frac{x - \mu}{\sigma}$$

---

## 3. Worked Examples (Bangla Dataset: $\mu = 75$, $\sigma = 5$)

Applying $z = \frac{x - \mu}{\sigma}$ across different marks in Bangla:

| Case | Raw Mark ($x$) | Substitution | Simplification | Z-Score ($z$) | Interpretation |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Case 1** | $x = 75$ | $z = \frac{75 - 75}{5}$ | $\frac{0}{5}$ | **$z = 0$** | Exactly at the class average ($\text{Mean} = 0$) |
| **Case 2** | $x = 80$ | $z = \frac{80 - 75}{5}$ | $\frac{5}{5}$ | **$z = +1$** | $1\sigma$ above the mean (student's main mark) |
| **Case 3** | $x = 85$ | $z = \frac{85 - 75}{5}$ | $\frac{10}{5}$ | **$z = +2$** | $2\sigma$ above the mean ($+2\sigma$) |
| **Case 4** | $x = 90$ | $z = \frac{90 - 75}{5}$ | $\frac{15}{5}$ | **$z = +3$** | $3\sigma$ above the mean ($+3\sigma$ boundary) |

### Standardized Z-Score Axis ($\mu = 0$, $\sigma = 1$)

Converting raw values into Z-scores centers the distribution at **$0$** with a standard deviation step of **$1$**:

```text
Z-Score Scale:    -3        -2        -1         0 (Mean)   +1        +2        +3   | Outlier Zone
                   |---------|---------|---------|----------|---------|---------|---> (z > +3)
Raw Bangla (x):   60        65        70        75         80        85        90
                                                 |<-- s=1 ->|
```

---

## 4. Key Applications in Data Science & Machine Learning

### 1. Z-Score Normalization (Standardization)
* **Purpose:** Transforms features measured on different scales (e.g., Bangla vs. Math marks, or Age vs. Salary) onto a uniform scale so no single feature dominates distance-based or gradient-based machine learning algorithms.
* **Formula:**
  $$z = \frac{x - \mu}{\sigma}$$
* **Resulting Properties:** Transformed feature has **Mean ($\mu$) $= 0$** and **Standard Deviation ($\sigma$) $= 1$**.

### 2. Z-Score Outlier Detection
* **Purpose:** Identifies extreme or anomalous data points that lie unusually far from the center of a normal distribution.
* **Threshold Rule:** $|z| > 3$ (i.e., $z > +3$ or $z < -3$).
* **Notebook Rule:** *"Mean এর ডান পাশে $3$য় ঘরের বাইরে হলে তাকে outlier ধরা হয়"* — Any observation falling beyond the $3\text{rd}$ standard deviation step from the mean is flagged as an **outlier**.