---
title: Widok wywołującego/wywoływanego — dane Instrumentacji pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2ac6322f7264f6a6816b6724f0e477c7daa977c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833472"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Widok wywołujący/wywoływany - Instrumentacji pamięci platformy .NET danych
Widok wywołujący/wywoływany profilowania danych, które zostały zebrane przy użyciu metody Instrumentacji pamięci platformy .NET Wyświetla alokacji i danych o chronometrażu dla wybranej funkcji i funkcji nadrzędnymi i podrzędnymi tych wybranych funkcji. Widok wywołujący/wywoływany zawiera trzy siatki.  
  
 **Bieżąca funkcja** są wyświetlane w siatce Środkowej i zawiera informacje na temat wybranej funkcji profilowania pamięci. Wartości obejmują wszystkie próbki wywołania funkcji.  
  
 **Funkcje, które wywołały bieżącą funkcję** są wyświetlane w siatce górnym i przedstawia ilość wartość wybranej funkcji (bieżącego), który został wygenerowany przez wywołania funkcji wywołującego (nadrzędnego).  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** są wyświetlane w siatce dolnej i pokazuje dane dla funkcji elementu wywoływanego (podrzędne) wybranej funkcji profilowania, gdy funkcja podrzędnych została wywołana przez bieżącą funkcję pamięci.  
  
 Kliknij dwukrotnie wywołujący lub wywoływany funkcja wiersz się wiersz bieżącą funkcję.  
  
## <a name="general"></a>Ogólne  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Adres funkcji**|Adres funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Liczba wywołań**|Całkowita liczba wywołań, które zostały wprowadzone do tej funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa, która jest przypisana do procesu.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji ze względu na instrumentacji. Narzut sondy odjęciu z cały czas wyłączny.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych z powodu instrumentacji. Narzut sondy odjęciu z cały czas (włącznie).|  
|**Typ**|Kontekst funkcji:<br /><br /> **0** -bieżącej funkcji<br /><br /> **1** — funkcji wywołującej bieżącą funkcję<br /><br /> **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Nazwa głównej funkcji**|Nazwa bieżącej funkcji. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
  
## <a name="net-memory-allocation-values"></a>Wartości alokacji pamięci .NET  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Przydziały wyłączne**|— W przypadku funkcji bieżącej liczby obiektów, które zostały utworzone podczas wykonywania kodu funkcji w treści funkcji (oznacza to, kiedy funkcja znajdowała się w górnej części stosu wywołań). Liczba nie obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez tę funkcję.<br />— Aby funkcja obiekt wywołujący, liczba przydziałów wyłącznych bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji do obiektu wywołującego.<br />— W przypadku funkcji / / wywoływany liczbę obiektów, które zostały utworzone przez wystąpienia tej funkcji, które zostały wywołane przez bieżącą funkcję. Ta liczba nie obejmuje obiekty, które zostały utworzone przez funkcje, które zostały wywołane przez funkcję / / wywoływany.|  
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone w profilowania, były przydziałów wyłącznych tej funkcji.|  
|**Przydziały włączne**|-Aby uzyskać bieżącą funkcję liczby obiektów przydzielonych za pomocą funkcji podczas uruchomienia profilowania. Liczba obejmuje obiekty, które zostały utworzone w funkcji / / wywoływany, które zostały wywołane przez funkcję.<br />— Aby funkcja obiekt wywołujący, liczba przydziałów włącznych bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji do obiektu wywołującego.<br />— W przypadku funkcji / / wywoływany liczbę obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba uwzględnia alokacji dokonanych przez funkcje, które były wywoływane przez tę funkcję, / / wywoływany.|  
|**% Przydziałów włącznych**|Procent wszystkich obiektów, które zostały utworzone w profilowania, były przydziałów włącznych tej funkcji.|  
|**Bajty wyłączne**|-Aby uzyskać bieżącą funkcję liczbę bajtów pamięci przydzielonych za pomocą funkcji podczas uruchomienia profilowania. Liczba nie obejmuje pamięci, która została przydzielona w funkcjach / / wywoływany, które zostały wywołane przez funkcję.<br />— Aby wywołujący funkcję liczba bajtów wyłącznych bieżącej funkcji, które zostały wygenerowane z wywołań przez tę funkcję do obiektu wywołującego.<br />— W przypadku funkcji / / wywoływany liczba bajtów przydzielonych przez wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba nie obejmuje bajtów przydzielonych przez funkcje, które zostały wywołane przez funkcję / / wywoływany.|  
|**% Bajtów wyłącznych**|Procent wszystkich bajtów pamięci przydzielonych w uruchomienia profilowania były przydziałów wyłącznych tej funkcji.|  
|**Bajty włączne**|-Aby uzyskać bieżącą funkcję liczba bajtów w pamięci, które zostały przydzielone przez funkcję podczas uruchomienia profilowania. Liczba uwzględnia pamięci, która została przydzielona w funkcjach / / wywoływany, które zostały wywołane przez funkcję.<br />– W przypadku funkcji wywołującego liczbę bajtów włącznych wystąpień bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji do obiektu wywołującego.<br />— W przypadku funkcji / / wywoływany liczba bajtów przydzielonych przez wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba uwzględnia bajtów przydzielonych przez funkcje, które były wywoływane przez tę funkcję, / / wywoływany.|  
|**% Bajtów włącznych**|Procent wszystkich bajtów pamięci przydzielonych w uruchomienia profilowania były przydziałów włącznych tej funkcji.|  
  
