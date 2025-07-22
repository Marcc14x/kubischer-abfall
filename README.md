# 🚀 Schnellmethode zur Schätzung von Kubikwurzeln großer Zahlen

Diese Methode erlaubt es, Kubikwurzeln großer Zahlen im Kopf sehr schnell zu schätzen – insbesondere bei **ganzen Kubikzahlen**.

---

## 🧠 Idee

Wenn du eine Zahl wie $985{,}074{,}875$ hat, die nahe an $1000^3 = 1\,000\,000\,000$ liegt, kannst du ihre Kubikwurzel schnell schätzen – **ohne Taschenrechner**, nur mittels des lokalen „kubischen Abfalls“.

---

## 📐 Methode (Formel)

Gegeben:

- $N$: Zahl, deren Kubikwurzel geschätzt werden soll  
- $a$: bekannte Kubikwurzel nahe bei $N$ (z. B. $a = 1000$, weil $1000^3 = 1\,000\,000\,000$)

### Schritte:

1. **Differenz zur Referenz:**

$$
   \Delta = a^3 - N
$$

2. **Kubischer Abfall (exakt):**

$$
   \text{Abfall} = a^3 - (a - 1)^3 = 3a^2 - 3a + 1
$$

   Näherung (für schnelles Kopfrechnen):

$$
   \text{Abfall} \approx 3a^2
$$

3. **Anteil des Abfalls:**

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

   $a = 1000 \quad\Rightarrow\quad a^3 = 1{,}000{,}000{,}000$


2. Differenz:  
$$
   \Delta = 1{,}000{,}000{,}000 - 985{,}074{,}875 = 14{,}925{,}125
$$

3. Kubischer Abfall (exakt):  
$$
   1000^3 - 999^3 = 1{,}000{,}000{,}000 - 997{,}002{,}999 = 2{,}997{,}001
$$

4. Anteil berechnen:  
$$
   \delta = \frac{14{,}925{,}125}{2{,}997{,}001} \approx 4.98
$$

5. Näherung:  
$$
   \hat{x} = 1000 - 5 = \boxed{995}
$$

**Prüfung:**  
$$
995^3 = 985{,}074{,}875 \quad \checkmark
$$

---

## ⚠️ Einschränkungen

- Funktioniert **nur exakt bei ganzen Kubikzahlen**
- Bei nicht-ganzzahligen Ergebnissen liefert es nur eine grobe Schätzung  
- Für Nachkommastellen sind anspruchsvollere Methoden (z. B. Newton‑Raphson) nötig  
- Erfordert ein gutes Gefühl für Größen und Abstände

---

## 🧮 Bonus: Python-Implementierung

```python
def estimate_cubic_root(N: int, reference: int = 1000) -> float:
    ref_cubed = reference ** 3
    delta = ref_cubed - N
    cubic_drop = ref_cubed - (reference - 1) ** 3
    return reference - (delta / cubic_drop)

# Test:
print(estimate_cubic_root(985_074_875))  # Ausgabe: 995.0
