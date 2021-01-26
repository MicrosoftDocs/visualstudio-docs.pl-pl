---
title: Porównywanie plików danych wydajności | Microsoft Docs
description: Dowiedz się, jak porównać wyniki dwóch różnych plików danych profilera (. vsp lub. vsps), aby znaleźć różnice, regresje wydajności i ulepszenia wydajności.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 40988d23dd8e9b848ea410aa75f4d4c1f45d524d
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800452"
---
# <a name="how-to-compare-performance-data-files"></a>Instrukcje: porównywanie plików danych dotyczących wydajności
Można porównać wyniki dwóch różnych plików danych profilera (.*VSP* lub. *vsps*) przez utworzenie porównania ("diff") raportu lub widoku. Porównanie pokazuje różnice, regresje wydajności i ulepszenia, które wystąpiły w jednej sesji profilowania.

 Raport diff przedstawia widok tabeli danych. W tabeli przedstawiono różnice lub zmiany z linii bazowej. Jest to obliczane przez określenie różnicy między starą wartością, wartością bazową i wartością wyniku z nowej analizy.

 Porównania danych profilera mogą opierać się na funkcjach w kodzie, modułach w aplikacji, wierszach, wskaźnikach instrukcji (IP) i typach.

 Próg można ustawić w celu zmniejszenia szumu i odfiltrowania danych w widoku tabeli wierszy, które nie uległy zmianie o określoną wartość.

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Aby utworzyć widok pliku porównania dla projektu w Eksplorator wydajności

1. W **Eksplorator wydajności** w obszarze **raporty** wybierz pozycję. *VSP* lub. *vsps* plik raportu, który ma być używany jako wartości odniesienia do porównania.

2. Wybierz pozycję. *VSP* lub. *vsps* pliki raportów, które chcesz porównać.

3. Kliknij prawym przyciskiem myszy jeden z wybranych plików, a następnie kliknij polecenie **PORÓWNAJ raporty**.

### <a name="to-compare-values"></a>Aby porównać wartości

1. Wybierz kartę **raport porównawczy** w oknie widok raportu.

2. Z listy rozwijanej **tabela** wybierz jedną z funkcji lub modułów do porównania.

3. Z listy rozwijanej **kolumna** wybierz wartość, którą chcesz porównać.

4. obowiązkowe Wpisz wartość **progu**.

5. Kliknij pozycję **Zastosuj**.

### <a name="to-compare-report-files"></a>Aby porównać pliki raportów

1. W menu **Analizuj** wybierz opcję **PORÓWNAJ raporty wydajności**.

2. W oknie **Wybieranie plików analizy do porównania** Przeglądaj i wybierz plik analizy **pliku bazowego** (.*VSP* lub. *vsps*) i **plik porównania** (.*VSP* lub. *vsps*).

3. Kliknij przycisk **OK**.
