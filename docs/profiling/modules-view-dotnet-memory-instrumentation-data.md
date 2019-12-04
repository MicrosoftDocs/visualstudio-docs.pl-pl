---
title: Widok modułów — dane Instrumentacji pamięci platformy .NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 521c884a0a25d7fa975a4039e6ec3e36ff4dc020
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778547"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Widok modułów — dane Instrumentacji pamięci platformy .NET
Widok modułów danych przydziału pamięci platformy .NET zbieranych przy użyciu metody instrumentacji grupuje dane dotyczące pamięci i chronometrażu przez moduły, które zostały wykonane w przebiegu profilowania. Dane profilowania dla funkcji modułu są wymienione pod węzłem modułu.

## <a name="general"></a>Ogólne

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa funkcji lub modułu.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Liczba wywołań**|Całkowita liczba wywołań wykonanych dla tej funkcji lub modułu.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję tej funkcji.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu, w którym uruchomiono moduł lub funkcję.|
|**Obciążenie sondy czasu wyłącznego**|Narzut czasu dla tej funkcji lub modułu ze względu na instrumentację.|
|**Narzut sondy czasu włącznego**|Narzut czasu dla tej funkcji lub modułu oraz jej funkcji podrzędnych z powodu Instrumentacji.|

## <a name="net-memory-values"></a>Wartości pamięci platformy .NET
 Wartości pamięci platformy .NET włącznie funkcji wskazują liczbę (alokacje) i rozmiar (w bajtach) obiektów, które zostały utworzone przez funkcję i jej funkcje podrzędne.

 Wartości pamięci wyłącznej wskazują liczbę i rozmiar obiektów, które zostały utworzone przez funkcję, a nie przez jej funkcje podrzędne.

 Wartości włączne i wyłączne pamięci modułu są sumą wartości pamięci włącznej i wyłącznej funkcji w module.

|Kolumna|Opis|
|------------|-----------------|
|**Przydziały włączne**|-Dla funkcji — całkowita liczba obiektów, które zostały utworzone przez funkcję. Ta liczba obejmuje obiekty, które zostały utworzone przez funkcje, które zostały wywołane przez funkcję.<br />-Dla modułu liczba obiektów w uruchomieniu profilowania, które zostały przydzieloną podczas wykonywania co najmniej jednej funkcji z modułu. Ta liczba obejmuje obiekty, które zostały przydzielone w funkcjach, które zostały wygenerowane przez wywołania z funkcji modułu.|
|**% Przydziałów włącznych**|Wartość procentowa wszystkich obiektów przydzielonych w ramach uruchomienia profilowania, które były przydzielone do modułu lub funkcji.|
|**Alokacje wyłączne**|-Dla funkcji, liczba obiektów, które zostały utworzone, gdy funkcja wykonywała kod w treści funkcji (to oznacza, gdy funkcja była w górnej części stosu wywołań). Ta liczba nie obejmuje obiektów, które zostały utworzone w funkcjach, które zostały wywołane przez funkcję.<br />-Dla modułu, suma wyłącznych alokacji funkcji w module.|
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały przydzielone w ramach uruchomienia profilowania, które były wyłącznych alokacji modułu lub funkcji.|
|**Bajty wyłączne**|-Dla funkcji — całkowita liczba bajtów pamięci, które zostały przydzieloną, gdy funkcja wykonywała kod w treści funkcji (to znaczy, gdy funkcja była w górnej części stosu wywołań). Ta liczba nie obejmuje bajtów, które zostały przydzielone w funkcjach, które zostały wywołane przez funkcję.<br />-Dla modułu, Suma bajtów wyłącznych, które zostały przydzielone przez funkcje w module.|
|**% Bajtów wyłącznych**|Procent wszystkich bajtów, które zostały przydzieloną w ramach uruchomienia profilowania, które były wyłącznych bajtów modułu, funkcji, wiersza lub instrukcji.|
|**Bajty włączne**|-Dla funkcji, liczba bajtów, które zostały przydzielone przez funkcję. Ta liczba obejmuje bajty, które zostały przydzielone w funkcjach, które zostały wywołane przez funkcję.<br />-Dla modułu liczba bajtów, które zostały przydzieloną w przebiegu profilowania, które zostały przydzieloną podczas wykonywania co najmniej jednej funkcji z modułu. Ta liczba obejmuje obiekty, które zostały utworzone we wszystkich funkcjach, które zostały wywołane przez funkcje modułu.|
|**% Bajtów włącznych**|Procent wszystkich bajtów, które zostały przydzieloną w ramach uruchomienia profilowania, które były włącznie bajtami modułu lub funkcji.|

## <a name="elapsed-inclusive-values"></a>Wartości włączne, które upłynęły
 Wartości włączne (włącznie) wskazują czas, przez który funkcja była w stosie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny, który upłynął**|-Dla funkcji, czas spędzony w funkcji. Obejmuje to czas spędzony w funkcjach podrzędnych i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.<br />-Dla modułu, okres czasu, w którym co najmniej jedna funkcja w module znajdowała się na stosie wywołań.|
