---
title: Przegląd raportu wydajności | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 517156677a6d3711fa5dc2e4a15629a55229cfe2
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74772235"
---
# <a name="performance-report-overview"></a>Przegląd raportu wydajności
Dane profilowania sesji wydajności można wyświetlić w oknie **raport o wydajności** zintegrowanego środowiska projektowego programu Visual Studio Team System Development (IDE). Dane profilowania są zapisywane w plikach. vsp i. vsps. Widok raportu okna umożliwiają wyświetlanie i analizowanie problemów z wydajnością aplikacji.

> [!CAUTION]
> Plik danych profilowania zawiera poufne informacje, takie jak nazwa komputera, wersja systemu operacyjnego, ścieżki plików, informacje o pamięci i inne informacje o konfiguracji komputera. Należy zachować ścisłą kontrolę nad dystrybucją danych, zarówno w swojej natywnej. Format *VSP* i po jego wyeksportowaniu do. *wolumin CSV* lub. plik *XML* .
>
> Jeśli dane śledzenia zdarzeń są zbierane w ramach sesji wydajności, w dzienniku śledzenia zdarzeń mogą pojawić się dodatkowe informacje. *ETL*). Te informacje obejmują domenę i nazwę użytkownika; w związku z tym należy zachować ścisłą kontrolę nad dystrybucją pliku dziennika.

## <a name="performance-report-window"></a>Okno raportu wydajności
 Okno Raport wydajności jest oknem narzędzia, które służy do wyświetlania i filtrowania danych wydajności oraz zarządzania nimi, a także do dostosowywalnej kontroli zapytań.

 Na głównym pasku narzędzi okna Raport o wydajności możesz uzyskać dostęp do każdego widoku. Kliknij strzałkę obok listy **bieżący widok** , aby wyświetlić i wybrać poszczególne dostępne widoki.

 Okno Raport o wydajności zawiera następujące widoki danych:

### <a name="summary-view"></a>Widok podsumowania
 Domyślnie dane profilowania są wyświetlane w widoku podsumowania. Ten widok jest punktem wyjścia w trakcie badania problemów z wydajnością. W każdym wierszu widoku Podsumowanie możesz przejść do bardziej szczegółowych widoków, klikając prawym przyciskiem myszy nazwę funkcji lub modułu. Aby uzyskać więcej informacji, zobacz [Widok podsumowania](../profiling/summary-view.md).

### <a name="callercallee-view"></a>Widok wywołujący/wywoływany
 Widok wywołujący/wywoływany Wyświetla drzewo wywołań dla pojedynczej funkcji. Widok jest podzielony na trzy części:

- Funkcja docelowa jest wyświetlana w połowie widoku.

- Funkcje, które wywołały funkcję (obiekty wywołujące), są wyświetlane powyżej funkcji docelowej.

- Funkcje, które są wywoływane przez funkcję docelową (wywoływane), są wyświetlane poniżej obiektu docelowego.

  Możesz wybrać inną funkcję przez dwukrotne kliknięcie dowolnej funkcji na liście wywoływanych lub liście wywoływanych. Aby uzyskać więcej informacji, zobacz [Widok wywołujący/wywoływany](../profiling/caller-callee-view.md).

### <a name="call-tree-view"></a>Widok drzewa wywołań
 W widoku drzewa wywołań są wyświetlane ścieżki wykonywania funkcji, które zostały przesunięte w profilowanej aplikacji. Katalog główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich wywoływanych funkcji i danych wydajności dotyczących tych wywołań funkcji.

 Widok drzewa wywołań może również rozszerzać i wyróżniać ścieżkę wykonywania funkcji, która zużywa najwięcej czasu lub była najczęściej próbkowana. Aby wyświetlić najbardziej aktywną ścieżkę, kliknij ją prawym przyciskiem myszy, a następnie kliknij polecenie **Rozwiń ścieżkę gorącą**. Aby uzyskać więcej informacji, zobacz [Widok drzewa wywołań](../profiling/call-tree-view.md).

### <a name="process-view"></a>Widok procesu
 Widok procesu przedstawia dane wydajności dla każdego procesu i wątku, które zostały profilowane. Aby uzyskać więcej informacji, zobacz [Widok procesu](../profiling/process-view.md).

