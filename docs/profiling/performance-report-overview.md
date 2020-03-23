---
title: Przegląd raportu o wynikach | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772235"
---
# <a name="performance-report-overview"></a>Omówienie raportu wydajności
Można wyświetlić dane profilowania sesji wydajności w oknie **raport wydajności** visual studio team system programistycznego zintegrowanego środowiska programistycznego (IDE). Dane profilowania są zapisywane w plikach vsp i .vsps. Okna widoku raportu umożliwiają wyświetlanie i analizowanie problemów z wydajnością aplikacji.

> [!CAUTION]
> Plik danych profilowania zawiera poufne informacje, takie jak nazwa komputera, wersja systemu operacyjnego, ścieżki plików, informacje o pamięci i inne informacje o konfiguracji komputera. Należy zachować ścisłą kontrolę nad dystrybucją danych, zarówno w ich natywnych . *vsp* i gdy jest eksportowany do . *csv* lub . *xml.*
>
> Jeśli dane śledzenia zdarzeń są zbierane w ramach sesji wydajności, dodatkowe informacje mogą pojawić się w dzienniku śledzenia zdarzeń (.* etl*). Informacje te obejmują domenę i nazwę użytkownika; w związku z tym należy zachować ścisłą kontrolę nad dystrybucją pliku dziennika.

## <a name="performance-report-window"></a>Okno Raport o wydajności
 Okno Raport wydajności jest oknem narzędzia, które służy do wyświetlania danych o wydajności, zarządzania i filtrowania, i zawiera konfigurowalną kontrolę kwerend.

 Na głównym pasku narzędzi okna Raport wydajności można uzyskać dostęp do każdego widoku. Kliknij strzałkę obok listy **Widok bieżący,** aby wyświetlić i wybrać poszczególne widoki, które są dostępne.

 Okno Raport wydajności zawiera następujące widoki danych:

### <a name="summary-view"></a>Widok podsumowania
 Domyślnie dane profilowania są wyświetlane w widoku Podsumowanie. Ten widok jest punktem wyjścia w badaniu problemów z wydajnością. Z każdego wiersza w widoku Podsumowanie można przejść do bardziej szczegółowych widoków, klikając prawym przyciskiem myszy nazwę funkcji lub modułu. Aby uzyskać więcej informacji, zobacz [Widok podsumowania](../profiling/summary-view.md).

### <a name="callercallee-view"></a>Widok wywołujący/wywoływany
 Widok wywołujący/wywoływany wyświetla drzewo wywołań dla pojedynczej funkcji. Widok jest podzielony na trzy części:

- Funkcja docelowa jest wyświetlana w środku widoku.

- Funkcje, które wywoływały funkcję (wywołujących) są wyświetlane powyżej funkcji docelowej.

- Funkcje wywoływane przez funkcję docelową (wywoływane) są wyświetlane poniżej obiektu docelowego.

  Można wybrać inną funkcję, klikając dwukrotnie dowolną funkcję na liście wywoływanych lub na liście wywoływanych. Aby uzyskać więcej informacji, zobacz [Widok wywołującego/wywoływania](../profiling/caller-callee-view.md).

### <a name="call-tree-view"></a>Widok drzewa wywołań
 Widok Drzewa wywołań wyświetla ścieżki wykonywania funkcji, które zostały przesuniętych w profilowanej aplikacji. Katalog główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich funkcji, które wywołuje i dane wydajności o tych wywołań funkcji.

 Widok drzewa wywołań można również rozwinąć i wyróżnić ścieżkę wykonywania funkcji, która pochłonęła najwięcej czasu lub była najczęściej próbkowana. Aby wyświetlić najbardziej aktywną ścieżkę, kliknij tę funkcję prawym przyciskiem myszy, a następnie kliknij polecenie **Rozwiń ścieżkę gorącą**. Aby uzyskać więcej informacji, zobacz [Widok drzewa wywołań](../profiling/call-tree-view.md).

### <a name="process-view"></a>Widok procesu
 W widoku Proces są wyświetlane dane dotyczące wydajności dla każdego procesu i wątku, który został profilowany. Aby uzyskać więcej informacji, zobacz [Widok procesu](../profiling/process-view.md).

