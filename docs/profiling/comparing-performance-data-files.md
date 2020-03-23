---
title: Porównywanie plików danych o wydajności | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 64842c5b4f622a1f76aa528360f79403ec92cb42
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777860"
---
# <a name="compare-performance-data-files"></a>Porównywanie plików danych dotyczących wydajności

Funkcja porównywania plików danych Narzędzi profilowania umożliwia wybranie dwóch plików raportu (.* vsp* /lub . *vsps*) i wygenerować raport, który pokazuje różnice, regresji wydajności i ulepszenia, które wystąpiły z jednej sesji profilowania do drugiej.

Raport porównawczy plików [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] danych z narzędzi profilowania porównuje wyniki analizy w jednym pliku danych profilowania z wynikami analizy linii bazowej w innym pliku danych. Oba pliki danych muszą zostać wygenerowane przy użyciu tej samej metody profilowania. Raport analizowanych porównań jest zapisywany jako plik . *vsps.*

W widoku raportu porównawczego przedstawiono widok tabeli zmienionych danych. Tabela przedstawia delta lub zmiany od linii bazowej. Delta jest obliczana przez określenie różnicy między starą wartością, wartością bazową i wartością wyniku z nowej analizy.

Porównania danych profilera mogą być oparte na funkcjach w kodzie, modułach w aplikacji, wierszach, wskaźnikach instrukcji (IP) i typach.

Dane profilowania, które są dostępne do porównania, obejmują informacje wyświetlane w kolumnach. Aby zapoznać się z definicjami tych nazw kolumn, zobacz [Widoki raportu wydajności](../profiling/performance-report-views.md).

Próg można ustawić, aby zmniejszyć hałas i odfiltrować wszystkie dane w widoku tabeli porównawczej wierszy, które nie zostały zmienione o określoną kwotę.

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: porównywanie plików danych dotyczących wydajności](../profiling/how-to-compare-performance-data-files.md)
