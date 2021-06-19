---
title: Uchybnił czas oceny funkcji i konieczne było przerwanie jej &apos; &apos; w niebezpieczny sposób | Microsoft Docs
description: 'Pełny tekst komunikatu: Udano przekreślenie czasu oceny funkcji "function" i konieczne było przerwanie jej w niebezpieczny sposób.'
ms.date: 06/18/2021
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e928bb0ebae1e644729fcaf4f47b7dd461399be6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386673"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Błąd: Szacowanie wartości &#39;funkcji&#39; ułożyło się i konieczne było przerwanie jej w niebezpieczny sposób

Pełny tekst komunikatu: Udano przekreślenie czasu oceny funkcji "function" i konieczne było przerwanie jej w niebezpieczny sposób. Może to spowodować uszkodzenie procesu docelowego.

Aby ułatwić sprawdzanie stanu obiektów .NET, debuger automatycznie wymusi uruchomienie dodatkowego kodu przez debugowany proces (zazwyczaj metody pobierające właściwości i funkcje ToString). W większości przypadków funkcje te są szybko ukończone i znacznie ułatwiają debugowanie. Jednak debuger nie uruchamia aplikacji w piaskownicy. W rezultacie metoda getter właściwości lub ToString, która wywołuje funkcję natywną, która przestaje odpowiadać, może prowadzić do długich limitów czasu, których odzyskanie może być nie do odzyskania. Jeśli wystąpi ten komunikat o błędzie, wystąpił.

Częstą przyczyną tego problemu jest to, że gdy debuger ocenia właściwość, umożliwia wykonanie tylko sprawdzanych wątków. Jeśli więc właściwość oczekuje na uruchomienie innych wątków wewnątrz debugowanych aplikacji, a jeśli oczekuje w taki sposób, że środowisko uruchomieniowe .NET nie jest w stanie przerwać działania, ten problem się stanie.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

W poniższych sekcjach znajduje się kilka możliwych rozwiązań tego problemu.

## <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Rozwiązanie #1: Uniemożliwianie debugerowi wywoływania właściwości getter lub metody ToString

Komunikat o błędzie będzie zawierał nazwę funkcji, która została wywołana przez debuger. Jeśli możesz zmodyfikować tę funkcję, możesz uniemożliwić debugerowi wywoływanie metody getter właściwości lub ToString. Wypróbuj jedną z następujących czynności:

* Zmień metodę na inny typ kodu oprócz metody getter właściwości lub Metody ToString, a problem nie będzie już problemem.
  -lub-
* (Dla ToString) [Zdefiniuj atrybut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) dla typu i debuger może ocenić coś innego niż ToString.
  -lub-
* (W przypadku getter właściwości) Umieść atrybut [System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)](/dotnet/api/system.diagnostics.debuggerbrowsableattribute) we właściwości . Może to być przydatne, jeśli masz metodę, która musi pozostać właściwością ze względu na zgodność interfejsu API, ale tak naprawdę powinna być metodą.

## <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Rozwiązanie #2: Poproś debuger o przerwanie oceny w kodzie docelowym

Komunikat o błędzie będzie zawierał nazwę funkcji, która została wywołana przez debuger. Jeśli metoda getter lub ToString właściwości czasami nie działa prawidłowo, szczególnie w sytuacjach, w których problem polega na tym, że kod wymaga innego wątku do uruchomienia kodu, funkcja implementacji może wywołać [metodę System.Diagnostics.Debugger.NotifyOfCrossThreadDependency,](/dotnet/api/system.diagnostics.debugger.notifyofcrossthreaddependency) aby poprosić debuger o przerwanie oceny funkcji. Dzięki temu rozwiązaniu nadal można jawnie ocenić te funkcje, ale zachowanie domyślne jest takie, że wykonywanie zatrzymuje się po wywołaniu NotifyOfCrossThreadDependency.

## <a name="solution-3-disable-all-implicit-evaluation"></a>Rozwiązanie #3: Wyłącz wszystkie niejawne oceny

Jeśli poprzednie rozwiązania nie rozwiążą problemu, przejdź do pozycji Narzędzia Opcje i usuń zaznaczenie ustawienia Debugowanie Ogólne Włączanie oceny właściwości i innych  >     >    >  **niejawnych wywołań funkcji**. Spowoduje to wyłączenie większości niejawnych ocen funkcji i powinno rozwiązać problem.

## <a name="solution-4-check-compatibility-with-third-party-developer-tools"></a>Rozwiązanie #4: Sprawdzanie zgodności z narzędziami deweloperskimi innych firm

Jeśli używasz narzędzia Resharper, zobacz ten [problem,](https://youtrack.jetbrains.com/issue/RSRP-476824) aby uzyskać sugestie.

## <a name="solution-5-enable-managed-compatibility-mode"></a>Rozwiązanie #5: Włączanie trybu zgodności zarządzanej

Jeśli przełączysz się na starszy aparat debugowania, możesz wyeliminować ten błąd. Przejdź do **opcji** Narzędzia i wybierz ustawienie Debugowanie  >     >  **Ogólne**  >  **Użyj trybu zgodności zarządzanej.** Aby uzyskać więcej informacji, zobacz [Ogólne opcje debugowania](../debugger/general-debugging-options-dialog-box.md).
