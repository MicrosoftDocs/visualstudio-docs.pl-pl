---
title: Porównywanie plików danych wydajności | Microsoft Docs
description: Użyj narzędzia profilowania, aby porównać dwa pliki raportów (. vsp lub. vsps). Porównanie pokazuje różnice, regresje wydajności i ulepszenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8d1c57c6c3dd8d7d01e37eae374c547e074d62e6
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533501"
---
# <a name="compare-performance-data-files"></a>Porównywanie plików danych dotyczących wydajności

Funkcja porównywania plików danych narzędzia profilowania umożliwia wybranie dwóch plików raportu (.*VSP* lub. *vsps*) pliki i generują raport pokazujący różnice, regresje wydajności i ulepszenia, które wystąpiły z jednej sesji profilowania do drugiej.

Raport porównania plików danych z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania porównuje wyniki analizy w jednym pliku danych profilowania do wyników analizy linii bazowej w innym pliku danych. Oba pliki danych muszą zostać wygenerowane za pomocą tej samej metody profilowania. Raport porównania analizowane jest zapisywany jako. plik *vsps* .

Widok raportu porównawczego przedstawia widok tabeli zmienionych danych. W tabeli przedstawiono różnice lub zmiany z linii bazowej. Różnica jest obliczana przez określenie różnicy między starą wartością, wartością bazową i wartością wyniku z nowej analizy.

Porównania danych profilera mogą opierać się na funkcjach w kodzie, modułach w aplikacji, wierszach, wskaźnikach instrukcji (IP) i typach.

Profilowanie danych, które są dostępne do porównania, zawiera informacje, które są wyświetlane w kolumnach. Aby uzyskać definicje tych nazw kolumn, zobacz [widoki raportów wydajności](../profiling/performance-report-views.md).

Próg można ustawić, aby zmniejszyć szum i odfiltrować dane w widoku tabeli porównawczej wierszy, które nie uległy zmianie o określoną wartość.

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: porównywanie plików danych dotyczących wydajności](../profiling/how-to-compare-performance-data-files.md)
