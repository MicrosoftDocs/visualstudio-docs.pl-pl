---
title: Okno Eksplorator wydajności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a370ae802408ecc821de4cd15824f9d1fca42b75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195525"
---
# <a name="performance-explorer-window"></a>Okno Eksploratora wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **Eksplorator wydajności** w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE) umożliwia konfigurowanie i uruchamianie sesji wydajności przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="performance-explorer-toolbar"></a>Eksplorator wydajności pasek narzędzi  
 Na pasku narzędzi **Eksplorator wydajności** są dostępne następujące opcje:  
  
- **Uruchom Kreatora wydajności** — wyświetla Kreatora wydajności, aby dodać nową sesję wydajności do okna Eksplorator wydajności.  
  
- **Nowa sesja wydajności** — dodaje pustą sesję wydajności do okna Eksplorator wydajności.  
  
- **Uruchom** — lista przycisków poleceń **uruchamiania** umożliwia uruchomienie aplikacji docelowej, która ma natychmiastowe włączenie profilowania (**Uruchom z profilowania**) lub profilowanie zawieszone (**Uruchom z wstrzymanym profilem**).  
  
- **Metoda** — określa, czy metoda profilowania sesji jest próbką lub Instrumentacją.  
  
- **Zatrzymaj** — natychmiast zamyka aplikację docelową i Profiler.  
  
- **Dołącz/Odłącz** — wyświetla okno dialogowe **Dołącz profiler do procesu** , aby wybrać uruchomiony proces, do którego ma zostać dołączony Profiler.  
  
## <a name="performance-explorer-window"></a>Okno Eksploratora wydajności  
 Okno **Eksplorator wydajności** zawiera kontrolkę drzewa, która wyświetla pliki binarne i dane raportów z co najmniej jednej sesji wydajności.  
  
- **Nazwa sesji** — katalog główny kontrolki drzewa zawiera nazwę sesji. Kliknij prawym przyciskiem myszy nazwę sesji, aby ustawić właściwości sesji lub uruchomić aplikację docelową oraz Profiler.  
  
- **Elementy docelowe** — wyświetla nazwy plików binarnych, które mają być profilowane w sesji. Kliknij prawym przyciskiem myszy **obiekt docelowy** , aby dodać lub usunąć plik binarny, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekt lub witrynę sieci Web. Kliknij prawym przyciskiem myszy nazwę docelową, aby ustawić właściwości dla poszczególnych plików binarnych.  
  
- **Raporty** — wyświetla nazwy plików danych profilera, które są generowane dla danej sesji. Kliknij prawym przyciskiem myszy pozycję **raporty** , aby dodać istniejący raport lub porównać dwa pliki danych profilera. Kliknij prawym przyciskiem myszy nazwę raportu, aby otworzyć, usunąć lub wyeksportować plik danych profilera.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)
