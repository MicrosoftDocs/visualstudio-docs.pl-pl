---
title: 'DA0021: Duża częstotliwość odzyskiwania pamięci Gen 1 | Dokumentacja firmy Microsoft'
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
ms.workload:
- multiple
ms.openlocfilehash: cd10bd9eb834a3ca41fce38baf11e36b13fe0734
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639131"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Duża częstotliwość odzyskiwania pamięci Gen 1

|||
|-|-|
|Identyfikator reguły|DA0021|
|Kategoria|Sposób użycia programu .NET framework|
|Metod profilowania|Wszystkie|
|Komunikat|Istnieje stosunkowo wysoki stopień Gen 1 wyrzucania elementów bezużytecznych występuje. Jeśli zgodnie z projektem, większość struktur danych programu są przydzielane i utrwalane na dłuższy czas, to nie jest zazwyczaj problem. Jednak w przypadku niezamierzonego to zachowanie aplikacji może być przypinanie obiektów. Jeśli nie masz pewności, możesz zbierać .NET pamięć alokacji danych i obiekt informacji o czasie życia poznać wzorce przydzielania pamięci używane przez aplikację.|
|Typ reguły|Informacje|

 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.

## <a name="cause"></a>Przyczyna
 Dane o wydajności systemu, które zostały zebrane podczas profilowania wskazuje, że znaczna część obiekty struktury for.NET pamięci zostało odzyskane w generację 1 wyrzucania elementów bezużytecznych w porównaniu do generacji 0 danych kolekcji.

## <a name="rule-description"></a>Opis reguły
 Microsoft .NET wspólnego języka środowiska wykonawczego (języka wspólnego CLR) zapewnia mechanizm zarządzania pamięcią automatyczną, który używa modułu odśmiecania pamięci, aby odzyskać pamięci z obiektów, które aplikacja już używa. Moduł odśmiecania pamięci jest zorientowana na generowanie na podstawie założenia, że wiele alokacje są krótkotrwałe. Na przykład, zmienne lokalne, powinny być krótkotrwały. Nowo utworzonych obiektach Uruchom w generacji 0 (gen 0), a następnie przejść do generacji 1, po ich przetrwać wyrzucania elementów bezużytecznych, uruchom, a na koniec przejścia do generacji 2, jeśli aplikacja nadal korzysta z nich.

 Obiekty w generacji 0 są zbierane, często i zazwyczaj bardzo wydajny sposób. Obiekty w generacji 1 są zbierane rzadziej i mniej skuteczne. Na koniec długotrwałe obiekty w generacji 2 powinny być zbierane nawet rzadziej. Kolekcji generacji 2, która znajduje się pełne wyrzucanie elementów bezużytecznych, uruchamianie, jest również najbardziej kosztowną operacją.

 Ta reguła jest uruchamiana podczas proporcjonalnie za dużo wystąpiły 1 wyrzucania elementów bezużytecznych generacji. Za dużo obiektów dość krótkotrwałe przetrwać bezużytecznych generacji 0, ale będą w stanie mają być zbierane w kolekcji generacji 1, koszty zarządzania pamięci może być nadmierne. Aby uzyskać więcej informacji, zobacz [kryzysu środku życia](http://go.microsoft.com/fwlink/?LinkId=177835) publikować informacje o technologii Rico Mariani wydajności w witrynie MSDN w sieci Web.

## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź **pamięć .NET CLR\\# pokolenia 0** i **pamięć .NET CLR\\# zbierania obiektów pokolenia 1** kolumn. Określa, czy określone faz wykonywania programu gdzie wyrzucania elementów bezużytecznych występuje częściej. Porównanie tych wartości, aby **czas działania modułu GC (%)** kolumny, aby zobaczyć, jeśli wzorzec alokacje pamięci zarządzanej powoduje narzutu związanego z zarządzaniem zbyt dużej ilości pamięci.

 Aby poznać wzorzec użycia pamięci zarządzanej aplikacji, profilować będzie ponownie działać alokacji pamięci obfuskatorem pomiarów okres istnienia obiektu profilu i żądania.

 Aby dowiedzieć się, jak poprawić wydajność odzyskiwania pamięci zbierania danych, zobacz [podstawy modułu odśmiecania pamięci i wskazówki dotyczące wydajności](http://go.microsoft.com/fwlink/?LinkId=148226) w witrynie sieci Web firmy Microsoft. Aby uzyskać informacje na temat obciążenie automatyczne wyrzucanie elementów bezużytecznych, zobacz [duży obiekt sterty Niepokryty](http://go.microsoft.com/fwlink/?LinkId=177836).