### <a name="modules-view"></a>Widok modułów
 Widok moduły wyświetla listę modułów w projekcie i przedstawia dane profilowania dla każdego modułu. Rozwiń lub Zwiń nazwę modułu, aby wyświetlić dane profilowania funkcji. Gdy dane zostały zebrane przy użyciu próbkowania, dostępne są również dane profilowania kodu źródłowego i wskaźnika instrukcji. Aby uzyskać więcej informacji, zobacz [Widok modułów](../profiling/modules-view.md).

### <a name="functions-view"></a>Widok funkcji
 Widok funkcji zawiera listę funkcji, które zostały wywołane podczas profilowania. Aby uzyskać więcej informacji, zobacz [Widok funkcji](../profiling/functions-view.md).

### <a name="line-view"></a>Widok wiersza
 Widok linie umożliwia wyświetlenie określonych wierszy kodu źródłowego, które zostały wykonane podczas profilowania próbkowania. Aby uzyskać więcej informacji, zobacz [Widok linii](../profiling/lines-view.md).

### <a name="instruction-pointer-ip-view"></a>Widok wskaźnika instrukcji (IP)
 Widok wskaźnika instrukcji umożliwia wyświetlenie określonych instrukcji, które zostały wykonane podczas profilowania próbkowania. Aby uzyskać więcej informacji, zobacz [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view.md).

### <a name="allocation-view"></a>Widok alokacji
 Widok alokacja jest dostępny, jeśli na stronie **Ogólne** okna dialogowego właściwości **sesji wydajności** została wybrana wartość **Zbieraj alokacje obiektów .NET** . Zobacz [Omówienie sesji wydajności](../profiling/performance-session-overview.md). Widok alokacja zawiera listę obiektów .NET, które zostały przydzielone przez aplikację lub składnik. Gdy wiersz obiektu jest rozwinięty, zostanie wyświetlona drzewo wywołań. Drzewo wywołań pokazuje ścieżki wykonywania, które spowodowały utworzenie obiektu. Wyświetlane są również informacje o liczbie włącznych i wyłącznych alokacji dla każdej funkcji w drzewie wywołań. Widok Alokacja może także rozwijać i wyróżniać ścieżkę wykonywania funkcji, która przydzieliła największą liczbę obiektów. Aby wyświetlić najbardziej aktywną ścieżkę, kliknij ją prawym przyciskiem myszy, a następnie kliknij polecenie **Rozwiń ścieżkę gorącą**. Aby uzyskać więcej informacji, zobacz [zbieranie danych dotyczących alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) oraz [przydziałów](../profiling/dotnet-memory-allocations-view.md).

### <a name="objects-lifetime-view"></a>Widok okresu istnienia obiektów
 Widok okresu istnienia obiektu jest dostępny w przypadku **zbierania informacji o alokacji obiektu .NET** i zbierania informacji o **okresie istnienia obiektu .NET** na stronie **Ogólne** w oknie dialogowym właściwości **sesji wydajności** .

 Widok okres istnienia obiektu przedstawia łączną liczbę wystąpień każdego typu i liczbę obiektów, które zostały zebrane w każdej generacji wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji, zobacz [Widok okresu istnienia obiektu](../profiling/object-lifetime-view.md).

## <a name="customizable-filter-control"></a>Dostosowywalny formant filtru
 Dostosowywalny formant filtru zawiera następujące opcje:

- **Import Filter** — pobiera poprzednio zapisane zapytanie niestandardowe.

- **Export Filter** — zapisuje niestandardowe zapytanie w określonej lokalizacji.

- **Wykonywanie zapytania** — uruchamia zapytanie w sposób, jak to jest wyświetlane w niestandardowej kontrolce zapytania.

- **Zatrzymaj zapytanie** — zatrzymuje wykonywanie zapytania, które jest uruchomione. Ten przycisk jest niedostępny, jeśli żadna kwerenda nie jest uruchomiona.

- **Pokaż zapytanie** -pokazuje/ukrywa niestandardową kontrolkę zapytania.

- **Zapisana** analiza — zapisuje raport wraz z bieżącą analizą jako plik. vsps.

- **Eksportuj** — zapisuje bieżący raport w. CVS — sformatowany lub. Plik w formacie XML z opcjami umożliwiającymi zapisanie różnych widoków.

## <a name="see-also"></a>Zobacz także
- [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)
- [Widoki raportów wydajności](../profiling/performance-report-views.md)
