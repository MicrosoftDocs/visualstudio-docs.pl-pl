---
title: Widok podsumowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 87692c938462f166f93b4cfb8b223a45e2553ada
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771588"
---
# <a name="summary-view"></a>Widok podsumowania
W widoku Podsumowanie są wyświetlane informacje o najbardziej kosztownych z wydajnością funkcjach lub obiektach w przebiegu profilowania. Ten widok zawiera wykres osi czasu i dwie lub więcej list najdroższych funkcji lub obiektów na podstawie metryk wydajności metody profilowania. Dane w tym widoku zależy od metody profilowania, który został użyty (próbkowanie, instrumentacji lub współbieżności) i czy alokacja pamięci .NET została zebrana.

 Dla wszystkich widoków podsumowania z wyjątkiem widoku podsumowania danych współbieżności, wykres osi czasu w widoku Podsumowanie pokazuje procesor (CPU) wykorzystanie profilowane aplikacji w czasie, gdy profilowanie miało miejsce.

- Jeśli określisz segment czasu na wykresie, możesz ponownie przeanalizować dane dla tego segmentu lub powiększyć wyświetlanie osi czasu do określonego segmentu. Aby uzyskać więcej informacji, zobacz [Jak: Filtrowanie widoków raportu z osi czasu podsumowania](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

- Można kliknąć funkcję na liście Widok podsumowania, aby otworzyć widok Szczegóły funkcji dla tej funkcji. Można również kliknąć prawym przyciskiem myszy funkcję dla innych opcji widoku.

- Aby zmodyfikować liczbę elementów wyświetlanych na listach widoków podsumowania, otwórz menu **Narzędzia,** wskaż **polecenie Opcje**, a następnie kliknij polecenie **Narzędzia wydajności**. W obszarze **Ustawienia ogólne**zmodyfikuj ustawienie Liczba funkcji w **widoku Podsumowanie.**

## <a name="notifications-links"></a>Linki powiadomień
 Możesz kliknąć łącza na liście Powiadomień, aby ustawić opcje wyświetlania raportu. Lista znajduje się po prawej stronie wykresu osi czasu.

|||
|-|-|
|**Pokaż kod niebędący użytkownikiem**<br /><br /> **Pokaż tylko mój kod**|Niedostępne dla kodu macierzystego lub profilowania danych, które zostały zebrane przy użyciu metody instrumentacji. Przełącza między wyświetlaniem tylko danych z kodu użytkownika (**Pokaż tylko mój kod**) a wyświetlaniem danych z całego kodu, w tym kodu systemu ( Pokaż kod**niebędący użytkownikiem**). Domyślnie dane są ograniczone do kodu użytkownika. Aby zmienić to ustawienie, zobacz [Jak: Filtrowanie widoków raportów narzędzi profilowania, aby wyświetlić tylko mój kod](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|
|**Wskazówki dotyczące wyświetlania**|Wyświetla ostrzeżenia reguły wydajności w oknie **Lista błędów.** Aby uzyskać więcej informacji, zobacz [Analizowanie danych za pomocą reguł wydajności](../profiling/using-performance-rules-to-analyze-data.md)|

## <a name="report"></a>Raport
 Możesz kliknąć łącza na liście Raport, aby otworzyć różne widoki i porównać, zapisać lub odfiltrować raport. Lista znajduje się po prawej stronie wykresu osi czasu.

| | |
|----------------------------| - |
| **Pokaż przycięte drzewo wywoławów** | Wyświetla najdroższe ścieżki wykonywania w widoku drzewa wywołań. Aby uzyskać więcej informacji, zobacz [Widok drzewa wywołań](../profiling/call-tree-view.md). |
| **Pokaż gorące linie** | Opcja niedostępna dla danych profilowania, które zostały zebrane przy użyciu metody instrumentacji. Wyświetla najdroższe wiersze kodu źródłowego w widoku wierszy. Aby uzyskać więcej informacji, zobacz [Widok wierszy](../profiling/lines-view.md). |
| **Porównaj raporty** | Wyświetla okno dialogowe **Wybieranie plików analizy do porównywania,** w którym można określić inny plik danych profilowania do porównania z bieżącym plikiem. Aby uzyskać więcej informacji, zobacz [Porównanie plików danych wydajności](../profiling/comparing-performance-data-files.md). |
| **Dane raportu eksportu** | Wyświetla okno dialogowe **Eksportowanie raportu,** w którym można określić jeden lub więcej widoków raportu, które mają być zapisywane jako pliki oddzielone przecinkami (csv) lub xml. Aby uzyskać więcej informacji, zobacz [Jak: Eksportowanie raportów narzędzi profilowania](/previous-versions/visualstudio/visual-studio-2010/ms182394\(v\=vs.100\)). |
| **Zapisz analizowany raport** | Zapisuje bieżący plik danych profilowania jako plik vsps, który [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]otwiera się szybciej w interfejsie dla . Aby uzyskać więcej informacji, zobacz [Jak: Zapisywanie analizowanych plików danych profilowania](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\)). |
| **Filtruj dane raportu** | Wyświetla okienko filtru raportu profilowania, w którym można określić kryteria ograniczania danych w widoku raportu. Aby uzyskać więcej informacji, zobacz [filtr widoku raportu o skuteczności](../profiling/performance-report-view-filter.md) |
| **Przełączanie pełnego ekranu** | Przełącza tryb pełnoekranowy dla widoku raportu. |

## <a name="see-also"></a>Zobacz też
- [Widok podsumowania — dane próbkowania](../profiling/summary-view-sampling-data.md)
- [Widok podsumowania - dane oprzyrządowania](../profiling/summary-view-instrumentation-data.md)
- [Widok podsumowania — dane pamięci .NET](../profiling/summary-view-dotnet-memory-data.md)
