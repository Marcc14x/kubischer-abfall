# kubischer-abfall
Meine Kopfrechenmethode für Kubikwurzeln &amp; Potenzen 

# 🚀 Schnellmethode zur Schätzung von Kubikwurzeln großer Zahlen

Diese Methode erlaubt es, Kubikwurzeln großer Zahlen im Kopf sehr schnell zu schätzen – insbesondere wenn es sich um ganze Kubikzahlen handelt.

---

## 🧠 Idee

Wenn du eine Zahl wie `985074875` gegeben hast und du weißt, dass sie in der Nähe von `1000^3 = 1_000_000_000` liegt, kannst du eine schnelle Näherung der Kubikwurzel berechnen – **ohne Taschenrechner**, nur mit einem Trick, der den lokalen "kubischen Abfall" nutzt.

---

## 📐 Formel

Gegeben:
- \( N \): Zahl, deren Kubikwurzel gesucht ist
- \( a \): bekannter Referenzwert (z. B. \( 1000 \), weil \( 1000^3 \) bekannt ist)

1. **Differenz zur Referenz:**

\[
\Delta = a^3 - N
\]

2. **Kubischer Abfall (Differenz zu vorigem Kubikwert):**

\[
\text{Abfall} = a^3 - (a - 1)^3 = 3a^2 - 3a + 1
\]

(Näherungsweise genügt oft \( \text{Abfall} \approx 3a^2 \))

3. **Schrittgröße berechnen:**

\[
\delta = \frac{\Delta}{\text{Abfall}}
\]

4. **Kubikwurzel schätzen:**

\[
\hat{x} = a - \delta
\]

---

## 📊 Beispiel

Gesucht:  
\[
\sqrt[3]{985074875}
\]

1. Referenz:  
\[
a = 1000 \Rightarrow a^3 = 1_000_000_000
\]

2. Differenz:  
\[
\Delta = 1_000_000_000 - 985_074_875 = 14_925_125
\]

3. Kubischer Abfall:  
\[
1000^3 - 999^3 = 2_997_001 \Rightarrow \text{Abfall} \approx 3_000_000
\]

4. Schätzung:  
\[
\delta = \frac{14_925_125}{3_000_000} \approx 4.975
\Rightarrow \hat{x} = 1000 - 5 = \boxed{995}
\]

Prüfung:  
\[
995^3 = 985_074_875 ✅
\]

---

## ⚠️ Einschränkungen

- Funktioniert **nur exakt bei ganzzahligen Kubikzahlen**
- Keine exakte Bestimmung von Nachkommastellen
- Für Zwischenwerte nur grobe Näherung

---

## 📦 Anwendung

Diese Methode eignet sich für:

- Kopfrechnen-Wettbewerbe
- Mathematische Shows (z. B. Supertalent)
- Schnellschätzungen in Technik & Naturwissenschaften

---

## 🧮 Bonus: Python-Implementierung

```python
def estimate_cubic_root(N: int, reference: int = 1000) -> float:
    ref_cubed = reference ** 3
    delta = ref_cubed - N
    cubic_drop = ref_cubed - (reference - 1) ** 3
    return reference - (delta / cubic_drop)

# Beispiel
print(estimate_cubic_root(985_074_875))  # Ausgabe: ~995.0
