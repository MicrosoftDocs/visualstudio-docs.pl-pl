---
title: Omówienie raportów wydajności | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ff52925dea61916b9fa27af8cfacc044588cdb75
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785625"
---
# <a name="performance-report-overview"></a>Raport dotyczący wydajności — omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można wyświetlić danych profilowania w sesji pomiaru wydajności **raport dotyczący wydajności** okna programu Visual Studio Team System Development Edition zintegrowanego środowiska programistycznego (IDE). Profilowania dane są zapisywane w plikach .vsp i .vsps. Widok raportu w systemie windows umożliwiają można wyświetlać i analizować problemy z wydajnością aplikacji.  
  
> [!CAUTION]
>  Plik danych profilowania zawiera poufne informacje, takie jak nazwa komputera, wersję systemu operacyjnego, ścieżki do plików, informacje o pamięci i innych informacji o instalacji na komputerze. Należy zachować ścisłą kontrolę nad dystrybucją danych, w formacie .vsp natywnych i podczas eksportowania do pliku CSV lub plik XML.  
>   
>  Jeśli dane śledzenia zdarzeń są zbierane w ramach sesji wydajności, dodatkowe informacje mogą być wyświetlane w zdarzeniu śledzenia plik dziennika (ETL). Te informacje obejmują nazwę domeny oraz nazwę użytkownika; w związku z tym należy zachować ścisłą kontrolę nad dystrybucją w pliku dziennika.  
  
## <a name="performance-report-window"></a>Okno raportu wydajności  
 Okno Raport dotyczący wydajności jest oknem narzędzi, który służy do wyświetlania, zarządzanie i filtrować dane dotyczące wydajności, a także kontroli dostosowywalne zapytania.  
  
 Na głównym pasku narzędzi okna Raport o wydajności możesz uzyskać dostęp każdy widok. Kliknij strzałkę obok pozycji **bieżący widok** listy do wyświetlania i wybierania poszczególnych widoków, które są dostępne.  
  
 Okno Raport wydajności zawiera następujące widoki danych:  
  
### <a name="summary-view"></a>Widok podsumowania  
 Domyślnie dane profilowania jest wyświetlany w widoku podsumowania. Ten widok jest punktem wyjścia w badaniu na problemy z wydajnością. Z każdego wiersza w widoku podsumowania można przenieść do bardziej szczegółowych widoków przez kliknięcie prawym przyciskiem myszy nazwę funkcji lub modułu. Aby uzyskać więcej informacji, zobacz [Widok Podsumowanie](../profiling/summary-view.md).  
  
### <a name="callercallee-view"></a>Widok wywołujący/wywoływany  
 Widok wywołujący/wywoływany Wyświetla drzewo wywołań dla poszczególnych funkcji. Widok jest podzielony na trzy części:  
  
- Funkcja docelowa jest wyświetlany w środku widoku.  
  
- Funkcje, które wywołuje funkcję (obiekty wywołujące) są wyświetlane powyżej docelowej funkcji.  
  
- Funkcje, które są wywoływane przez funkcję target (wywoływane) są wyświetlane poniżej wartości docelowej.  
  
  Możesz wybrać inną funkcję przez dwukrotne kliknięcie dowolnej funkcji, na liście o nazwie lub na liście / / wywoływany. Aby uzyskać więcej informacji, zobacz [widok wywołujący/wywoływany](../profiling/caller-callee-view.md).  
  
### <a name="call-tree-view"></a>Widok drzewa wywołań  
 Widok drzewa wywołania Wyświetla ścieżki wykonywania funkcji, które zostały przesunięta w profilowanej aplikacji. Główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji Wyświetla wszystkie funkcje, które go wywołały i dane wydajności dotyczące tych wywołań funkcji.  
  
 Widok drzewa wywołania można również rozwijać i Podświetlenie ścieżki wykonywania funkcji, która użyte najwięcej czasu lub zostało pobrane najczęściej. Aby wyświetlić najbardziej aktywne ścieżkę, kliknij prawym przyciskiem myszy funkcję, a następnie kliknij przycisk **Rozwiń ścieżkę aktywną**. Aby uzyskać więcej informacji, zobacz [widok drzewa wywołań](../profiling/call-tree-view.md).  
  
### <a name="process-view"></a>Widok procesu  
 Widok procesu przedstawia dane wydajności dla każdego procesu i wątku, która była profilowana. Aby uzyskać więcej informacji, zobacz [widok procesu](../profiling/process-view.md).  
  
