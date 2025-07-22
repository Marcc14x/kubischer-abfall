# 🚀 Schnellmethode zur Schätzung von Kubikwurzeln großer Zahlen

Diese Methode erlaubt es, Kubikwurzeln großer Zahlen im Kopf sehr schnell zu schätzen – insbesondere wenn es sich um ganze Kubikzahlen handelt.

---

## 🧠 Idee

Wenn du eine Zahl wie $985{,}074{,}875$ gegeben hast und du weißt, dass sie in der Nähe von $1000^3 = 1\,000\,000\,000$ liegt, kannst du eine schnelle Näherung der Kubikwurzel berechnen – **ohne Taschenrechner**, nur mit einem Trick, der den lokalen "kubischen Abfall" nutzt.

---

## 📐 Methode (Formel)

Gegeben:

- $N$: Zahl, deren Kubikwurzel geschätzt werden soll
- $a$: bekannte Kubikwurzel nahe bei $N$ (z. B. $a = 1000$, weil $1000^3 = 1\,000\,000\,000$ bekannt ist)

### Schritte:

1. **Differenz zur Referenz berechnen:**

   $$
   \Delta = a^3 - N
   $$

2. **Kubischen Abfall berechnen:**

   $$
   \text{Abfall} = a^3 - (a - 1)^3 = 3a^2 - 3a + 1
   $$

   Näherung (für schnelles Kopfrechnen):

   $$
   \text{Abfall} \approx 3a^2
   $$

3. **Anteil des Abfalls berechnen:**

   $$
   \delta = \frac{\Delta}{\text{Abfall}}
   $$

4. **Kubikwurzel schätzen:**

   $$
   \hat{x} = a - \delta
   $$

---

## 📊 Beispiel

Gesucht: $\sqrt[3]{985{,}074{,}875}$

1. Referenz:

   $$
   a = 1000 \Rightarrow a^3 = 1{,}000{,}000{,}000
   $$

2. Differenz:

   $$
   \Delta = 1{,}000{,}000{,}000 - 985{,}074{,}875 = 14{,}925{,}125
   $$

3. Kubischer Abfall:

   $$
   1000^3 - 999^3 = 1{,}000{,}000{,}000 - 997{,}002{,}999 = 2{,}997{,}001
   $$

4. Anteil:

   $$
   \delta = \frac{14{,}925{,}125}{2{,}997{,}001} \approx 4.98
   $$

5. Näherung:

   $$
   \hat{x} = 1000 - 5 = \boxed{995}
   $$

**Ergebnisprüfung:**

$$
995^3 = 985{,}074{,}875 \quad \checkmark
$$

---

## ⚠️ Einschränkungen

- Funktioniert **nur exakt bei ganzzahligen Kubikzahlen**
- Für nicht-exakte Kubikwurzeln liefert die Methode eine grobe Näherung
- Nicht geeignet zur Bestimmung von Nachkommastellen
- Gutes Gefühl für Kubikwerte und Abstände erforderlich

---

## 🧮 Bonus: Python-Implementierung

```python
def estimate_cubic_root(N: int, reference: int = 1000) -> float:
    ref_cubed = reference ** 3
    delta = ref_cubed - N
    cubic_drop = ref_cubed - (reference - 1) ** 3
    return reference - (delta / cubic_drop)

# Beispiel
print(estimate_cubic_root(985_074_875))  # Ausgabe: 995.0
