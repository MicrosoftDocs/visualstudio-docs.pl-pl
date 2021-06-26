---
title: Przekreślenie czasu oceny funkcji wymagało przerywania w &apos; niebezpieczny sposób | &apos; Microsoft Docs
description: 'Pełny tekst komunikatu: Udano czas oceny funkcji "function" i konieczne było przerwanie jej działania w niebezpieczny sposób.'
ms.date: 06/18/2021
ms.topic: error-reference
ms.custom: contperf-fy21q4
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94c308e9ec960f744a98f0f930999df36afff475
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925010"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Błąd: Szacowanie funkcji &#39;,&#39; ułożyło się i trzeba było je przerwane w niebezpieczny sposób

Pełny tekst komunikatu: Udano czas oceny funkcji "function" i konieczne było przerwanie jej działania w niebezpieczny sposób. Może to spowodować uszkodzenie procesu docelowego.

Aby ułatwić sprawdzanie stanu obiektów .NET, debuger automatycznie wymusi uruchomienie dodatkowego kodu przez debugowany proces (zazwyczaj metody pobierające właściwości i funkcje ToString). W większości wszystkich scenariuszy funkcje te są szybko ukończone i znacznie ułatwiają debugowanie. Jednak debuger nie uruchamia aplikacji w piaskownicy. W związku z tym metoda getter właściwości lub Metoda ToString, która wywołuje funkcję natywną, która przestaje odpowiadać, może prowadzić do długich limitów czasu, których odzyskanie może być nie do odzyskania. Jeśli wystąpi ten komunikat o błędzie, wystąpił.

Częstą przyczyną tego problemu jest to, że gdy debuger ocenia właściwość, umożliwia wykonanie tylko sprawdzanych wątków. Jeśli więc właściwość oczekuje na uruchomienie innych wątków wewnątrz debugowanych aplikacji, a jeśli oczekuje w sposób, który nie może przerwać działania środowiska uruchomieniowego .NET, ten problem się stanie.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Zobacz poniższe sekcje, aby uzyskać kilka możliwych rozwiązań tego problemu.

## <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Rozwiązanie #1: Uniemożliwianie debugerowi wywoływania właściwości getter lub metody ToString

Komunikat o błędzie będzie zawierał nazwę funkcji, która została wywołana przez debuger. Jeśli możesz zmodyfikować tę funkcję, możesz uniemożliwić debugerowi wywoływanie metody getter właściwości lub ToString. Wypróbuj jedną z następujących czynności:

* Zmień metodę na inny typ kodu oprócz metody getter właściwości lub Metody ToString, a problem zostanie umyty.
  -lub-
* (Dla ToString) [Zdefiniuj atrybut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) dla typu i debuger może ocenić coś innego niż ToString.
  -lub-
* (W przypadku getter właściwości) Umieść atrybut [System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)](/dotnet/api/system.diagnostics.debuggerbrowsableattribute) we właściwości . Może to być przydatne, jeśli masz metodę, która musi pozostać właściwością ze względu na zgodność interfejsu API, ale tak naprawdę powinna to być metoda.

## <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Rozwiązanie #2: Poproś debuger o przerwanie oceny w kodzie docelowym

Komunikat o błędzie będzie zawierał nazwę funkcji, która została wywołana przez debuger. Jeśli metoda getter lub ToString właściwości czasami nie działa prawidłowo, szczególnie w sytuacjach, gdy problem polega na tym, że kod wymaga innego wątku do uruchomienia kodu, funkcja implementacji może wywołać [metodę System.Diagnostics.Debugger.NotifyOfCrossThreadDependency,](/dotnet/api/system.diagnostics.debugger.notifyofcrossthreaddependency) aby poprosić debuger o przerwanie oceny funkcji. Dzięki temu rozwiązaniu nadal można jawnie ocenić te funkcje, ale domyślnym zachowaniem jest zatrzymanie wykonywania po wywołaniu NotifyOfCrossThreadDependency.

## <a name="solution-3-disable-all-implicit-evaluation"></a>Rozwiązanie #3: wyłącz wszystkie niejawne oceny

Jeśli poprzednie rozwiązania nie rozwiążą problemu, przejdź do pozycji Opcje narzędzi i usuń zaznaczenie ustawienia Debugowanie Ogólne Włączanie oceny właściwości i innych  >     >    >  **niejawnych wywołań funkcji**. Spowoduje to wyłączenie większości niejawnych ocen funkcji i powinno rozwiązać problem.

## <a name="solution-4-check-compatibility-with-third-party-developer-tools"></a>Rozwiązanie #4: sprawdzanie zgodności z narzędziami deweloperskimi innych firm

Jeśli używasz programu Resharper, zobacz ten [problem,](https://youtrack.jetbrains.com/issue/RSRP-476824) aby uzyskać sugestie.

## <a name="solution-5-enable-managed-compatibility-mode"></a>Rozwiązanie #5: Włączanie trybu zgodności zarządzanej

Jeśli przełączysz się na starszy aparat debugowania, możesz wyeliminować ten błąd. Przejdź do **opcji**  >  **Narzędzia** i wybierz ustawienie **Debugowanie**  >  **Ogólne**  >  **Użyj trybu zgodności zarządzanej.** Aby uzyskać więcej informacji, zobacz [Ogólne opcje debugowania.](../debugger/general-debugging-options-dialog-box.md)
