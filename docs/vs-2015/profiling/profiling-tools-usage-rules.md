---
title: Reguły użycia narzędzia profilowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4158a6a393ed6e64dedddfca10c1ae04a95e3d3a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535554"
---
# <a name="profiling-tools-usage-rules"></a>Reguły korzystania z narzędzi profilowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Reguły wydajności w kategorii użycie narzędzia profilowania zawierają wskazówki dotyczące najbardziej efektywnego zbierania danych przy użyciu programu Profiler.  
  
|Reguła|Opis|  
|-|-|  
|[DA0002: Brak biblioteki VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|Profilowanie wiersza polecenia może zawierać niekompletne dane dla [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] plików binarnych. Może to być spowodowane nieustawieniem poprawnych zmiennych środowiskowych.|  
|[DA0003: Wiele przykładów jądra](../profiling/da0003-many-kernel-samples.md)|Zarejestrowano wiele przykładów profilowania, które wystąpiły poza wykonywaniem docelowej wartości binarnej. Aby zebrać dokładniejsze dane, rozważ użycie metody instrumentacji.|  
|[DA0004: Znaczące użycie procesora](../profiling/da0004-high-processor-usage.md)|Profilowanie danych sugeruje, że procesory były stale zajęte podczas przebiegu profilowania. Aby zebrać dokładniejsze dane, rozważ użycie metody próbkowania.|  
|[DA0008: Zebrano kilka próbek](../profiling/da0008-few-samples-collected.md)|Liczba próbek zebranych w przebiegu profilowania była zbyt duża, aby była statystycznie znacząca. Rozważ ponowne utworzenie profilu i uruchomienie aplikacji przez dłuższy czas. Możesz również rozważyć użycie metody instrumentacji do zbierania danych.|  
|[DA0026: Nadmierne zużycie czasu procesora w trybie jądra](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|W trybie jądra procesora wystąpił znaczący czas w przebiegu profilowania. Należy rozważyć próbkowanie przy użyciu wywołań systemowych jako metryki zamiast czasu użycia jako metryki.|  
|[DA0029: Nieobsługiwana wersja środowiska CLR](../profiling/da0029-unsupported-clr-version.md)|Profilowany plik binarny używa wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , która nie jest obsługiwana przez profiler. Raporty profilera nie mogą rozpoznać nazw symboli.|  
|[DA0030: Zbierz miary interakcji warstw dla projektów bazy danych](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Zebrano znaczną liczbę wywołań metod w <xref:System.Data?displayProperty=fullName> przestrzeni nazw. Aby uwzględnić dane dotyczące wywołań bazy danych, należy rozważyć zbieranie danych o interakcji między warstwami w profilu.|
