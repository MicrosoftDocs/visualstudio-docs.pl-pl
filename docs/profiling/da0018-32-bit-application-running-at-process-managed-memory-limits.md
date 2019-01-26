---
title: 'DA0018: Aplikacja 32-bitowa działa w procesie granicach pamięci zarządzanej | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 65ee298aab44613f87764bc66d901476e6ccbfd4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070386"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018: Aplikacja 32-bitowa działa w limity pamięci proces zarządzany

|||  
|-|-|  
|Identyfikator reguły|DA0018|  
|Kategoria|Użycie narzędzia profilowania|  
|Metoda profilowania|Próbkowania|  
|Komunikat|Zarządzane alokacji pamięci, zbliża się limit domyślny dla procesu 32-bitowych. Aplikacja może być powiązane z pamięci.|  
|Typ reguły|Ostrzeżenie|  

 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  

## <a name="cause"></a>Przyczyna  
 System danych zebranych podczas uruchomienia profilowania wskazuje, że pamięci .NET Framework stosów skontaktowali maksymalnego rozmiaru sterty zarządzanej może nawiązać połączenie w procesie 32-bitowym. Ten maksymalny rozmiar jest wartością domyślną. Jest ona oparta na łączną ilość przestrzeni adresowej procesu, która może być przydzielona dla prywatnych bajtów. Zgłaszana wartość to maksimum zaobserwowane WE wartość sterty podczas aktywnego PROFILOWANEGO procesu. Należy wziąć pod uwagę, profilowanie ponownie przy użyciu metody profilowania pamięci .NET i optymalizację użycia zasobów zarządzanych przez aplikację.  

 Gdy rozmiar zarządzanej sterty podejście domyślny limit, proces zbierania automatyczne wyrzucanie elementów może być konieczne wywoływanej częściej. Zwiększa to narzut na zarządzanie pamięcią.  

 Reguła jest uruchamiana tylko dla 32-bitowymi aplikacjami działającymi na komputerach 32-bitowych.  

## <a name="rule-description"></a>Opis reguły  
 Microsoft .NET wspólnego języka środowiska wykonawczego (języka wspólnego CLR) zapewnia mechanizm zarządzania pamięcią automatyczną, który używa modułu odśmiecania pamięci, aby odzyskać pamięci z obiektów, które aplikacja już używa. Moduł odśmiecania pamięci jest zorientowana na generowanie na podstawie założenia, że wiele alokacje są krótkotrwałe. Na przykład, zmienne lokalne, powinny być krótkotrwały. Nowo utworzonych obiektach Uruchom w generacji 0 (gen 0), a następnie przejść do generacji 1, po ich przetrwać wyrzucania elementów bezużytecznych, uruchom, a na koniec przejścia do generacji 2, jeśli aplikacja nadal korzysta z nich.  

 Zarządzane obiekty, które są większe niż 85 KB są przydzielane sterty obiektów wielkich, której podlegają rzadsze wyrzucania elementów bezużytecznych i kompaktowania niż mniejsze obiekty. duże obiekty są zarządzane oddzielnie, ponieważ zakłada się, że są one więcej trwały i ponieważ mieszanie trwałego, jak i dużych obiektów z często przydzielone obiekty mniejszych może utworzyć rzutowania najgorszy fragmentację sterty.  

 Ponieważ całkowity rozmiar zarządzanej sterty podejście domyślny limit, obciążenie zarządzanie pamięcią zwykle zwiększa się do punktu, w którym można uruchomić mających wpływ na czas odpowiedzi i skalowalność aplikacji.  

## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [znaczniki](../profiling/marks-view.md) widoku. Znajdź **pamięć .NET CLR\\# bajtów we wszystkich Stertach** i **# łączna liczba zadeklarowanych bajtów** kolumn. Określa, czy określone faz wykonywania programu gdzie alokacji pamięci zarządzanej jest większe niż pozostałych faz. Porównaj wartości **# bajtów we wszystkich Stertach** kolumny do szybkości wyrzucania elementów bezużytecznych zgłoszone w **pamięć .NET CLR\\# pokolenia 0**, **pamięć .NET CLR\\# zbierania obiektów pokolenia 1**, i **pamięć .NET CLR\\# zbierania obiektów pokolenia 2** kolumny w celu określenia, jeśli wzorzec alokacje pamięci zarządzanej ma wpływ na stopień odzyskiwania pamięci Kolekcja.  

 W przypadku aplikacji .NET Framework środowisko uruchomieniowe języka wspólnego ogranicza całkowity rozmiar zarządzanej sterty deskryptorów do nieco mniej niż połowa maksymalny rozmiar w prywatnym obszarze części przestrzeni adresowej procesu. Dla procesów 32-bitowych, uruchomione na komputerze 32-bitowym 2 GB reprezentuje górny limit prywatna część przestrzeni adresowej procesu. Całkowity rozmiar sterty zarządzanej po rozpoczęciu jego domyślny limit podejście do, może zwiększyć obciążenie zarządzanie pamięcią i może obniżyć wydajność aplikacji.  

 W przypadku zbyt dużej ilości pamięci zarządzanej obciążenie problemu wziąć pod uwagę jedną z następujących opcji:  

- Optymalizacja użycia aplikacji zasobów pamięci zarządzanej  

   —lub—  

- wykonanie czynności, aby zwolnić architektury ograniczenia dotyczące maksymalnego rozmiaru pamięci wirtualnej dla procesu 32-bitowego  

  Aby zoptymalizować użycie zasobów pamięci zarządzanej aplikacji, zbierać dane alokacji pamięci zarządzanej w alokacji pamięci .NET przebiegu profilowania. Przegląd [widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md) raportów, aby poznać wzorce przydzielania pamięci w aplikacji.  

  Użyj [widok okresu istnienia obiektu](../profiling/object-lifetime-view.md) umożliwia określenie, które uszkodziło danych obiekty są pozostałych do generacji, a następnie odzyskać z tego miejsca.  

  Użyj [Widok alokacji](../profiling/dotnet-memory-allocations-view.md) można ustalić ścieżki wykonywania, które spowodowały tych przydziałów.  

  Aby uzyskać więcej informacji na temat zwiększania wydajności kolekcji wyrzucania elementów, zobacz artykułu technicznego na .NET Framework, [podstawy modułu odśmiecania pamięci i wskazówki dotyczące wydajności](http://go.microsoft.com/fwlink/?LinkId=177946) w witrynie MSDN w sieci Web.  

  Aby uzyskać architektury zwolnienia z ograniczenia pamięci wirtualnej na podstawie rozmiaru części prywatnej przestrzeni adresowej procesu, spróbuj uruchomienie tego procesu 32-bitowego na komputerze 64-bitowym.  32-bitowy proces na komputerze 64-bitowym, mogą uzyskiwać maksymalnie 4 GB pamięci wirtualnej prywatny.  

  64-bitowych proces uruchomiony na komputerze 64-bitowym, mogą uzyskiwać do 8 TB pamięci wirtualnej. Należy wziąć pod uwagę, ponownej kompilacji aplikacji ma działać jako natywnych aplikacji 64-bitowych. Ta reguła jest wyłącznie w celach informacyjnych i może nie wymagać działań korygujących.