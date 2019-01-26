---
title: Widok wywołującego/wywoływanego — dane Instrumentacji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c1970c8a026e509cb31a9a58a0ae42777425bef
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945284"
---
# <a name="callercallee-view---instrumentation-data"></a>Widok wywołujący/wywoływany - dane Instrumentacji
Widok wywołujący/wywoływany Wyświetla profilowania informacji na temat wybranej funkcji i jej funkcji nadrzędnymi i podrzędnymi w drzewie wywołań. Widok wywołujący/wywoływany zawiera trzy siatki.  
  
 **Bieżąca funkcja** jest wyświetlany w środkowy siatkę, a pokazuje profilowania informacji na temat wybranej funkcji. Wartości obejmują wszystkie wywołania do funkcji.  
  
 **Funkcje, które wywołały bieżącą funkcję** jest wyświetlana w górnej siatki i pokazuje profilowania informacje na temat funkcji wywołującego (nadrzędnego) wybranej funkcji. Wartości wskazują ilość wartości bieżącej funkcji, który został wygenerowany przez wywołania z tej funkcji do obiektu wywołującego.  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w siatce dolnej i pokazuje profilowania informacje o wystąpieniach funkcji wywoływanych (podrzędne) wybranej funkcji. Wartości wskazuje czas spędzony w funkcji podrzędnych wywołanego przez bieżącą funkcję.  
  
## <a name="general"></a>Ogólne  
 Ogólne kolumn identyfikować ich funkcję w wierszu widoku.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Adres funkcji**|Adres funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Liczba wywołań**|Całkowita liczba wywołań wykonanych dla tej funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji, które zostało spowodowane przez Instrumentację. Narzut sondy odjęciu z cały czas wyłączny.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych, które zostało spowodowane przez Instrumentację. Narzut sondy odjęciu z cały czas (włącznie).|  
|**Typ**|Kontekst funkcji:<br /><br /> **0** -bieżącej funkcji<br /><br /> **1** — funkcji wywołującej bieżącą funkcję<br /><br /> **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Nazwa głównej funkcji**|Nazwa bieżącej funkcji. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
  
## <a name="elapsed-inclusive-values"></a>Upłynęło włącznie wartości  
 Upłynęło wartości włącznie wskazują godzinę, będący funkcji na stosie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych i czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|-Aby uzyskać bieżącą funkcję czas spędzony w funkcji. Wartość zawiera czas spędzony w funkcji podrzędnych i w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.<br />— Aby wywołujący funkcję ilość czasu bieżącej funkcji, który został wygenerowany przez wywołania z tej funkcji obiekt wywołujący, który upłynął (włącznie).<br />— W przypadku funkcji / / wywoływany czas spędzony w wystąpieniach tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość zawiera czas spędzony w funkcji podrzędne o obiekcie wywoływanym i w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.|  
|**% Całkowitego czasu, który upłynął**|Procent sumy, który upłynął całkowity czas uruchomienia profilowania, która tracony jest czas całkowity czas tej funkcji, w tym kontekście.|  
|**Średnia liczba upłynęło włącznie czasu**|Średni całkowity czas wywołania tej funkcji, w tym kontekście, który upłynął.|  
|**Maksymalny czas, który upłynął (włącznie)**|Maksymalny całkowity czas wywołania tej funkcji, w tym kontekście, który upłynął.|  
|**Min upłynęło włącznie czasu**|Minimalny całkowity czas wywołania tej funkcji, w tym kontekście, który upłynął.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wyłączny wartości  
 Czas wyłączny wartości wskazują godzinę, wykonywanej funkcji bezpośrednio w górnej części stosu wywołań. Czas obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, ale nie obejmuje czas spędzony w funkcjach podrzędnych.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Czas wyłączny, który upłynął**|— Aby uzyskać bieżącą funkcję czas spędzony w bezpośrednie wykonywanie funkcji. Wartość zawiera czas spędzony w funkcji podrzędnych i w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.<br />— Aby funkcja obiekt wywołujący, który upłynął czas wyłączny bieżącej funkcji, który został wygenerowany przez wywołania z tej funkcji do obiektu wywołującego.<br />— W przypadku funkcji / / wywoływany czas spędzony w wystąpieniach tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość nie obejmuje czas spędzony w funkcjach podrzędnych funkcji / / wywoływany, ale obejmuje wywołania do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.|  