|**% Czasu włącznego, który upłynął**|Wartość procentowa łącznego czasu trwania przebiegu profilowania w łącznym czasie trwania tego modułu lub funkcji.|
|**Średni łączny czas, który upłynął**|-Dla funkcji — średni czas włączny, który upłynął w przypadku wywołania tej funkcji.<br />— Dla modułu, średni czas włączny, który upłynął dla wszystkich wywołań funkcji w module.|
|**Maksymalny łączny czas, który upłynął**|-Dla funkcji — maksymalny czas, który upłynął, włącznie wywołania tej funkcji.<br />— W przypadku modułu maksymalny czas, który upłynął włącznie, dla wszystkich wywołań funkcji w module.|
|**Minimalny łączny czas, który upłynął**|-Dla funkcji — minimalny czas, który upłynął, włącznie wywołania tego modułu lub funkcji.<br />-Dla modułu, minimalny czas, który upłynął włącznie dla wszystkich wywołań funkcji w module.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęły
 Wartości wyłączne, które upłynęły, wskazują czas, przez który funkcja została bezpośrednio uruchomiona w górnej części stosu wywołań. Czas obejmuje czas wywołań systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|-Dla funkcji, czas spędzony w module lub funkcji. Obejmuje to wywołania systemu operacyjnego, takie jak przełączenia kontekstu i operacje wejścia/wyjścia, ale wyklucza czas spędzony w funkcjach podrzędnych.<br />-Dla modułu, suma czasu wyłącznego dla funkcji w module.|
|**% Czasu wyłącznego, który upłynął**|Wartość procentowa łącznego czasu trwania uruchomienia profilowania, która nastąpiła w łącznym czasie trwania tego modułu lub funkcji.|
|**Średni czas wyłączny, który upłynął**|— Dla funkcji — średni czas, który upłynął w przypadku wywołania tej funkcji.<br />— Dla modułu, średni czas wyłączny wszystkich wywołań funkcji w module.|
|**Maksymalny czas wyłączny, który upłynął**|— Dla funkcji, maksymalny czas wyłączny wywołania tej funkcji.<br />— W przypadku modułu maksymalny czas, który upłynął, przez wszystkie wywołania funkcji w module.|
|**Minimalny czas, który upłynął**|— Dla funkcji — minimalny czas, który upłynął podczas wywołania tego modułu lub funkcji.<br />— W przypadku modułu minimalny czas, który upłynął, w przypadku wszystkich wywołań funkcji w module.|

## <a name="application-inclusive-values"></a>Wartości włączne aplikacji
 Wartości włącznie obejmują czas, przez który funkcja była w stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, ale obejmuje czas spędzony w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny aplikacji**|-Dla funkcji, czas spędzony w wywołaniach funkcji. Obejmuje to czas spędzony w funkcjach podrzędnych, ale wyklucza wywołania systemu operacyjnego, takie jak operacje przełączania kontekstu i operacji wejścia/wyjścia.<br />-Dla modułu, okres czasu, w którym co najmniej jedna funkcja w module znajdował się w stosie wywołań, z wyłączeniem czasu spędzonego w wywołaniach do systemu operacyjnego.|
|**% Włącznego czasu aplikacji**|Wartość procentowa łącznego czasu trwania przebiegu profilowania, która została wykorzystana w czasie trwania tego modułu lub funkcji przez aplikację.|
|**Średni czas włączny aplikacji**|-Dla funkcji — średni czas włączny aplikacji wywołania tej funkcji.<br />-Dla modułu, średni czas włączania wszystkich wywołań funkcji w module.|
|**Maksymalny czas włączny aplikacji**|-Dla funkcji — maksymalny czas włączny aplikacji wywołania tej funkcji.<br />— W przypadku modułu maksymalny czas trwania wszystkich wywołań funkcji w module.|
|**Minimalny czas włączny aplikacji**|-Dla funkcji, minimalna godzina włącznego wywołania do tego modułu lub funkcji.<br />— W przypadku modułu minimalna dołączenia do funkcji w module (włącznie).|

## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji
 Wartości wyłączne aplikacji wskazują czas spędzony w module lub funkcji, z wyłączeniem czasu spędzonego w funkcjach podrzędnych. Wskazany czas również wyklucza wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny aplikacji**|-Dla funkcji — łączny czas trwania wywołań tej funkcji.<br />— W przypadku modułu łączny czas wyłączny aplikacji wszystkich wywołań funkcji w module.|
|**% Wyłącznego czasu aplikacji**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania, który został wykorzystany w niepełnym czasie aplikacji tego modułu lub funkcji.|
|**Średni czas wyłączny aplikacji**|-Dla funkcji — średni czas wyłączny aplikacji wywołania tej funkcji.<br />— Dla modułu, średni czas wyłączny aplikacji dla wszystkich wywołań funkcji w module.|
|**Maksymalny czas wyłączny aplikacji**|— W przypadku funkcji maksymalny czas wyłączny aplikacji wywołania tej funkcji.<br />— W przypadku modułu maksymalna, wyłączny czas aplikacji dla wszystkich wywołań funkcji w module.|
|**Minimalny czas wyłączny aplikacji**|— W przypadku funkcji jest to minimalny czas wyłączny aplikacji wywołania tego modułu lub funkcji.<br />— W przypadku modułu minimalna, wyłączny czas wszystkich wywołań funkcji w module.|

## <a name="see-also"></a>Zobacz także
- [Widok modułów-próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Widok modułów](../profiling/modules-view-instrumentation-data.md)
- [Widok modułów](../profiling/modules-view-sampling-data.md)
