---
title: 'Błąd: Obliczenie funkcji &#39;funkcja&#39; przekroczyła limit czasu i konieczne było przerwanie procesu w niebezpieczny sposób | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d5a992751e31f21a7875091b4c8b1be9bd0bd0a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197066"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Błąd: Obliczenie funkcji &#39;funkcja&#39; przekroczyła limit czasu i konieczne było przerwanie procesu w niebezpieczny sposób
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Komunikat pełny tekst: Ocena funkcji "function" Upłynął limit czasu i konieczne było przerwanie procesu w niebezpieczny sposób. Może to uszkodzenia procesu docelowego. 

Aby ułatwić sprawdzić stan obiektów platformy .NET, debuger automatycznie wymusi debugowanego procesu do uruchomienia dodatkowych kodu (zwykle metody pobierającej właściwości i funkcji ToString). W większości przypadków wszystkie te funkcje są wykonywane szybko i znacznie ułatwia debugowanie. Debuger nie uruchamiać aplikację w piaskownicy. W rezultacie metoda pobierająca właściwości lub metody ToString, który wywołuje w funkcji natywnej, która jest używana z może prowadzić do długie limity czasu, który może nie być możliwe do odzyskania. Jeśli napotkasz ten komunikat o błędzie, ten błąd wystąpił.
 
Jednym z najczęstszych przyczyn tego problemu jest gdy debuger ocenia właściwością, tylko możliwość wątku poddawana do wykonania. Więc jeśli właściwość oczekuje na inne wątki były uruchomione w debugowanym aplikacji i oczekuje ono w taki sposób, że środowisko uruchomieniowe platformy .NET nie jest w stanie przerwania, ten problem będzie się zdarzyć.
 
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd
 
Istnieją trzy możliwe rozwiązania tego problemu.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Rozwiązanie #1: Debuger uniemożliwić wywołanie metody pobierającej właściwości lub metody ToString
 
Komunikat o błędzie informuje o nazwę funkcji, w której debuger próbował wywołać. Jeśli zmodyfikujesz tę funkcję, można uniemożliwić wywołanie metody pobierającej właściwości lub metody ToString debugera. Wypróbuj jedną z następujących czynności:
 
* Zmienić metodę na inny rodzaj kodu oprócz pobierającą właściwość lub metoda ToString i problem znikną.
    —lub—
* (W przypadku ToString) Zdefiniuj atrybut DebuggerDisplay od typu, i może mieć debugera coś innego niż ToString oceny.
    —lub—
* (Dla metody pobierającej właściwości) Umieść `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atrybutu dla właściwości. Może to być przydatne, jeśli masz metodę, która musi znajdować się właściwości interfejsu API ze względu na zgodność, ale należy go tak naprawdę metody.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Rozwiązanie #2: Kod docelowy, poproś debugera, aby przerwać oceny
 
Komunikat o błędzie informuje o nazwę funkcji, w której debuger próbował wywołać. Jeśli metoda pobierająca właściwości lub metody ToString niepowodzenia by działała poprawnie, szczególnie w sytuacjach, gdy ten problem, które jest kod wymaga innego wątku, aby uruchomić kod, a następnie wywołać funkcję implementacji `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` poprosić debugera do przerwania funkcji Ocena. Za pomocą tego rozwiązania jest nadal możliwe jawnie ocenić tych funkcji, ale domyślne zachowanie to, zatrzyma wykonywanie po wystąpieniu wywołania NotifyOfCrossThreadDependency.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Rozwiązanie #3: Wyłącz wszystkie bezwarunkowa ocena
 
Jeśli poprzednie rozwiązania nie rozwiązują problemu, przejdź do strony *narzędzia* / *opcje*i usuń zaznaczenie opcji *debugowanie*  /   *Ogólne* / *Włącz obliczanie właściwości i inne niejawne wywołania funkcji*. To spowoduje wyłączenie większość Obliczanie funkcji niejawnie i powinno rozwiązać problem.
