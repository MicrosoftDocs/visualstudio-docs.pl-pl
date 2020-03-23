---
title: 'DA0021: Wysoki wskaźnik odbioru śmieci gen 1 | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 36350b59a3d70f8553fddc5f58bf5c79716fa3aa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777663"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Wysoki stopień odzyskiwania pamięci Gen 1

|||
|-|-|
|Identyfikator reguły|DA0021|
|Kategoria|Użycie programu .NET Framework|
|Metody profilowania|Wszystkie|
|Komunikat|Istnieje dość wysoki wskaźnik gen 1 wyrzucania elementów bezużytecznych występujących. Jeśli zgodnie z projektem większość struktur danych programu są przydzielane i utrwalone przez długi czas, nie jest to zwykle problem. Jednak jeśli to zachowanie jest niezamierzone, aplikacja może być przypinanie obiektów. Jeśli nie masz pewności, można zebrać dane alokacji pamięci .NET i informacje o okresie istnienia obiektu, aby zrozumieć wzorzec alokacji pamięci używane przez aplikację.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Dane wydajności systemu, które zostały zebrane podczas profilowania wskazują, że znaczna część pamięci for.NET obiektów Framework została odzyskana w generacji 1 wyrzucania elementów bezużytecznych w porównaniu do generacji 0 zbieranie danych.

## <a name="rule-description"></a>Opis reguły
 Wspólny język microsoft .NET (CLR) zapewnia mechanizm automatycznego zarządzania pamięcią, który używa modułu zbierającego elementy bezużyteczne do odzyskiwania pamięci z obiektów, które aplikacja nie jest już używana. Moduł zbierający elementy bezużyteczne jest zorientowany na generowanie, przy założeniu, że wiele alokacji są krótkotrwałe. Zmienne lokalne, na przykład, powinny być krótkotrwałe. Nowo utworzone obiekty rozpoczynają się w generacji 0 (gen 0), a następnie przechodzą do generacji 1, gdy przetrwają uruchomienie wyrzucania elementów bezużytecznych, a na koniec przejście do generacji 2, jeśli aplikacja nadal ich używa.

 Obiekty w generacji 0 są zbierane często i zwykle bardzo sprawnie. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajnie. Wreszcie, długowieczne obiekty w generacji 2 powinny być zbierane jeszcze rzadziej. Kolekcja generacji 2, która jest pełną operacją wyrzucania elementów bezużytecznych, jest również najdroższą operacją.

 Ta reguła jest uruchamiana, gdy proporcjonalnie wystąpiło zbyt wiele wyrzucania elementów bezużytecznych generacji 1. Jeśli zbyt wiele obiektów dość krótkotrwałe przetrwać kolekcji generacji 0, ale są następnie w stanie być zbierane w kolekcji generacji 1, koszt zarządzania pamięcią może stać się nadmierne. Aby uzyskać więcej informacji, zobacz [mid-life post kryzysu](https://blogs.msdn.microsoft.com/ricom/2003/12/04/mid-life-crisis/) na Rico Mariani's Performance Tidbits na stronie internetowej MSDN.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczników](../profiling/marks-view.md) danych profilowania. Znajdź **.NET CLR\\Memory # kolekcji Gen 0** i **.NET CLR Memory\\# gen 1 kolekcje** kolumny. Określ, czy istnieją określone fazy wykonywania programu, w których wyrzucanie elementów bezużytecznych występuje częściej. Porównaj te wartości z **kolumną % time w gc,** aby sprawdzić, czy wzorzec alokacji pamięci zarządzanej powoduje nadmierne obciążenie związane z zarządzaniem pamięcią.

 Aby zrozumieć wzorzec aplikacji użycia pamięci zarządzanej, profil go ponownie uruchomiony a.NET profile alokacji pamięci i zażądać pomiarów okres istnienia obiektu.

 Aby uzyskać informacje dotyczące zwiększania wydajności wyrzucania elementów [bezużytecznych, zobacz Podstawowe informacje o modułach zbierających elementy bezużyteczne i wskazówki dotyczące wydajności](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) w witrynie firmy Microsoft w sieci Web. Aby uzyskać informacje na temat narzutu automatycznego wyrzucania elementów [bezużytecznych, zobacz Sterta dużych obiektów odkryta](https://msdn.microsoft.com/magazine/cc534993.aspx).
