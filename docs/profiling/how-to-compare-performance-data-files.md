---
title: 'Jak: Porównanie plików danych wydajności | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c6dc9d485f6f40eb345ade8f9680be9e0b948106
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779002"
---
# <a name="how-to-compare-performance-data-files"></a>Instrukcje: porównywanie plików danych dotyczących wydajności
Można porównać wyniki dwóch różnych plików danych profilera (.* vsp* lub . *vsps*) przez utworzenie raportu lub widoku porównania ("Diff"). Porównanie pokazuje różnice, regresji wydajności i ulepszenia, które wystąpiły z jednej sesji profilowania do drugiej.

 Raport Diff przedstawia widok tabeli danych. Tabela przedstawia delta lub zmiany od linii bazowej. Jest to obliczane przez określenie różnicy między starą wartością, wartością bazową i wartością wyniku z nowej analizy.

 Porównania danych profilera mogą być oparte na funkcjach w kodzie, modułach w aplikacji, wierszach, wskaźnikach instrukcji (IP) i typach.

 Próg można ustawić, aby zmniejszyć hałas i odfiltrować wszystkie dane w widoku tabeli wierszy, które nie zostały zmienione o określoną kwotę.

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Aby utworzyć widok pliku porównania dla projektu w Eksploratorze wydajności

1. W **Eksploratorze wydajności**w obszarze **Raporty**wybierz opcję . *vsp* lub . *vsps* plik raportu, który ma być używany jako wartości linii bazowej do porównania.

2. Wybierz plik . *vsp* lub . *vsps* plików raportu, które chcesz porównać.

3. Kliknij prawym przyciskiem myszy jeden z zaznaczonych plików, a następnie kliknij polecenie **Porównaj raporty**.

### <a name="to-compare-values"></a>Aby porównać wartości

1. Wybierz kartę **Raport porównawczy** w oknie Widok raportu.

2. Z listy rozwijanej **Tabela** wybierz jedną z funkcji lub modułów do porównania.

3. Z listy rozwijanej **Kolumna** wybierz wartość, którą chcesz porównać.

4. (opcjonalnie) Wpisz wartość **dla progu**.

5. Kliknij przycisk **Zastosuj**.

### <a name="to-compare-report-files"></a>Aby porównać pliki raportu

1. W menu **Analiza** wybierz polecenie **Porównaj raporty wydajności**.

2. W oknie **Wybierz pliki analizy do porównania** przeglądaj i wybierz plik analizy pliku linii **bazowej** (.* vsp* lub . *vsps*) oraz **plik porównawczy** (.* vsp* lub . *vsps*).

3. Kliknij przycisk **OK**.
