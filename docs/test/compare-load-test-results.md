---
title: Porównanie wyników testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, results
ms.assetid: 31874114-459a-45d5-9f8b-2ea503627db8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: fc54324f2c5bc91dba64aa35b125bbdc12ca1a45
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895031"
---
# <a name="report-load-tests-results-for-test-comparisons-or-trend-analysis"></a>Testy obciążenia raport wyników dla potrzeb porównań testów lub analizy trendów

Można generować raporty testu obciążenia programu Microsoft Excel, które opierają się na dwóch lub więcej wynikach badań.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Dostępne są dwa typy raportów testów obciążenia:

- Uruchom porównanie&mdash;ten raport jest faktycznie dwóch raportów, które wyświetlają dane porównania side-by-side przy użyciu tabel i wykresów słupkowych.

- Trend&mdash;możesz wygenerować analizy trendu na podstawie co najmniej dwóch raportów. Wyniki są wyświetlane przy użyciu wykresów liniowych.

Raport może służyć do udostępniania danych dotyczących wydajności zainteresowanym osobom i przekazywania, czy ogólna wydajność i kondycja systemu jest coraz lepsza czy gorsza.

Definicje raportów są przechowywane w bazie danych testu obciążenia. Po zapisaniu raportu definicja raportu jest zapisywany w bazie danych i mogą być używane ponownie później.

Ponadto plik arkusza kalkulacyjnego mogą być udostępniane zainteresowane strony, aby nie trzeba połączyć z bazą danych, aby wyświetlić raport zainteresowanych stron.

> [!NOTE]
> Po dodaniu komentarzy do testu obciążenia są wyświetlane w raporcie programu Excel.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Tworzenie raportu wydajności i obciążenia:** można tworzyć raporty na testy wydajności sieci web i obciążenia, przy użyciu programu Microsoft Excel.|- [Porady: tworzenie w programie Microsoft Excel raportów wydajności testu obciążenia](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)|
|**Ręczne tworzenie raportu wydajności i obciążenia za pomocą programu Microsoft Word:** można tworzyć raporty na testy wydajności sieci web i obciążenia ręcznie kopiując i wklejając podsumowanie, tabeli i dane wykresu do dokumentu programu Microsoft Word.|- [Porady: ręczne tworzenie raportu wydajności testu obciążenia przy użyciu programu Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md)|

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)