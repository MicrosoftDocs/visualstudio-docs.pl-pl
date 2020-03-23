---
title: 'DA0023: Wysoki czas procesora GC | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f0dd45486f526954d7dfce45cd607ff6196eae00
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777650"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Wysokie wykorzystanie czasu GC CPU

|||
|-|-|
|Identyfikator reguły|DA0023|
|Kategoria|Użycie programu .NET Framework|
|Metoda profilowania|Wszystkie|
|Komunikat|% czasu w GC jest dość wysoki. To wskazanie nadmiernej ilości elementów bezużytecznych obciążenie może mieć wpływ na szybkość reakcji aplikacji. Można zebrać dane alokacji pamięci .NET i informacje o okresie istnienia obiektu, aby lepiej zrozumieć wzorzec alokacji pamięci, którego aplikacja używa.|
|Typ reguły|Informacyjne|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Dane wydajności systemu, który jest zbierany podczas profilowania wskazuje, że ilość czasu spędzonego w wyrzucaniu elementów bezużytecznych jest znacząca w porównaniu z całkowitym czasem przetwarzania aplikacji.

## <a name="rule-description"></a>Opis reguły
 Wspólny język microsoft .NET (CLR) zapewnia mechanizm automatycznego zarządzania pamięcią, który używa modułu zbierającego elementy bezużyteczne do odzyskiwania pamięci z obiektów, które aplikacja nie jest już używana. Moduł zbierający elementy bezużyteczne jest zorientowany na generowanie, przy założeniu, że wiele alokacji są krótkotrwałe. Zmienne lokalne, na przykład, powinny być krótkotrwałe. Nowo utworzone obiekty rozpoczynają się w generacji 0 (gen 0), a następnie przechodzą do generacji 1, gdy przetrwają uruchomienie wyrzucania elementów bezużytecznych, a na koniec przejście do generacji 2, jeśli aplikacja nadal ich używa.

 Obiekty w generacji 0 są zbierane często i wydajnie. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajnie. Wreszcie, długowieczne obiekty w generacji 2 powinny być zbierane jeszcze rzadziej. Kolekcja generacji 2, która jest pełną operacją wyrzucania elementów bezużytecznych, jest również najdroższą operacją.

 Ta reguła jest uruchamiana, gdy ilość czasu spędzonego w wyrzucaniu elementów bezużytecznych jest znacząca w porównaniu z całkowitym czasem przetwarzania aplikacji.

> [!NOTE]
> Gdy proporcja czasu spędzonego w wyrzucaniu elementów bezużytecznych jest nadmierna w porównaniu z całkowitym czasem przetwarzania aplikacji, zamiast tej reguły jest uruchamiane ostrzeżenie [o czasie procesora DA0024: Nadmierny czas procesora GC](../profiling/da0024-excessive-gc-cpu-time.md) zamiast tej reguły.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczników](../profiling/marks-view.md) danych profilowania. Znajdź kolumnę **.NET\\CLR Memory % time w** kolumnie GC. Określ, czy istnieją określone fazy wykonywania programu, gdzie obciążenie związane z wyrzucaniem elementów bezużytecznych pamięci zarządzanej jest cięższe niż inne fazy. Porównaj wartości % czasu w GC wartość do szybkości wyrzucania **elementów bezużytecznych zgłoszonych w # gen 0 kolekcje**, **# gen 1 kolekcje**, **# gen 2 kolekcje** wartości.

 Wartość % czasu w gc próbuje zgłosić czas, który aplikacja spędza na wykonywaniu wyrzucania elementów bezużytecznych proporcjonalnie do całkowitej ilości przetwarzania. Należy pamiętać, że istnieją okoliczności, gdy % czasu w gc wartość może zgłosić wysoką wartość, ale nie jest z powodu nadmiernego wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji na temat sposobu obliczania % czasu w wartości GC, zobacz [różnica między danymi perf zgłoszonymi przez różne narzędzia — 4](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) wpis **bloga Maoni** w sieci MSDN. Jeśli występują błędy strony lub aplikacja jest wywłaszczona przez inne prace o wyższym priorytecie na komputerze podczas wyrzucania elementów bezużytecznych, licznik % czasu w gc będzie odzwierciedlać te dodatkowe opóźnienia.
