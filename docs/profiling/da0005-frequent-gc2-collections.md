---
title: 'DA0005: Częste kolekcje GC2 | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a50567a101d77ed6498aaae13a5fe5556d9c1056
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777715"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Częste kolekcje GC2

|||
|-|-|
|Ruleid|DA0005|
|Kategoria|Użycie programu .NET Framework|
|Metoda profilowania|Pamięć .NET|
|Komunikat|Wiele obiektów są zbierane w generacji 2 wyrzucania elementów bezużytecznych.|
|Typ wiadomości|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Duża liczba obiektów pamięci .NET są odzyskiwane w generacji 2 wyrzucania elementów bezużytecznych.

## <a name="rule-description"></a>Opis reguły
 Środowisko wykonawcze języka wspólnego microsoft .NET (CLR) zapewnia mechanizm automatycznego zarządzania pamięcią, który używa modułu zbierającego elementy bezużyteczne do odzyskiwania pamięci z obiektów, które aplikacja nie jest już używana. Moduł zbierający elementy bezużyteczne jest zorientowany na generowanie, przy założeniu, że wiele alokacji są krótkotrwałe. Zmienne lokalne, na przykład, powinny być krótkotrwałe. Nowo utworzone obiekty rozpoczynają się w generacji 0 (gen 0), a następnie przechodzą do generacji 1, gdy przetrwają uruchomienie wyrzucania elementów bezużytecznych, a na koniec przejście do generacji 2, jeśli aplikacja nadal ich używa.

 Obiekty w generacji 0 są zbierane często i zwykle bardzo sprawnie. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajnie. Wreszcie, długowieczne obiekty w generacji 2 powinny być zbierane jeszcze rzadziej. Kolekcja generacji 2, która jest pełną operacją wyrzucania elementów bezużytecznych, jest również najdroższą operacją.

 Ta reguła jest uruchamiana, gdy proporcjonalnie wystąpiło zbyt wiele wyrzucania elementów bezużytecznych generacji 2. Jeśli zbyt wiele stosunkowo krótkotrwałe obiekty przetrwać kolekcji generacji 1, ale są następnie w stanie być zbierane w generacji 2 pełnej kolekcji, koszt zarządzania pamięcią może łatwo stać się nadmierne. Aby uzyskać więcej informacji, zobacz [mid-life post kryzysu](https://blogs.msdn.microsoft.com/ricom/2003/12/04/mid-life-crisis/) na Rico Mariani's Performance Tidbits na stronie internetowej MSDN.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Przejrzyj raporty [widoki danych pamięci .NET,](../profiling/dotnet-memory-data-views.md) aby zrozumieć wzorzec alokacji pamięci aplikacji. Użyj [widoku okres istnienia obiektu,](../profiling/object-lifetime-view.md) aby określić, które z obiektów danych programu są przeżywane do generacji 2, a następnie są odzyskiwane stamtąd. Użyj [widoku alokacji,](../profiling/dotnet-memory-allocations-view.md) aby określić ścieżkę wykonywania, która spowodowała te alokacje.

 Aby uzyskać informacje dotyczące zwiększania wydajności wyrzucania elementów [bezużytecznych, zobacz Podstawowe informacje o modułach zbierających elementy bezużyteczne i wskazówki dotyczące wydajności](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) w witrynie firmy Microsoft w sieci Web. Aby uzyskać informacje na temat narzutu automatycznego wyrzucania elementów [bezużytecznych, zobacz Sterta dużych obiektów odkryta](https://msdn.microsoft.com/magazine/cc534993.aspx).
