---
title: 'Błąd: szacowanie &#39;funkcji&#39; Przekroczono limit czasu i wymaganie przerwania w sposób niebezpieczny | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a27bf67770eef770fddef0301a804e6c45579539
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387125"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Błąd: szacowanie &#39;funkcji&#39; przekroczony limit czasu i wymaganie przerwania w sposób niebezpieczny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pełny tekst komunikatu: przekroczono limit czasu obliczania funkcji "Function" i wymaganie zostało przerwane w sposób niebezpieczny. Może to spowodować uszkodzenie procesu docelowego. 

Aby ułatwić sprawdzenie stanu obiektów .NET, debuger automatycznie wymusi w debugowanym procesie uruchomić dodatkowy kod (zazwyczaj metody pobierające właściwości i funkcje ToString). W większości przypadków te funkcje są szybko i ułatwiają debugowanie. Jednak debuger nie uruchamia aplikacji w piaskownicy. W związku z tym metoda pobierająca lub ToString właściwości, która wywołuje funkcję natywną, która przestaje odpowiadać, może prowadzić do długotrwałych limitów czasu, które mogą nie być możliwe do odzyskania. Ten komunikat o błędzie wystąpił.
 
Jednym z typowych przyczyn tego problemu jest to, że gdy debuger szacuje właściwość, umożliwia tylko poddane inspekcji do wykonania. Dlatego jeśli właściwość oczekuje na inne wątki do uruchomienia w debugowanej aplikacji i jeśli oczekuje na to, że środowisko uruchomieniowe platformy .NET nie może przerwać działania, ten problem wystąpi.
 
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd
 
Istnieją trzy możliwe rozwiązania tego problemu.
 
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
 
Jeśli poprzednie rozwiązania nie rozwiążą problemu, przejdź do *Tools*  /  *opcji*narzędzia, a następnie usuń zaznaczenie pola *Debuguj*  /  *Ogólne*  /  *Włącz Obliczanie właściwości i inne niejawne wywołania funkcji*. Spowoduje to wyłączenie najbardziej niejawnych ocen funkcji i powinno rozwiązać problem.