## <a name="elapsed-inclusive-values"></a>Upłynęło włącznie wartości  
 Upłynęło wartości włącznie wskazują godzinę, będący funkcji na stosie wywołań. Czas obejmuje czas spędzony w funkcji podrzędnych i w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|-Aby uzyskać bieżącą funkcję czas spędzony w funkcji. Wartość zawiera czas spędzony w funkcji podrzędnych i w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.<br />— Aby wywołujący funkcję ilość czasu bieżącej funkcji, który został wygenerowany przez wywołania z tej funkcji obiekt wywołujący, który upłynął (włącznie).<br />— W przypadku funkcji elementu wywoływanego czas spędzony w tej funkcji, który został wygenerowany przez wywołuje z bieżącej funkcji. Wartość zawiera czas spędzony w funkcji podrzędnych i w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.|  
|**% Całkowitego czasu, który upłynął**|Procent sumy, który upłynął całkowity czas uruchomienia profilowania, która tracony jest czas całkowity czas tej funkcji, w tym kontekście.|  
|**Średnia liczba upłynęło włącznie czasu**|Średni całkowity czas wywołania tej funkcji, w tym kontekście, który upłynął.|  
|**Maksymalny czas, który upłynął (włącznie)**|Maksymalny całkowity czas wywołania tej funkcji, w tym kontekście, który upłynął.|  
|**Min upłynęło włącznie czasu**|Minimalny całkowity czas wywołania tej funkcji, w tym kontekście, który upłynął.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wyłączny wartości  
 Czas wyłączny wartości wskazują godzinę, wykonywanej funkcji bezpośrednio w górnej części stosu wywołań. Czas obejmuje czas w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, ale nie obejmuje czas spędzony w funkcjach podrzędnych.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Czas wyłączny, który upłynął**|-Aby uzyskać bieżącą funkcję czas spędzony w trakcie wykonania treści funkcji. Wartość nie obejmuje czasu, która została wydana w funkcjach podrzędnych, ale obejmuje wywołania do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.<br />— Aby funkcja obiekt wywołujący, który upłynął czas wyłączny bieżącej funkcji, który został wygenerowany przez wywołania z tej funkcji do obiektu wywołującego.<br />— W przypadku funkcji elementu wywoływanego czas spędzony w tej funkcji, który został wygenerowany przez wywołuje z bieżącej funkcji. Wartość nie obejmuje czasu, która została wydana w funkcjach podrzędnych funkcji / / wywoływany, ale obejmuje wywołania do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.|  
