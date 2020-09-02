---
title: Widok modułów — dane próbkowania pamięci platformy .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: abc5f1f6a15271fa3ec530658add2b6ca3027959
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160865"
---
# <a name="modules-view---net-memory-sampling-data"></a>Widok modułów — dane próbkowania pamięci platformy .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok modułów danych przydziału pamięci platformy .NET zbieranych przy użyciu metody próbkowania grupuje dane pamięci według modułów, które zostały wykonane w przebiegu profilowania. Każdy moduł jest katalogiem głównym drzewa hierarchicznego. Funkcje modułu są wymienione pod węzłem modułu.  
  
 Numer wiersza pliku źródłowego instrukcji przynoszących pamięć znajduje się poniżej węzła funkcja, a adresy instrukcji, które wykonują alokację, są wymienione pod węzłem wiersza. Wartości włączne i wyłączne są zawsze takie same dla danych liniowych i danych instrukcji.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa modułu, funkcji, numeru wiersza lub instrukcji.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|  
|**Nazwa procesu**|Nazwa procesu|  
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Przydziały włączne**|-Dla funkcji — całkowita liczba obiektów, które zostały utworzone przez funkcję. Liczba zawiera obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez tę funkcję.<br />-Dla modułu liczba obiektów w przebiegu profilowania, które zostały przydzieloną podczas wykonywania co najmniej jednej funkcji z modułu. Liczba zawiera obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez funkcje modułu.<br />— W przypadku linii lub instrukcji, całkowitej liczby obiektów przydzielonej przez wiersz lub instrukcję.|  
|**% Przydziałów włącznych**|Wartość procentowa wszystkich obiektów przydzielonych w ramach uruchomienia profilowania, która obejmuje przydziały modułu, funkcji, wiersza lub instrukcji.|  
|**Alokacje wyłączne**|— Dla bieżącej funkcji — liczba obiektów, które zostały utworzone, gdy funkcja wykonywała kod treści funkcji (to oznacza, gdy funkcja była w górnej części stosu wywołań). Liczba nie obejmuje obiektów, które zostały utworzone w funkcjach, które zostały wywołane przez tę funkcję.<br />-Dla modułu, suma wyłącznych alokacji funkcji w module.<br />— W przypadku linii lub instrukcji — całkowita liczba obiektów, które zostały utworzone przez ten wiersz lub instrukcję.|  
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały przydzielone w ramach uruchomienia profilowania, które były wyłącznych alokacji modułu, funkcji, wiersza lub instrukcji.|  
|**Bajty włączne**|-Dla funkcji, liczba bajtów, które zostały przydzielone przez funkcję. Liczba zawiera bajty, które zostały przydzielone w funkcjach, które zostały wywołane przez tę funkcję.<br />-Dla modułu liczba bajtów, które zostały przydzieloną w przebiegu profilowania, które zostały przydzieloną podczas wykonywania co najmniej jednej funkcji z modułu. Liczba zawiera obiekty, które zostały utworzone we wszystkich funkcjach, które zostały wywołane przez funkcje modułu.<br />— W przypadku linii lub instrukcji — całkowita liczba obiektów, które zostały utworzone przez wiersz lub instrukcję.|  
|**% Bajtów włącznych**|Procent wszystkich bajtów, które zostały przydzieloną w ramach uruchomienia profilowania, które były włącznie bajtami modułu, funkcji, wiersza lub instrukcji.|  
|**Bajty wyłączne**|-Dla funkcji — całkowita liczba bajtów, które zostały przydzielone przez funkcję. Liczba nie obejmuje bajtów, które zostały przydzielone w funkcjach, które zostały wywołane przez tę funkcję.<br />-Dla modułu, Suma bajtów wyłącznych, które zostały przydzielone przez funkcje w module.<br />— W przypadku linii lub instrukcji, całkowitej liczby obiektów przydzielonej przez ten wiersz lub instrukcję.|  
|**% Bajtów wyłącznych**|Procent wszystkich bajtów, które zostały przydzieloną w ramach uruchomienia profilowania, które były wyłącznych bajtów modułu, funkcji, wiersza lub instrukcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok modułów-Instrumentacja](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Widok modułów](../profiling/modules-view-sampling-data.md)   
 [Widok modułów](../profiling/modules-view-instrumentation-data.md)
