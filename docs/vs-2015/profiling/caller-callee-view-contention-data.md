---
title: Widok wywołujący-wywoływany — dane rywalizacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f60e8eedeeb7106a7a95a33a4a5cc794194861c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164565"
---
# <a name="caller--callee-view----contention-data"></a>Widok wywołujący/wywoływany-dane rywalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok wywołujący/wywoływany wyświetla informacje o rywalizacji dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki.  
  
 **Bieżąca funkcja** jest wyświetlana w środkowej siatce i zawiera informacje o rywalizacji o zawartość wybranej funkcji. Wartości obejmują wszystkie blokowanie rywalizacji dla funkcji.  
  
 **Funkcje, które wywołały bieżącą funkcję** , są wyświetlane w górnej siatce i pokazują indywidualne udziały funkcji wywołujących (nadrzędnych) do wartości wybranej (bieżącej) funkcji.  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** , są wyświetlane w dolnej siatce i pokazują informacje o rywalizacji o zawartość dla funkcji wywoływanych (podrzędnych) wybranej funkcji, gdy funkcja podrzędna została wywołana przez bieżącą funkcję.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Typ**|Kontekst funkcji:<br /><br /> -   **0** — bieżąca funkcja<br />-   **1** — funkcja, która wywołuje bieżącą funkcję<br />-   **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|  
|**Wyłączny czas blokowania**|— Dla bieżącej funkcji godzina, o której zablokowano wykonywanie kodu w treści funkcji. Czas blokowania w funkcjach wywoływanych przez funkcję nie jest uwzględniany.<br />-Dla funkcji wywołującej część wyłącznego czasu blokowania bieżącej funkcji, która wystąpiła, gdy ta funkcja nazywa bieżącą funkcję.<br />-Dla funkcji wywoływanej, czas, przez który ta funkcja została zablokowana do wykonywania własnego kodu, gdy ta funkcja została wywołana przez bieżącą funkcję. Czas blokowania w funkcjach podrzędnych wywoływanych przez wywoływaną funkcję nie jest uwzględniany.|  
|**% Wyłącznego czasu blokowania**|Procent całego zablokowanego czasu w przebiegu profilowania, który miał wyłączny czas zablokowany dla tej funkcji w tym kontekście.|  
|**Rywalizacje wyłączne**|— Dla bieżącej funkcji, ile razy ta funkcja została zablokowana z wykonywania kodu w treści funkcji. Rywalizacje, które wystąpiły w funkcjach, które zostały wywołane przez funkcję, nie są uwzględniane.<br />-Dla funkcji wywołującej liczba wyłącznych rywalizacji o bieżącą funkcję, która wystąpiła, gdy ta funkcja nazywa bieżącą funkcję.<br />-Dla funkcji wywoływanej, ile razy ta funkcja została zablokowana z wykonywania kodu w treści funkcji, gdy ta funkcja została wywołana przez bieżącą funkcję. Rywalizacje, które wystąpiły w funkcjach wywoływanych przez wywoływaną funkcję, nie są uwzględniane.|  
|**Zawartość wyłącznych%**|Procent wszystkich rywalizacji w przebiegu profilowania, który miał wykluczające się rywalizacje dla tej funkcji w tym kontekście.|  
|**Adres funkcji**|Adres lub token funkcji.|  
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|  
|**Włączny czas blokowania**|— Dla bieżącej funkcji, czas blokowania wykonywania tej funkcji lub jednej z funkcji, które zostały wywołane przez tę funkcję. Uwzględniono zablokowany czas w funkcjach, które zostały wywołane przez bieżącą funkcję.<br />— Dla funkcji wywołującej część zablokowego czasu blokowania bieżącej funkcji, która wystąpiła, gdy ta funkcja nazywa bieżącą funkcję.<br />-Dla funkcji wywoływanej, czas, przez który ta funkcja lub jedna z funkcji, która została wywołana przez funkcję, została zablokowana z wykonywania, gdy ta funkcja została wywołana przez bieżącą funkcję. Uwzględniono zablokowany czas w funkcjach, które zostały wywołane przez wywoływaną funkcję.|  
|**% Włącznego czasu blokowania**|Procent całego zablokowanego czasu w przebiegu profilowania, który był w tym kontekście przeznaczony do blokowania czasu dla tej funkcji.|  
|**Rywalizacje włączne**|— Dla bieżącej funkcji, ile razy ta funkcja lub jedna z funkcji, które zostały wywołane przez funkcję, została zablokowana z wykonywania. Uwzględniono rywalizacje, które wystąpiły w funkcjach, które zostały wywołane przez funkcję.<br />-Dla funkcji wywołującej liczba rywalizacji włącznie z bieżącą funkcją, która wystąpiła, gdy ta funkcja nazywa bieżącą funkcję.<br />— Dla funkcji wywoływanej, ile razy ta funkcja lub jedna z funkcji, które zostały wywołane przez funkcję, została zablokowana z wykonywania, gdy ta funkcja została wywołana przez bieżącą funkcję. Są uwzględniane rywalizacje, które wystąpiły w funkcjach wywoływanych przez wywoływaną funkcję.|  
|**% Rywalizacji włącznych**|Procent wszystkich rywalizacji w przebiegu profilowania, który miał wykluczające się rywalizacje dla tej funkcji w tym kontekście.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym wystąpiły rywalizacje.|  
|**Nazwa procesu**|Nazwa procesu|  
|**Nazwa funkcji głównej**|Nazwa bieżącej funkcji. Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok wywołujący/wywoływany](../profiling/caller-callee-view.md)   
 [Widok wywołujący/wywoływany-Dane próbkowania](../profiling/caller-callee-view-sampling-data.md)   
 [Widok wywołujący/wywoływany-Dane instrumentacji pamięci sieciowej](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Widok wywołujący/wywoływany — Dane próbkowania pamięci platformy .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Widok wywołujący/wywoływany-Dane instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)