|**% Wyłącznego czasu, który upłynął**|Łączny czas wyłączny czas tej funkcji, w tym kontekście przeznaczony procent całkowity czas własny czas uruchomienia profilowania.|  
|**Średnia liczba upłynęło wyłącznie czasu**|Średni własny czas wywołania tej funkcji, w tym kontekście, który upłynął.|  
|**Maksymalny czas wyłączny, który upłynął**|Maksymalny własny czas wywołania tej funkcji, w tym kontekście, który upłynął.|  
|**Min upłynęło wyłącznie czasu**|Minimalny własny czas wywołania tej funkcji, w tym kontekście, który upłynął.|  
  
## <a name="application-inclusive-values"></a>Wartości włączne aplikacji  
 Aplikacji wartości włącznie wskazują czasu, która funkcja była w stosie wywołań. Czas nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, ale ma czas spędzony w funkcjach podrzędnych.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|– W przypadku bieżącej funkcji czas spędzony w funkcji i jej funkcji podrzędnych. Wartość nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.<br />— Aby wywołujący funkcję ilość całkowity czas aplikacji bieżącej funkcji, który został wygenerowany przez wywołania z tej funkcji do obiektu wywołującego.<br />— W przypadku funkcji / / wywoływany czas spędzony w taki sposób, w tej funkcji i jej funkcji podrzędnych, który został wygenerowany przez wywołania z bieżącej funkcji. Wartość nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.|  
|**% Całkowitego czasu aplikacji**|Wartość procentowa całkowity czas całkowity czas uruchomienia profilowania był poświęcony w kompletnej aplikacji, całkowity czas tej funkcji, w tym kontekście.|  
|**Średni całkowity czas aplikacji**|Średni całkowity czas aplikacji wywołania tej funkcji, w tym kontekście.|  
|**Maksymalny całkowity czas aplikacji**|Maksymalny całkowity czas aplikacji wywołania tej funkcji, w tym kontekście.|  
|**Minimalny całkowity czas aplikacji**|Minimalny całkowity czas aplikacji wywołania tej funkcji, w tym kontekście.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji  
 Aplikacja wyłączne wartości wskazują czas spędzony w funkcji bez czasu spędzony w funkcjach podrzędnych. Wskazany czas nie obejmuje również czas, jaki był incalls poświęconym systemowi operacyjnemu, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|-Aby uzyskać bieżącą funkcję czas spędzony w trakcie wykonania treści funkcji. Wartość nie obejmuje czas spędzony w funkcji podrzędnej nie obejmuje wywołania do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.<br />— Aby wywołujący funkcję ilość własny czas aplikacji bieżącej funkcji, który został wygenerowany przez wywołania z tej funkcji do obiektu wywołującego.<br />— W przypadku funkcji elementu wywoływanego czas spędzony w tej funkcji, który został wygenerowany przez wywołuje z bieżącej funkcji. Wartość nie obejmuje czas spędzony w funkcji podrzędnych funkcji elementu wywoływanego nie obejmuje wywołania do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.|  
|**% Własnego czasu aplikacji**|Wartość procentowa całkowity czas własny czas uruchomienia profilowania przeznaczony własny czas aplikacji całkowita tej funkcji, w tym kontekście.|  
|**Średni własny czas aplikacji**|Średni własny czas aplikacji wywołania tej funkcji, w tym kontekście.|  
|**Maksymalny własny czas aplikacji**|Maksymalny własny czas aplikacji wywołania tej funkcji, w tym kontekście.|  
|**Minimalny własny czas aplikacji**|Minimalny własny czas aplikacji wywołania tej funkcji, w tym kontekście.|  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok wywołujący/wywoływany - dane próbkowania pamięci platformy .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)   
 [Widok wywołujący/wywoływany - dane próbkowania](../profiling/caller-callee-view-sampling-data.md)