### <a name="modules-view"></a>Widok modułów  
 Widok modułów Wyświetla listę modułów w projekcie i przedstawia danych profilowania dla każdego modułu. Rozwiń lub Zwiń nazwę modułu, aby wyświetlić dane profilowania funkcji. Podczas zbierania danych za pomocą próbkowania, źródła kodu wiersza i instrukcje wskaźnik danych profilowania jest również dostępna. Aby uzyskać więcej informacji, zobacz [widok modułów](../profiling/modules-view.md).  
  
### <a name="functions-view"></a>Widok funkcji  
 Widok funkcji zawiera listę funkcji, które zostały wywołane podczas profilowania. Aby uzyskać więcej informacji, zobacz [widoku funkcji](../profiling/functions-view.md).  
  
### <a name="line-view"></a>Widok wiersza  
 Widok linii umożliwia wyświetlenie określonego źródła wierszy kodu, które zostały wykonane podczas pobierania próbek profilowania. Aby uzyskać więcej informacji, zobacz [widok linii](../profiling/lines-view.md).  
  
### <a name="instruction-pointer-ip-view"></a>Widok wskaźnika (IP) w instrukcji  
 Widok wskaźnika instrukcji umożliwia wyświetlenie szczegółowych instrukcji, które zostały wykonane podczas pobierania próbek profilowania. Aby uzyskać więcej informacji, zobacz [widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view.md).  
  
### <a name="allocation-view"></a>Widok alokacji  
 Widok alokacji jest dostępny jeśli **przydziału obiektu .NET zbieranie** został wybrany na **ogólne** strony **sesji wydajności** okno dialogowe właściwości. Zobacz [sesja wydajności — omówienie](../profiling/performance-session-overview.md). Widok alokacji Wyświetla listę obiektów platformy .NET, które zostały przydzielone przez aplikację lub składnik. Po rozwinięciu wiersza obiektu drzewo wywołań jest wyświetlany. Drzewo wywołań pokazuje ścieżki wykonywania, które spowodowało utworzenie obiektu. Są również informacje o liczbie przydziały włączne i wyłączne dla poszczególnych funkcji w drzewie wywołań. Widok alokacji można również rozwijać i Podświetlenie ścieżki wykonywania funkcji, która przydzielona największej liczby obiektów. Aby wyświetlić najbardziej aktywne ścieżkę, kliknij prawym przyciskiem myszy funkcję, a następnie kliknij przycisk **Rozwiń ścieżkę aktywną**. Aby uzyskać więcej informacji, zobacz [zbieranie alokacji pamięci .NET i danych o okresie istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) i [Widok alokacji](../profiling/dotnet-memory-allocations-view.md).  
  
### <a name="objects-lifetime-view"></a>Widok okresu istnienia obiektów  
 Widok okresu istnienia obiektu jest dostępny jeśli **informacje dotyczące alokacji obiektów .NET zbieranie** i **również zbierać informacje dotyczące okresu istnienia obiektu platformy .NET** zostały wybrane na **ogólne**strony **sesji wydajności** okno dialogowe właściwości.  
  
 Widok okresu istnienia obiektu Wyświetla całkowitą liczbę wystąpień każdego typu i liczby obiektów, które zostały zebrane w wszystkich generacjach wyrzucania. Aby uzyskać więcej informacji, zobacz [widok okresu istnienia obiektu](../profiling/object-lifetime-view.md).  
  
## <a name="customizable-filter-control"></a>Formant filtru można dostosowywać  
 Formant filtru można dostosowywać ma następujące opcje:  
  
-   **Importowanie filtru** — pobiera wcześniej zapisane zapytanie niestandardowe.  
  
-   **Eksportuj filtr** — zapisuje niestandardowe zapytanie do określonej lokalizacji.  
  
-   **Wykonaj zapytanie** — wykonuje zapytanie, wyświetlana w formancie zapytanie niestandardowe.  
  
-   **Zatrzymaj zapytanie** -zatrzymuje wykonywanie zapytania, który jest uruchomiony. Ten przycisk jest dostępny, jeśli jest uruchomiony bez określenia zapytania.  
  
-   **Wyświetl zapytanie** — pokazuje lub ukrywa Kontrolki niestandardowe zapytanie.  
  
-   **Zapisz Analyzed** — raport wraz z jego bieżącej analizy jest zapisywany jako plik .vsps.  
  
-   **Eksportuj** — zapisuje bieżący raport w. Sformatowana CVS lub. Pliku w formacie XML, z opcjami, aby zapisać różne widoki.  
  
## <a name="see-also"></a>Zobacz też  
 [Analizowanie wydajności danych dotyczących narzędzi](../profiling/analyzing-performance-tools-data.md)   
 [Widoki raportu wydajności](../profiling/performance-report-views.md)
