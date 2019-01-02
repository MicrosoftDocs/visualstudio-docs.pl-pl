---
title: 'DA0005: Częste kolekcje GC2 | Dokumentacja firmy Microsoft'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41e6ed5396a58bb6f3c39f9addbcd36b8dfaa7e6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948579"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Częste kolekcje GC2

|||  
|-|-|  
|Identyfikator reguły|DA0005|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metoda profilowania|Pamięć .NET|  
|Komunikat|Wiele obiektów są zbierane w generacji 2 wyrzucania elementów bezużytecznych.|  
|Typ komunikatu|Ostrzeżenie|  

## <a name="cause"></a>Przyczyna  
 Dużą liczbę obiektów pamięci platformy .NET są są odzyskiwane w generacji 2 wyrzucania elementów bezużytecznych.  

## <a name="rule-description"></a>Opis reguły  
 Microsoft .NET środowisko uruchomieniowe języka wspólnego (CLR) zapewnia mechanizm zarządzania pamięcią automatyczną, który używa modułu odśmiecania pamięci, aby odzyskać pamięci z obiektów, które aplikacja już używa. Moduł odśmiecania pamięci jest zorientowana na generowanie na podstawie założenia, że wiele alokacje są krótkotrwałe. Na przykład, zmienne lokalne, powinny być krótkotrwały. Nowo utworzonych obiektach Uruchom w generacji 0 (gen 0), a następnie przejść do generacji 1, po ich przetrwać wyrzucania elementów bezużytecznych, uruchom, a na koniec przejścia do generacji 2, jeśli aplikacja nadal korzysta z nich.  

 Obiekty w generacji 0 są zbierane, często i zazwyczaj bardzo wydajny sposób. Obiekty w generacji 1 są zbierane rzadziej i mniej skuteczne. Na koniec długotrwałe obiekty w generacji 2 powinny być zbierane nawet rzadziej. Kolekcji generacji 2, która znajduje się pełne wyrzucanie elementów bezużytecznych, uruchamianie, jest również najbardziej kosztowną operacją.  

 Ta reguła jest uruchamiana podczas proporcjonalnie za dużo generacji 2 wyrzucania elementów bezużytecznych miały miejsce. Jeśli zbyt wiele obiektów stosunkowo krótkotrwałe przetrwać bezużytecznych generacji 1, ale będą w stanie mają być zbierane w generacji 2 pełnego, koszty zarządzania pamięci mogą łatwo stać się nadmierne. Aby uzyskać więcej informacji, zobacz [kryzysu środku życia](http://go.microsoft.com/fwlink/?LinkId=177835) publikować informacje o technologii Rico Mariani wydajności w witrynie MSDN w sieci Web.  

## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Przegląd [widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md) raportów, aby poznać wzorce przydzielania pamięci w aplikacji. Użyj [widok okresu istnienia obiektu](../profiling/object-lifetime-view.md) umożliwia określenie, które uszkodziło danych obiekty są pozostałych do generacji 2, a następnie odzyskać z tego miejsca. Użyj [Widok alokacji](../profiling/dotnet-memory-allocations-view.md) można ustalić ścieżki wykonywania, które spowodowały tych przydziałów.  

 Aby dowiedzieć się, jak poprawić wydajność odzyskiwania pamięci zbierania danych, zobacz [podstawy modułu odśmiecania pamięci i wskazówki dotyczące wydajności](http://go.microsoft.com/fwlink/?LinkId=148226) w witrynie sieci Web firmy Microsoft. Aby uzyskać informacje na temat obciążenie automatyczne wyrzucanie elementów bezużytecznych, zobacz [duży obiekt sterty Niepokryty](http://go.microsoft.com/fwlink/?LinkId=177836).