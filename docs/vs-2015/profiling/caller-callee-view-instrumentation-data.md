---
title: Widok wywołujący-wywoływany-Dane instrumentacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c8db1d559682ccb0f202d100fac6a586d3477cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147919"
---
# <a name="callercallee-view---instrumentation-data"></a>Widok wywołujący/wywoływany-Dane instrumentacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok wywołujący/wywoływany wyświetla informacje profilowania dotyczące wybranej funkcji i jej funkcji nadrzędnych i podrzędnych w drzewie wywołań. Widok wywołujący/wywoływany zawiera trzy siatki.  
  
 **Bieżąca funkcja** jest wyświetlana w środkowej siatce i zawiera informacje profilowania dotyczące wybranej funkcji. Wartości obejmują wszystkie wywołania funkcji.  
  
 **Funkcje, które wywołały bieżącą funkcję** , są wyświetlane w górnej siatce i pokazują informacje profilowania dotyczące funkcji obiektu wywołującego (nadrzędnego) wybranej funkcji. Wartości wskazują ilość bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującej.  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** , są wyświetlane w dolnej siatce i pokazują informacje profilowania dotyczące wystąpień wywoływanych (podrzędnych) funkcji wybranej funkcji. Wartości wskazują tylko czas spędzony w funkcji podrzędnej, gdy została wywołana przez bieżącą funkcję.  
  
## <a name="general"></a>Ogólne  
 Kolumny ogólne identyfikują funkcję w wierszu widoku.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Adres funkcji**|Adres funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Liczba połączeń**|Całkowita liczba wywołań wykonanych dla tej funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|  
|**Nazwa procesu**|Nazwa procesu|  
|**Obciążenie sondy czasu wyłącznego**|Narzut czasu dla tej funkcji, który został spowodowany przez instrumentację. Narzuty sondowania zostały odjęte od wszystkich wyłączeń.|  
|**Narzut sondy czasu włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych, która została spowodowana przez instrumentację. Narzuty sondowania zostały odjęte od wszystkich czasów włączania.|  
|**Typ**|Kontekst funkcji:<br /><br /> **0** — bieżąca funkcja<br /><br /> **1** — funkcja, która wywołuje bieżącą funkcję<br /><br /> **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|  
|**Nazwa funkcji głównej**|Nazwa bieżącej funkcji. Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|  
  
## <a name="elapsed-inclusive-values"></a>Wartości włączne, które upłynęły  
 Wartości włączne (włącznie) wskazują czas, przez który funkcja była w stosie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych i czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Czas włączny, który upłynął**|— Dla bieżącej funkcji, czas spędzony w funkcji. Wartość obejmuje czas spędzony w funkcjach podrzędnych i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującej, ilość czasu włącznego dla bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującej.<br />-Dla funkcji wywoływanej, czas spędzony w wystąpieniach tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość obejmuje czas spędzony w funkcjach podrzędnych elementu wywoływanego i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.|  
|**% Czasu włącznego, który upłynął**|Procent łącznego czasu trwania przebiegu profilowania, który był spędzony w czasie trwania tej funkcji w tym kontekście.|  
|**Średni łączny czas, który upłynął**|Średni czas włączny, który upłynął w tym kontekście w przypadku wywołania tej funkcji.|  
|**Maksymalny łączny czas, który upłynął**|Maksymalny łączny czas, który upłynął w przypadku wywołania tej funkcji w tym kontekście.|  
|**Minimalny łączny czas, który upłynął**|Minimalny łączny czas, który upłynął w przypadku wywołania tej funkcji w tym kontekście.|  
  
## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęły  
 Wartości wyłączne, które upłynęły, wskazują czas, przez który funkcja została bezpośrednio uruchomiona w górnej części stosu wywołań. Czas obejmuje czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach podrzędnych.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Czas wyłączny, który upłynął**|— Dla bieżącej funkcji czas spędzony w bezpośrednim wykonywaniu funkcji. Wartość obejmuje czas spędzony w funkcjach podrzędnych i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującej, ilość czasu wyłącznego bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującej.<br />-Dla funkcji wywoływanej, czas spędzony w wystąpieniach tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość wyklucza czas spędzony w funkcjach podrzędnych funkcji wywoływanej, ale obejmuje wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.|  
