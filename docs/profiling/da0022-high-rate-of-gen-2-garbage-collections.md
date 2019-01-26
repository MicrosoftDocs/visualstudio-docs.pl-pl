---
title: 'DA0022: Duża częstotliwość odzyskiwania pamięci Gen 2 | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: d810f9f04a408d3f155265d3ed9f8fadaea462f9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027779"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Duża częstotliwość odzyskiwania pamięci Gen 2

|||  
|-|-|  
|Identyfikator reguły|DA0022|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metoda profilowania|Wszystkie|  
|Komunikat|Istnieje stosunkowo wysoki stopień Gen 2 wyrzucania elementów bezużytecznych występuje. Jeśli zgodnie z projektem, większość struktur danych programu są przydzielane i utrwalane na dłuższy czas, to nie jest zazwyczaj problem. Jednak w przypadku niezamierzonego to zachowanie aplikacji może być przypinanie obiektów. Jeśli nie masz pewności, możesz zbierać .NET pamięć alokacji danych i obiekt informacji o czasie życia poznać wzorce przydzielania pamięci używane przez aplikację.|  
|Typ reguły|Ostrzeżenie|  

 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  

## <a name="cause"></a>Przyczyna  
 Dane o wydajności systemu, które zostały zebrane podczas profilowania wskazuje, że znaczna część obiekty struktury for.NET pamięci zostało odzyskane w generacji 2, wyrzucanie elementów bezużytecznych w porównaniu do generacji 0 i 1 wyrzucania generacji.  

## <a name="rule-description"></a>Opis reguły  
 Microsoft .NET wspólnego języka środowiska wykonawczego (języka wspólnego CLR) zapewnia mechanizm zarządzania pamięcią automatyczną, który używa modułu odśmiecania pamięci, aby odzyskać pamięci z obiektów, które aplikacja już używa. Moduł odśmiecania pamięci jest zorientowana na generowanie na podstawie założenia, że wiele alokacje są krótkotrwałe. Na przykład, zmienne lokalne, powinny być krótkotrwały. Nowo utworzonych obiektach Uruchom w generacji 0 (gen 0), a następnie przejść do generacji 1, po ich przetrwać wyrzucania elementów bezużytecznych, uruchom, a na koniec przejścia do generacji 2, jeśli aplikacja nadal korzysta z nich.  

 Obiekty w generacji 0 są zbierane, często i zazwyczaj bardzo wydajny sposób. Obiekty w generacji 1 są zbierane rzadziej i mniej skuteczne. Na koniec długotrwałe obiekty w generacji 2 powinny być zbierane nawet rzadziej. Kolekcji generacji 2, która znajduje się pełne wyrzucanie elementów bezużytecznych, uruchamianie, jest również najbardziej kosztowną operacją.  

 Ta reguła jest uruchamiana podczas proporcjonalnie za dużo występują 2 wyrzucania elementów bezużytecznych generacji. Dobrze działające aplikacje programu .NET Framework ma więcej niż 5 razy więcej generacji 1 wyrzucania elementów bezużytecznych, jak kolekcje geenracji 2. (Prawdopodobnie idealnym rozwiązaniem jest współczynnik 10 x).  

## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź **pamięć .NET CLR\\# pokolenia 0** i **pamięć .NET CLR\\# zbierania obiektów pokolenia 1** kolumn. Określa, czy określone faz wykonywania programu gdzie wyrzucania elementów bezużytecznych występuje częściej. Porównanie tych wartości, aby **czas działania modułu GC (%)** kolumny, aby zobaczyć, jeśli wzorzec alokacje pamięci zarządzanej powoduje narzutu związanego z zarządzaniem zbyt dużej ilości pamięci.  

 Dużą część 2. generacji wyrzucania elementów bezużytecznych nie zawsze jest problemem. Może to być zgodne z projektem. Aplikacja, która przydziela struktury dużych ilości danych, które muszą pozostać aktywne przez długi czas podczas wykonywania może wywołać tę regułę. Po takiej aplikacji występuje duże wykorzystanie pamięci, mogą być zmuszeni do wykonywania częstych wyrzucania elementów bezużytecznych. Jeśli mniej kosztowne generacji 0 i 1 generacji wyrzucania elementów bezużytecznych może odzyskać pamięci małą ilością zarządzane, zostanie zaplanowane częściej bezużytecznych generacji 2.  

 Istnieją dodatkowe kolumny pamięć .NET CLR w widoku znaczniki, które mogą pomóc w identyfikowaniu problemów kolekcji wyrzucania elementów. **Czas działania modułu GC (%)** kolumny pomaga zrozumieć, występuje narzutu związanego z zarządzaniem ilości pamięci. Jeśli aplikacja używa zwykle stosunkowo niewielkiej liczby dużych, ale trwałe obiekty, następnie częste kolekcji generacji 2 nie może przekroczyć nadmiernej ilości czasu procesora CPU. Jeśli aplikacja jest duże wykorzystanie pamięci, ponieważ więcej pamięci fizycznej (RAM) jest wymagane, powiązane reguły, które oceny **Pamięć\Strony/s** wartości w kolumnie mogą również wyzwalać.  

 Aby poznać wzorzec użycia pamięci zarządzanej aplikacji, będzie ponownie działać profilu alokacji pamięci obfuskatorem profilu, a następnie wybierz profilowania opcję okres istnienia obiektu.  

 Aby dowiedzieć się, jak poprawić wydajność odzyskiwania pamięci zbierania danych, zobacz [podstawy modułu odśmiecania pamięci i wskazówki dotyczące wydajności](http://go.microsoft.com/fwlink/?LinkId=148226) w witrynie sieci Web firmy Microsoft. Aby uzyskać informacje na temat obciążenie automatyczne wyrzucanie elementów bezużytecznych, zobacz [duży obiekt sterty Niepokryty](http://go.microsoft.com/fwlink/?LinkId=177836).