---
title: Ocenianie &apos; &apos; przekroczenia limitu czasu funkcji funkcji i wymaganie przerwania w sposób niebezpieczny | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f6cae3ffb692161deb0b162a6432efe90f12bf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871653"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Błąd: szacowanie &#39;funkcji&#39; przekroczony limit czasu i wymaganie przerwania w sposób niebezpieczny

Pełny tekst komunikatu: przekroczono limit czasu obliczania funkcji "Function" i wymaganie zostało przerwane w sposób niebezpieczny. Może to spowodować uszkodzenie procesu docelowego.

Aby ułatwić sprawdzenie stanu obiektów .NET, debuger automatycznie wymusi w debugowanym procesie uruchomić dodatkowy kod (zazwyczaj metody pobierające właściwości i funkcje ToString). W większości przypadków te funkcje są szybko i ułatwiają debugowanie. Jednak debuger nie uruchamia aplikacji w piaskownicy. W związku z tym metoda pobierająca lub ToString właściwości, która wywołuje funkcję natywną, która przestaje odpowiadać, może prowadzić do długotrwałych limitów czasu, które mogą nie być możliwe do odzyskania. Ten komunikat o błędzie wystąpił.

Jednym z typowych przyczyn tego problemu jest to, że gdy debuger szacuje właściwość, umożliwia tylko poddane inspekcji do wykonania. Dlatego jeśli właściwość oczekuje na inne wątki do uruchomienia w debugowanej aplikacji i jeśli oczekuje na to, że środowisko uruchomieniowe platformy .NET nie może przerwać działania, ten problem wystąpi.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Istnieje kilka możliwych rozwiązań tego problemu.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>#1 rozwiązania: Uniemożliwianie debugerowi wywoływania właściwości pobierającej lub metody ToString

Komunikat o błędzie informuje o nazwie funkcji, którą debuger próbował wywołać. Jeśli można zmodyfikować tę funkcję, można uniemożliwić debugerowi wywoływanie metody pobierającej lub ToString właściwości. Wypróbuj jedną z następujących czynności:

* Zmień metodę na inny typ kodu oprócz metody pobierającej lub ToString właściwości, a problem zostanie wysunięty.
    -lub-
* (Dla ToString) Zdefiniuj atrybut DebuggerDisplay w typie, a debuger może oszacować coś innego niż ToString.
    -lub-
* (Dla metody pobierającej właściwości) Umieść `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atrybut we właściwości. Może to być przydatne, jeśli masz metodę, która musi pozostać właściwością ze względu na zgodność interfejsu API, ale w rzeczywistości powinna być to metoda.

### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>#2 rozwiązania: czy kod docelowy poprosił debugera o przerwanie oceny

Komunikat o błędzie informuje o nazwie funkcji, którą debuger próbował wywołać. Jeśli metoda getter lub ToString właściwości czasami nie działa prawidłowo, szczególnie w sytuacjach, gdy problem polega na tym, że kod wymaga innego wątku do uruchomienia kodu, funkcja implementacji może wywołać, `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` Aby polecić debugerowi przerwanie oceny funkcji. W tym rozwiązaniu nadal można jawnie oszacować te funkcje, ale domyślne zachowanie jest wykonywane, gdy nastąpi wywołanie NotifyOfCrossThreadDependency.

### <a name="solution-3-disable-all-implicit-evaluation"></a>#3 rozwiązania: Wyłącz wszystkie niejawne oceny

Jeśli poprzednie rozwiązania nie rozwiążą problemu, przejdź do   >  **opcji** narzędzia, a następnie usuń zaznaczenie pola **Debuguj**  >  **Ogólne**  >  **Włącz Obliczanie właściwości i inne niejawne wywołania funkcji**. Spowoduje to wyłączenie najbardziej niejawnych ocen funkcji i powinno rozwiązać problem.

### <a name="solution-4-enable-managed-compatibility-mode"></a>#4 rozwiązania: Włącz tryb zgodności zarządzanej

Jeśli przełączysz się do starszego aparatu debugowania, możesz wyeliminować ten błąd. Przejdź do   >  **opcji** narzędzia, a następnie wybierz ustawienie **debugowanie**  >  **Ogólne**  >  **Użyj zarządzanego trybu zgodności**. Aby uzyskać więcej informacji, zobacz [Ogólne opcje debugowania](../debugger/general-debugging-options-dialog-box.md).