|**% Wyłącznego czasu, który upłynął**|Łączny czas wyłączny czas tej funkcji, w tym kontekście przeznaczony procent całkowity czas własny czas uruchomienia profilowania.|  
|**Średnia liczba upłynęło wyłącznie czasu**|Średni własny czas wywołania tej funkcji, w tym kontekście, który upłynął.|  
|**Maksymalny czas wyłączny, który upłynął**|Maksymalny własny czas wywołania tej funkcji, w tym kontekście, który upłynął.|  
|**Min upłynęło wyłącznie czasu**|Minimalny własny czas wywołania tej funkcji, w tym kontekście, który upłynął.|  
  
## <a name="application-inclusive-values"></a>Wartości włączne aplikacji  
 Aplikacji wartości włącznie wskazują czasu, która funkcja była w stosie wywołań. Czas nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, ale ma czas spędzony w funkcjach podrzędnych.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|– W przypadku bieżącej funkcji czas spędzony w funkcji i jej funkcji podrzędnych. Wartość nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.<br />— Aby wywołujący funkcję ilość całkowity czas aplikacji bieżącej funkcji, który został wygenerowany przez wywołania z tej funkcji do obiektu wywołującego.<br />— W przypadku funkcji / / wywoływany czas spędzony w wystąpieniach tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość zawiera czas spędzony w funkcji podrzędnych funkcji / / wywoływany, ale nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.|  
|**% Całkowitego czasu aplikacji**|Wartość procentowa całkowity czas całkowity czas uruchomienia profilowania był poświęcony w kompletnej aplikacji, całkowity czas tej funkcji, w tym kontekście.|  
|**Średni całkowity czas aplikacji**|Średni całkowity czas aplikacji wywołania tej funkcji, w tym kontekście.|  
|**Maksymalny całkowity czas aplikacji**|Maksymalny całkowity czas aplikacji wywołania tej funkcji, w tym kontekście.|  
|**Minimalny całkowity czas aplikacji**|Minimalny całkowity czas aplikacji wywołania tej funkcji, w tym kontekście.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji  
 Aplikacja wyłączne wartości wskazują czas spędzony w funkcji. Nie obejmuje to czas, jaki był poświęcony funkcji podrzędnej, a także wyklucza wywołań do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|— Aby uzyskać bieżącą funkcję czas spędzony w bezpośrednie wykonywanie funkcji. Wartość nie obejmuje czas spędzony w funkcji podrzędnej nie obejmuje wywołania do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.<br />— Aby wywołujący funkcję ilość własny czas aplikacji bieżącej funkcji, który został wygenerowany przez wywołania z tej funkcji do obiektu wywołującego.<br />— W przypadku funkcji / / wywoływany czas spędzony w wystąpieniach tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość nie obejmuje czas spędzony w funkcji podrzędnych funkcji elementu wywoływanego nie obejmuje wywołania do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.|  
|**% Własnego czasu aplikacji**|Wartość procentowa całkowity czas własny czas uruchomienia profilowania przeznaczony własny czas aplikacji całkowita tej funkcji, w tym kontekście.|  
|**Średni własny czas aplikacji**|Średni własny czas aplikacji wywołania tej funkcji, w tym kontekście.|  
|**Maksymalny własny czas aplikacji**|Maksymalny własny czas aplikacji wywołania tej funkcji, w tym kontekście.|  
|**Minimalny własny czas aplikacji**|Minimalny własny czas aplikacji wywołania tej funkcji, w tym kontekście.|  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok wywołujący/wywoływany - dane próbkowania](../profiling/caller-callee-view-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane próbkowania pamięci platformy .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji pamięci platformy .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)