|**% Czasu wyłącznego, który upłynął**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania w łącznym czasie trwania tej funkcji w tym kontekście.|  
|**Średni czas wyłączny, który upłynął**|Średni czas wyłączny dla wywołania tej funkcji w tym kontekście.|  
|**Maksymalny czas wyłączny, który upłynął**|Maksymalny czas wyłączny w wywołaniu tej funkcji w tym kontekście.|  
|**Minimalny czas, który upłynął**|Minimalny czas, który upłynął w przypadku wywołania tej funkcji w tym kontekście.|  
  
## <a name="application-inclusive-values"></a>Wartości włączne aplikacji  
 Wartości włącznie obejmują czas, przez który funkcja była w stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, ale obejmuje czas spędzony w funkcjach podrzędnych.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Czas włączny aplikacji**|— Dla bieżącej funkcji, czas spędzony w funkcji i jej funkcjach podrzędnych. Wartość wyklucza czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.<br />-Dla funkcji wywołującej, ilość łącznego czasu aplikacji wygenerowanej przez wywołania z tej funkcji wywołującej.<br />-Dla funkcji wywoływanej, czas spędzony w wystąpieniach tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość obejmuje czas spędzony w funkcjach podrzędnych funkcji wywoływanej, ale nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.|  
|**% Włącznego czasu aplikacji**|Wartość procentowa łącznego czasu trwania przebiegu profilowania, która została wykorzystana w łącznym czasie włącznie aplikacji w tym kontekście.|  
|**Średni czas włączny aplikacji**|Średni czas włączny aplikacji wywołania tej funkcji w tym kontekście.|  
|**Maksymalny czas włączny aplikacji**|Maksymalny czas włączny aplikacji wywołania tej funkcji w tym kontekście.|  
|**Minimalny czas włączny aplikacji**|Minimalny czas włączny aplikacji w tym kontekście w przypadku wywołania tej funkcji.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji  
 Wartości wyłączne aplikacji wskazują czas spędzony w funkcji. Wyklucza to czas spędzony w funkcjach podrzędnych, a także wyklucza wywołania systemu operacyjnego, takie jak operacje przełączania kontekstu i operacji wejścia/wyjścia.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Czas wyłączny aplikacji**|— Dla bieżącej funkcji czas spędzony w bezpośrednim wykonywaniu funkcji. Wartość nie obejmuje czasu spędzonego w funkcjach podrzędnych ani nie obejmuje wywołań do systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującej, ilość czasu wyłącznego aplikacji dla bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującej.<br />-Dla funkcji wywoływanej, czas spędzony w wystąpieniach tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość nie obejmuje czasu spędzonego w funkcjach podrzędnych funkcji wywoływanej ani nie obejmuje wywołań do systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.|  
|**% Wyłącznego czasu aplikacji**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania, który został spędzony w łącznym czasie trwania tej funkcji aplikacji w tym kontekście.|  
|**Średni czas wyłączny aplikacji**|Średni czas wyłączny aplikacji wywołania tej funkcji w tym kontekście.|  
|**Maksymalny czas wyłączny aplikacji**|Maksymalny czas wyłączny aplikacji wywołania tej funkcji w tym kontekście.|  
|**Minimalny czas wyłączny aplikacji**|Minimalny czas wyłączny aplikacji w wywołaniu tej funkcji w tym kontekście.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok wywołujący/wywoływany-Dane próbkowania](../profiling/caller-callee-view-sampling-data.md)   
 [Widok wywołujący/wywoływany — Dane próbkowania pamięci platformy .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Widok wywołujący/wywoływany-Dane instrumentacji pamięci sieciowej](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