### <a name="modules-view"></a>Widok modułów
 Widok Moduły wyświetla listę modułów w projekcie i przedstawia dane profilowania dla każdego modułu. Rozwiń lub zwiń nazwę modułu, aby wyświetlić dane profilowania funkcji. Gdy dane zostały zebrane przy użyciu próbkowania, wiersz kodu źródłowego i dane profilowania wskaźnika instrukcji jest również dostępna. Aby uzyskać więcej informacji, zobacz [Widok modułów](../profiling/modules-view.md).

### <a name="functions-view"></a>Widok funkcji
 Widok Funkcje zawiera listę funkcji, które zostały wywołane podczas profilowania. Aby uzyskać więcej informacji, zobacz [Widok funkcji](../profiling/functions-view.md).

### <a name="line-view"></a>Widok linii
 Widok Linie umożliwia wyświetlanie określonych wierszy kodu źródłowego, które zostały wykonane podczas profilowania próbkowania. Aby uzyskać więcej informacji, zobacz [Widok wierszy](../profiling/lines-view.md).

### <a name="instruction-pointer-ip-view"></a>Widok wskaźnika instrukcji (IP)
 Widok wskaźnik instrukcji umożliwia wyświetlanie określonych instrukcji, które zostały wykonane podczas profilowania próbkowania. Aby uzyskać więcej informacji, zobacz [Widok wskaźników instrukcji ..](../profiling/instruction-pointers-ips-view.md)

### <a name="allocation-view"></a>Widok alokacji
 Widok Alokacja jest dostępny, jeśli na stronie **Ogólne** okna dialogowego właściwości **sesji wydajności** wybrano opcję Zbierz **alokację obiektu .NET.** Zobacz [Omówienie sesji wydajności](../profiling/performance-session-overview.md). Widok Alokacja zawiera listę obiektów .NET, które zostały przydzielone przez aplikację lub składnik. Po rozwinięciu wiersza obiektu wyświetlane jest drzewo wywołań. Drzewo wywołań pokazuje ścieżki wykonywania, które doprowadziły do utworzenia obiektu. Wyświetlane są również informacje o liczbie alokacji włączających i wyłącznych dla każdej funkcji w drzewie wywołań. Widok Alokacja można również rozwinąć i wyróżnić ścieżkę wykonywania funkcji, która przydzieliła największą liczbę obiektów. Aby wyświetlić najbardziej aktywną ścieżkę, kliknij tę funkcję prawym przyciskiem myszy, a następnie kliknij polecenie **Rozwiń ścieżkę gorącą**. Aby uzyskać więcej informacji, zobacz [Zbieranie alokacji pamięci .NET oraz danych okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) oraz widoku [Alokacje](../profiling/dotnet-memory-allocations-view.md).

### <a name="objects-lifetime-view"></a>Widok okresu istnienia obiektów
 Widok Okres istnienia obiektu jest dostępny, jeśli w oknie dialogowym Właściwości sesji **General** **wydajności** wybrano informacje **o alokacji obiektów .NET** i również **zbierać informacje o okresie istnienia obiektu .NET.**

 W widoku Okres istnienia obiektu wyświetlana jest całkowita liczba wystąpień każdego typu oraz liczba obiektów zebranych w każdym generowaniu wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji, zobacz [Widok okresu istnienia obiektu](../profiling/object-lifetime-view.md).

## <a name="customizable-filter-control"></a>Konfigurowalna kontrola filtra
 Konfigurowalny formant filtru ma następujące opcje:

- **Importuj filtr** — pobiera wcześniej zapisaną kwerendę niestandardową.

- **Eksportuj filtr** — zapisuje kwerendę niestandardową w określonej lokalizacji.

- **Execute Query** - uruchamia kwerendę wyświetlaną w formancie kwerendy niestandardowej.

- **Zatrzymaj kwerendę** - zatrzymuje wykonywanie uruchomionej kwerendy. Ten przycisk nie jest dostępny, jeśli nie jest uruchomiona żadna kwerenda.

- **Pokaż kwerendę** - pokazuje/ukrywa niestandardową kontrolę kwerendy.

- **Zapisz analizowane** - zapisuje raport wraz z jego bieżącej analizy jako plik vsps.

- **Eksport -** zapisuje bieżący raport w pliku . W formacie CVS lub . Plik w formacie XML z opcjami zapisywania różnych widoków.

## <a name="see-also"></a>Zobacz też
- [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)
- [Widoki raportu o skuteczności](../profiling/performance-report-views.md)
