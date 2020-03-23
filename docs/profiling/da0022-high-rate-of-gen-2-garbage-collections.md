---
title: 'DA0022: Wysoki wskaźnik odbioru śmieci gen 2 | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4e1fa46162f2aea74c5b3cb8396ad5e8d4c9a4cf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779379"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Wysoki stopień wyrzucania elementów bezużytecznych Gen 2

|||
|-|-|
|Identyfikator reguły|DA0022|
|Kategoria|Użycie programu .NET Framework|
|Metoda profilowania|Wszystkie|
|Komunikat|Istnieje dość wysoki wskaźnik gen 2 wyrzucania elementów bezużytecznych występujących. Jeśli zgodnie z projektem większość struktur danych programu są przydzielane i utrwalone przez długi czas, nie jest to zwykle problem. Jednak jeśli to zachowanie jest niezamierzone, aplikacja może być przypinanie obiektów. Jeśli nie masz pewności, można zebrać dane alokacji pamięci .NET i informacje o okresie istnienia obiektu, aby zrozumieć wzorzec alokacji pamięci używane przez aplikację.|
|Typ reguły|Ostrzeżenie|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Dane wydajności systemu, które zostały zebrane podczas profilowania wskazują, że znaczna część pamięci for.NET obiektów Framework została odzyskana w generacji 2 wyrzucania elementów bezużytecznych w porównaniu do generacji 0 i generacji 1 wyrzucania elementów bezużytecznych.

## <a name="rule-description"></a>Opis reguły
 Wspólny język microsoft .NET (CLR) zapewnia mechanizm automatycznego zarządzania pamięcią, który używa modułu zbierającego elementy bezużyteczne do odzyskiwania pamięci z obiektów, które aplikacja nie jest już używana. Moduł zbierający elementy bezużyteczne jest zorientowany na generowanie, przy założeniu, że wiele alokacji są krótkotrwałe. Zmienne lokalne, na przykład, powinny być krótkotrwałe. Nowo utworzone obiekty rozpoczynają się w generacji 0 (gen 0), a następnie przechodzą do generacji 1, gdy przetrwają uruchomienie wyrzucania elementów bezużytecznych, a na koniec przejście do generacji 2, jeśli aplikacja nadal ich używa.

 Obiekty w generacji 0 są zbierane często i zwykle bardzo sprawnie. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajnie. Wreszcie, długowieczne obiekty w generacji 2 powinny być zbierane jeszcze rzadziej. Kolekcja generacji 2, która jest pełną operacją wyrzucania elementów bezużytecznych, jest również najdroższą operacją.

 Ta reguła jest uruchamiana, gdy występuje proporcjonalnie zbyt wiele wyrzucania elementów bezużytecznych generacji 2. Dobrze zachowane aplikacje .NET Framework będą miały ponad 5 razy więcej niż generacji 1 wyrzucania elementów bezużytecznych jako kolekcje generacji 2. (Współczynnik 10x jest prawdopodobnie idealny.)

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczników](../profiling/marks-view.md) danych profilowania. Znajdź **.NET CLR\\Memory # kolekcji Gen 0** i **.NET CLR Memory\\# gen 1 kolekcje** kolumny. Określ, czy istnieją określone fazy wykonywania programu, w których wyrzucanie elementów bezużytecznych występuje częściej. Porównaj te wartości z **kolumną % time w gc,** aby sprawdzić, czy wzorzec alokacji pamięci zarządzanej powoduje nadmierne obciążenie związane z zarządzaniem pamięcią.

 Wysoki odsetek wyrzucania elementów bezużytecznych generacji 2 nie zawsze jest problemem. Może to być zgodnie z projektem. Aplikacja, która przydziela duże struktury danych, które muszą pozostać aktywne przez długi czas podczas wykonywania może wyzwolić tę regułę. Gdy taka aplikacja jest pod ciśnieniem pamięci, może być zmuszony do wykonywania częstych wyrzucania elementów bezużytecznych. Jeśli tańsze generacji 0 i generacji 1 wyrzucania elementów bezużytecznych można odzyskać tylko niewielką ilość pamięci zarządzanej, częściej generacji 2 wyrzucania elementów bezużytecznych zostaną zaplanowane.

 Istnieją dodatkowe kolumny pamięci CLR .NET w widoku znaczników, które mogą pomóc w identyfikowaniu problemów z wyrzucaniem elementów bezużytecznych. Kolumna **%time in GC** pomaga zrozumieć, jak bardzo występuje obciążenie związane z zarządzaniem pamięcią. Jeśli aplikacja zazwyczaj używa dość niewielką liczbę dużych, ale trwałe obiekty, a następnie częste kolekcje generacji 2 nie powinny zużywać nadmierne ilości czasu procesora CPU. Jeśli aplikacja znajduje się pod presją pamięci, ponieważ wymagana jest większa ilość pamięci fizycznej (RAM), mogą również zostać uruchamiane powiązane reguły oceniające wartości kolumny **Pamięć\Strony/s.**

 Aby zrozumieć wzorzec użycia pamięci zarządzanej przez aplikację, należy ponownie go profiluj a.NET profile alokacji pamięci i wybrać opcję Profilowanie w okresie istnienia obiektu.

 Aby uzyskać informacje dotyczące zwiększania wydajności wyrzucania elementów [bezużytecznych, zobacz Podstawowe informacje o modułach zbierających elementy bezużyteczne i wskazówki dotyczące wydajności](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) w witrynie firmy Microsoft w sieci Web. Aby uzyskać informacje na temat narzutu automatycznego wyrzucania elementów [bezużytecznych, zobacz Sterta dużych obiektów odkryta](https://msdn.microsoft.com/magazine/cc534993.aspx).
