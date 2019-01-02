---
title: Widok modułów — dane rywalizacji o zasoby | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: edd882b00c5bdaf62ae280cb0e4986662b05ad83
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926402"
---
# <a name="modules-view---contention-data"></a>Widok modułów — dane rywalizacji
Widok modułów danych rywalizacji o zasoby współbieżności dane są pogrupowane według modułów, które zostały poddane próbkowaniu w danych profilowania. Każdy moduł jest katalogiem głównym drzewa hierarchicznego. Funkcji modułu, w którym wystąpiło zdarzenia rywalizacji są wyświetlane w węźle modułu.  
  
 W przypadku wykonywania funkcji swój własny kod po wystąpieniu zdarzenia rywalizacji o zasoby, oznacza to, że funkcja znajdowała się w górnej części stosu wywołań, wiersze kodu i instrukcji, że adresy, które wykonywały są wyświetlane w węźle funkcji. Ponieważ dane są zbierane dla wiersza źródłowego lub wskaźnika instrukcji, podczas wykonywania wiersza lub instrukcji, wartości włączne i wyłączne są zawsze takie same dla wiersza danych i danych instrukcji.  
  
 W poniższej tabeli opisano wartości kolumn w widoku modułów danych rywalizacji o zasoby.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Wyłączny czas blokowania**|— Dla funkcji, czas, jaki ta funkcja została zablokowana z wykonywania kodu w treści funkcji. Czas blokowania w funkcjach, które zostały wywołane przez funkcję nie jest włączony.<br />— Dla modułu, sumę wyłączny czas blokowania funkcje w module.<br />— W przypadku wiersza lub instrukcję, czas, że wiersz lub został zablokowany wykonywania instrukcji.|  
|**% Własnego czasu blokowania**|-Funkcji lub modułu procent wszystkich czas blokowania w profilowania, była wyłączny czas blokowania w tej funkcji lub modułu.<br />— W przypadku wiersza lub instrukcję, procent wszystkich czas blokowania podczas uruchomienia profilowania, w którym ten wiersz lub instrukcji zablokowano wykonywania.|  
|**Rywalizacje wyłączne**|— Dla funkcji, ile razy ta funkcja została zablokowana z wykonywania kodu w treści funkcji. Rywalizacje w funkcjach, które zostały wywołane przez funkcję nie są uwzględniane.<br />— Dla modułu, sumę rywalizacji wyłącznych funkcje w module.<br />— W przypadku wiersza lub instrukcję, ile razy ten wiersz lub instrukcji zostało zablokowane z wykonywania.|  
|**% Rywalizacji wyłącznych**|-Funkcji lub modułu procent wszystkie rywalizacje w uruchomienia profilowania były rywalizacji wyłącznych tej funkcji lub modułu.<br />-Linię lub instrukcję procent wszystkie rywalizacje w uruchomienia profilowania były rywalizacji, które blokowane tego wiersza lub instrukcji wykonywanie.|  
|**Całkowity czas blokowania**|— W przypadku funkcji czasu, która tej funkcji lub funkcji, która została wywołana przez tę funkcję, została zablokowana wykonania.<br />— Dla modułu suma czasu blokowania, w których co najmniej jedną funkcję z tego modułu znajdowała się na stosie.<br />— W przypadku wiersza lub instrukcję, czas, że wiersz lub został zablokowany wykonywania instrukcji.|  
|**% Całkowitego czasu blokowania**|-Funkcji lub modułu procent wszystkich czas blokowania w profilowania, była całkowity czas blokowania w tej funkcji lub modułu.<br />— W przypadku wiersza lub instrukcję procent wszystkich czas blokowania w profilowania są uruchamiane w którym ten wiersz lub instrukcja powodowała.|  
|**Rywalizacje włączne**|— Dla funkcji, ile razy ta funkcja lub funkcja, która została wywołana przez tę funkcję zablokowano wykonywania.<br />— Dla modułu liczba rywalizacji, w których co najmniej jedną funkcję z tego modułu znajdowała się na stosie.<br />— W przypadku wiersza lub instrukcję, ile razy ten wiersz lub instrukcji zostało zablokowane z wykonywania.|  
|**% Rywalizacji włącznych**|-Funkcji lub modułu procent wszystkie rywalizacje w uruchomienia profilowania były rywalizacji włącznych tej funkcji lub modułu.<br />— W przypadku wiersza lub instrukcję procent wszystkich czas blokowania w profilowania są uruchamiane w którym ten wiersz lub instrukcja powodowała.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera wskaźnik funkcji, wiersza lub instrukcji.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera wskaźnik modułu, funkcji, wiersza lub instrukcji.|  
|**Nazwa**|Nazwa modułu lub funkcji.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok modułów](../profiling/modules-view.md)   
 [Widok modułów - Instrumentacja](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Moduły View - próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Widok modułów](../profiling/modules-view-instrumentation-data.md)   
 [Widok modułów](../profiling/modules-view-sampling-data.md)