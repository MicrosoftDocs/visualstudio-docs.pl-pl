---
title: 'DA0022: wysoka szybkość wyrzucania elementów bezużytecznych generacji 2 | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: ba70e303c3164417890be51e834d86d8983526cf
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72910533"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Wysoki stopień wyrzucania elementów bezużytecznych Gen 2

|||
|-|-|
|Identyfikator reguły|DA0022|
|Kategoria|Użycie .NET Framework|
|Metoda profilowania|Wszystkie|
|Komunikat|Występuje dość duża liczba wyrzucania elementów bezużytecznych generacji 2. W przypadku, gdy konstrukcja większość struktur danych programu jest alokowana i utrwalana przez dłuższy czas, nie jest to problem. Jeśli jednak takie zachowanie jest niezamierzone, aplikacja może przypinać obiekty. Jeśli nie masz pewności, możesz zebrać dane alokacji pamięci .NET i informacje o okresie istnienia obiektu, aby zrozumieć wzorzec alokacji pamięci używanej przez aplikację.|
|Typ reguły|Ostrzeżenie|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Dane wydajności systemu, które zostały zebrane podczas profilowania wskazują, że znacząca część obiektów for.NET pamięci programu Memory została odbrana w ramach generacji 2 wyrzucania elementów bezużytecznych w porównaniu do generacji 0 i wyrzucania elementów bezużytecznych generacji 1.

## <a name="rule-description"></a>Opis reguły
 Microsoft .NET Common Language Time (CLR) zapewnia automatyczny mechanizm zarządzania pamięcią, który używa modułu wyrzucania elementów bezużytecznych do odzyskiwania pamięci z obiektów, które nie są już używane przez aplikację. Moduł wyrzucania elementów bezużytecznych jest oparty na generacji, w oparciu o założenie, że wiele alokacji jest krótkoterminowych. Zmienne lokalne, na przykład, powinny być krótkotrwałe. Nowo utworzone obiekty rozpoczynają się w generacji 0 (Gen 0), a następnie postępować w generacji 1, gdy zajmują się uruchomieniem odzyskiwania pamięci, a wreszcie przechodzą do generacji 2, jeśli aplikacja nadal używa tych danych.

 Obiekty w generacji 0 są zbierane często i zwykle bardzo wydajnie. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajne. Na koniec obiekty długotrwałe w generacji 2 powinny być zbierane nawet rzadziej. Kolekcja 2 generacji, która jest pełnym przebiegiem odzyskiwania pamięci, jest również najtańszą operacją.

 Ta reguła jest wyzwalana, gdy występuje zbyt wiele wyrzucania elementów bezużytecznych generacji 2. Dobrze działające .NET Framework aplikacje będą mieć więcej niż 5 razy więcej niż raz w przypadku kolekcji generacji 2. (Współczynnik 10X jest prawdopodobnie idealny).

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź **pamięć środowiska .NET clr\\liczba kolekcji gen 0** i\\liczba kolumn **kolekcji generacji 1 środowiska CLR** . Ustal, czy istnieją konkretne etapy wykonywania programu, w których wyrzucanie elementów bezużytecznych występuje częściej. Porównaj te wartości w kolumnie **% Time w usłudze GC** , aby sprawdzić, czy wzorzec alokacji pamięci zarządzanej powoduje nadmierne obciążenie zarządzania pamięcią.

 W przypadku dużej części wyrzucania elementów bezużytecznych generacji 2 nie zawsze występuje problem. Może być zaprojektowana. Aplikacja, która alokuje duże struktury danych, które muszą pozostawać aktywne przez długie okresy podczas wykonywania, może wyzwolić tę regułę. Gdy taka aplikacja korzysta z pamięci, może być wymuszone wykonywanie częstych wyrzucania elementów bezużytecznych. Jeśli wyrzucanie elementów bezużytecznych generacji 0 i generacja 1 może odistnieć tylko niewielką ilość pamięci zarządzanej, planowane jest przetworzenie częściowej generacji 2 wyrzucania elementów bezużytecznych.

 W widoku znaczniki znajdują się dodatkowe kolumny pamięci CLR platformy .NET, które mogą pomóc identyfikować problemy z wyrzucaniem elementów bezużytecznych. **Czas (%) w kolumnie GC** pomaga zrozumieć, ile miejsca jest związane z zarządzaniem pamięcią. Jeśli aplikacja zwykle używa dość małej liczby dużych, ale trwałych obiektów, to częste kolekcje 2 generacji nie powinny zużywać nadmiernych ilości czasu procesora CPU. Jeśli aplikacja działa w pamięci, ponieważ jest wymagana większa ilość pamięci fizycznej (RAM), powiązane reguły, które ocenią wartości kolumny **pamięć \ strony/s** , mogą również być uruchamiane.

 Aby zrozumieć wzorzec zastosowania pamięci zarządzanej, należy go ponownie uruchomić przy użyciu profilu alokacji pamięci a.NET i wybrać opcję profilowania okresu istnienia obiektu.

 Aby uzyskać informacje na temat zwiększania wydajności odzyskiwania pamięci, zobacz [podstawy modułu zbierającego elementy bezużyteczne i wskazówki dotyczące wydajności](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) w witrynie sieci Web firmy Microsoft. Aby uzyskać informacje o obciążeniu automatycznego odzyskiwania pamięci, zapoznaj się z [pokrytym stertą dużego obiektu](https://msdn.microsoft.com/magazine/cc534993.aspx).