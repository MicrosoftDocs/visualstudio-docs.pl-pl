---
title: 'DA0014: Bardzo wysokie szybkości stronicowania aktywnej pamięci na dysku | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e068771ba0fcc9b044ba7ff5243a75ceb3161e03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779417"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014: Wyjątkowo wysoki stopień stronicowania aktywnej pamięci na dysku

|||
|-|-|
|Identyfikator reguły|DA0014|
|Kategoria|Pamięć i stronicowanie|
|Metoda profilowania|Wszystkie|
|Komunikat|Występuje bardzo wysoka szybkość stronicowania aktywnej pamięci na dysku. Aplikacja może być związana z pamięcią.|
|Typ reguły|Ostrzeżenie|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 25 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Dane wydajności systemu, które zostały zebrane w przebiegu profilowania wskazuje, że bardzo wysoki wskaźnik stronicowania aktywnej pamięci do i z dysku wystąpił podczas wykonywania profilowania. Szybkość stronicowania na tym poziomie zwykle wpływa na wydajność aplikacji i szybkość reakcji. Należy rozważyć zmniejszenie alokacji pamięci przez zmianę algorytmów. Może być również należy wziąć pod uwagę wymagania dotyczące pamięci aplikacji. ponowne uruchamianie profilowania na komputerze z większą pamięcią.

## <a name="rule-description"></a>Opis reguły
 Nadmierne stronicowanie na dysku może być spowodowane brakiem pamięci fizycznej. Jeśli operacje stronicowania dominują przy użyciu dysku fizycznego, na którym znajduje się plik stronicowania, mogą spowolnić inne operacje dysku zorientowane na aplikację na tym samym dysku.

 Często strony są odczytywane z dysku lub zapisywane na dysku w zbiorczych operacjach stronicowania. Liczba stron wyjściowych/s jest często znacznie większa niż liczba zapisów strony/s, na przykład. Ponieważ dane wyjściowe stron/s obejmują również zmienione strony danych z pamięci podręcznej plików systemowych. Jednak nie zawsze jest łatwo określić, który proces jest bezpośrednio odpowiedzialny za stronicowanie lub dlaczego.

> [!NOTE]
> Ta reguła jest uruchamiana, gdy poziomy stronicowania pamięci aktywnej osiągają bardzo wysoki poziom. Gdy poziom stronicowania jest znaczący, ale nie ekstremalny, reguła informacyjna [DA0017: Wysokie szybkości stronicowania aktywnej pamięci do dysków](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md) są uruchamiane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Kliknij dwukrotnie wiadomość w oknie Lista błędów, aby przejść do widoku [Znaczniki.](../profiling/marks-view.md) Znajdź kolumnę **Pamięć\Strony/s.** Określ, czy istnieją określone fazy wykonywania programu, w których działanie we/wy stronicowania jest cięższe niż inne.

 Jeśli zbierasz dane profilu dla aplikacji ASP.NET w scenariuszu testowania obciążenia, spróbuj ponownie uruchomić test obciążenia na komputerze skonfigurowanym z dodatkową pamięcią fizyczną (lub pamięcią RAM).

 Należy rozważyć zmniejszenie alokacji pamięci, zmieniając algorytmy i unikając interfejsów API intensywnie korzystających z pamięci, takich jak String.Concat i String.Substring.
