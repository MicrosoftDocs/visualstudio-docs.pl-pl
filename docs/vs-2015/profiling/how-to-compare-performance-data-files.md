---
title: 'Instrukcje: Porównywanie plików danych dotyczących wydajności | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 185494623e019ef666374bd46e52bca0d58738f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185936"
---
# <a name="how-to-compare-performance-data-files"></a>Instrukcje: Porównywanie plików danych dotyczących wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wyniki dwóch różnych plików danych profilera (. vsp lub. vsps) można porównać, tworząc porównanie ("diff") raportu lub widoku. Porównanie pokazuje różnice, regresje wydajności i ulepszenia, które wystąpiły w jednej sesji profilowania.  
  
 Raport diff przedstawia widok tabeli danych. W tabeli przedstawiono różnice lub zmiany z linii bazowej. Jest to obliczane przez określenie różnicy między starą wartością, wartością bazową i wartością wyniku z nowej analizy.  
  
 Porównania danych profilera mogą opierać się na funkcjach w kodzie, modułach w aplikacji, wierszach, wskaźnikach instrukcji (IP) i typach.  
  
 Próg można ustawić w celu zmniejszenia szumu i odfiltrowania danych w widoku tabeli wierszy, które nie uległy zmianie o określoną wartość.  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Aby utworzyć widok pliku porównania dla projektu w Eksplorator wydajności  
  
1. W **Eksplorator wydajności**w obszarze **raporty**wybierz plik raportu. vsp lub. vsps, który ma być używany jako wartości odniesienia do porównania.  
  
2. Wybierz pliki raportów VSP lub vsps, które chcesz porównać.  
  
3. Kliknij prawym przyciskiem myszy jeden z wybranych plików, a następnie kliknij polecenie **PORÓWNAJ raporty**.  
  
### <a name="to-compare-values"></a>Aby porównać wartości  
  
1. Wybierz kartę **raport porównawczy** w oknie widok raportu.  
  
2. Z listy rozwijanej **tabela** wybierz jedną z funkcji lub modułów do porównania.  
  
3. Z listy rozwijanej **kolumna** wybierz wartość, którą chcesz porównać.  
  
4. obowiązkowe Wpisz wartość **progu**.  
  
5. Kliknij przycisk **Zastosuj**.  
  
### <a name="to-compare-report-files"></a>Aby porównać pliki raportów  
  
1. W menu **Analizuj** wybierz opcję **PORÓWNAJ raporty wydajności**.  
  
2. W oknie **Wybieranie plików analizy do porównania** Przeglądaj i wybierz plik analizy **pliku bazowego** (. vsp lub. vsps) i **plik porównania** (. vsp lub. vsps).  
  
3. Kliknij przycisk **OK**.
