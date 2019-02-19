---
title: Widok modułów — dane próbkowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 04c714576a0207d4168f20a241d6f0c7dd29298c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54784460"
---
# <a name="modules-view---sampling-data"></a>Widok modułów — dane próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok modułów próbkuje dane wydajności wyświetla dane, które są pogrupowane według modułów, które zostały poddane próbkowaniu w danych profilowania. Każdy moduł jest katalogiem głównym drzewa hierarchicznego. Próbkowane funkcji modułu są wyświetlane poniżej tego węzła modułu.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Jeśli wykonywania funkcji podczas próbek (oznacza to, że funkcja znajdowała się w górnej części stosu wywołań), wiersze źródłowe i adresy instrukcji, które wykonywały są wymienione poniżej tego węzła funkcji. Ponieważ dane są zbierane dla wiersza źródłowego lub wskaźnika instrukcji, podczas wykonywania wiersza lub instrukcji, wartości włączne i wyłączne są zawsze takie same dla wiersza danych i danych instrukcji.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa modułu, funkcji, numer wiersza lub adres wskaźnika instrukcji.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera wskaźnik funkcji, wiersza lub instrukcji.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera wskaźnik modułu, funkcji, wiersza lub instrukcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Próbki włączne**|— Dla funkcji liczba próbek, w których ta funkcja lub funkcja, która została wywołana przez tę funkcję wykonywania; oznacza to, że liczba wywołań stosu przykładów, które zawiera tę funkcję.<br />— Dla modułu liczba próbek w funkcji co najmniej jeden z modułu wykonywania.<br />— W przypadku wiersza lub instrukcji, liczba próbek w którym ten wiersz lub instrukcja powodowała.|  
|**% Włącznych próbek**|-Funkcji lub modułu, wartość procentowa wszystkie przykłady w uruchomienia profilowania były włącznych próbek w tej funkcji lub modułu.<br />— Dla wiersza lub instrukcji procent wszystkie przykłady w profilowania są uruchamiane w którym ten wiersz lub instrukcja powodowała.|  
|**Próbki wyłączne**|— Dla funkcji liczba wywołań stosu przykładów, w których ta funkcja był wykonywany bezpośrednio; oznacza to, liczba próbek, w których ta funkcja była w górnej części stosu wywołań.<br />— Dla modułu, sumę wyłącznych próbek funkcje w module.<br />— W przypadku wiersza lub instrukcji, liczba próbek w którym ten wiersz lub instrukcja powodowała.|  
|**% Wyłącznych próbek**|-Funkcji lub modułu, wartość procentowa wszystkie przykłady w uruchomienia profilowania były wyłącznych próbek w tej funkcji lub modułu.<br />— Dla wiersza lub instrukcji procent wszystkie przykłady w profilowania są uruchamiane w którym ten wiersz lub instrukcja powodowała.|  
  
## <a name="see-also"></a>Zobacz też  
 [Moduły View - próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Widok modułów - Instrumentacja](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Widok modułów](../profiling/modules-view-instrumentation-data.md)
