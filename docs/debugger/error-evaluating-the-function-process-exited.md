---
title: Błąd — proces docelowy zakończył pracę z &apos; kodem kodu &apos; podczas obliczania funkcji funkcji &apos; &apos; | Microsoft Docs
ms.date: 4/06/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94effc8a5f75e7b38fb7275d175eb324c479a7a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88711641"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Błąd: proces docelowy zakończył działanie z kodem &#39;kod&#39; podczas oceniania funkcji &#39;funkcji&#39;

Pełny tekst komunikatu: proces docelowy zakończył działanie z kodem "Code" podczas obliczania funkcji "Function".

Aby ułatwić sprawdzenie stanu obiektów .NET, debuger automatycznie wymusi w debugowanym procesie uruchomić dodatkowy kod (zazwyczaj metody pobierające właściwości i `ToString` funkcje). W większości scenariuszy te funkcje zostały pomyślnie wykonane lub wyrzucają wyjątki, które mogą zostać przechwycone przez debuger. Istnieją jednak pewne sytuacje, w których wyjątki nie mogą być przechwytywane, ponieważ przekraczają granice jądra, wymagają pompowania komunikatów użytkownika lub nie można ich odzyskać. W związku z tym metoda pobierająca lub ToString właściwości, która wykonuje kod, który jawnie kończy proces (na przykład wywołania `ExitProcess()` ) lub zgłasza nieobsłużony wyjątek, którego nie można przechwycić (na przykład), `StackOverflowException` spowoduje zakończenie debugowanego procesu i zakończenie sesji debugowania. Ten komunikat o błędzie wystąpił.

Jednym z typowych przyczyn tego problemu jest to, że gdy debuger oblicza właściwość, która wywołuje sam siebie, może to spowodować wyjątek przepełnienia stosu. Nie można odzyskać wyjątku przepełnienia stosu, a proces docelowy zostanie przerwany.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Istnieją dwa możliwe rozwiązania tego problemu.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>#1 rozwiązania: Uniemożliwianie debugerowi wywoływania właściwości pobierającej lub metody ToString 

Komunikat o błędzie informuje o nazwie funkcji, którą debuger próbował wywołać. Przy użyciu nazwy funkcji można spróbować ponownie ocenić tę funkcję z okna **bezpośredniego** , aby debugować ocenę. Debugowanie jest możliwe podczas oceniania z okna **bezpośredniego** , ponieważ, w przeciwieństwie do niejawnych ocen z okna **Autokorekty/lokalne/czujki** , debuger przerwie w nieobsłużonych wyjątkach.

Jeśli można zmodyfikować tę funkcję, można uniemożliwić debugerowi wywoływanie metody pobierającej lub `ToString` metodzie właściwości. Wypróbuj jedną z następujących czynności:

* Zmień metodę na inny typ kodu oprócz metody pobierającej lub ToString właściwości, a problem zostanie wysunięty.
    -lub-
* (Do `ToString` ) Zdefiniuj `DebuggerDisplay` atrybut w typie, a debuger może oszacować coś innego niż `ToString` .
    -lub-
* (Dla metody pobierającej właściwości) Umieść `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atrybut we właściwości. Może to być przydatne, jeśli masz metodę, która musi pozostać właściwością ze względu na zgodność interfejsu API, ale w rzeczywistości powinna być to metoda.

Jeśli nie można zmodyfikować tej metody, można przerwać proces docelowy z alternatywną instrukcją i ponowić próbę dokonania oceny.

### <a name="solution-2-disable-all-implicit-evaluation"></a>#2 rozwiązania: Wyłącz wszystkie niejawne oceny

Jeśli poprzednie rozwiązania nie rozwiążą problemu, przejdź do **Tools**  >  **opcji**narzędzia, a następnie usuń zaznaczenie pola **Debuguj**  >  **Ogólne**  >  **Włącz Obliczanie właściwości i inne niejawne wywołania funkcji**. Spowoduje to wyłączenie najbardziej niejawnych ocen funkcji i powinno rozwiązać problem.
