---
title: 'Instrukcje: Zbieranie danych licznika Windows | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2c3e4a9cffd81561af39cef5eb88f4a7745b2dad
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753419"
---
# <a name="how-to-collect-windows-counter-data"></a>Instrukcje: Zbieranie danych liczników systemu Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Liczniki Windows są liczniki wydajności systemu, które mogą być zbierane podczas profilowania w ustalonych odstępach czasu. W widoku znaczniki raportu narzędzi profilowania z wiersza jest oznaczona etykietą **AutoMark** dla każdego interwału zbierania. Wiersz zawiera kolumny, które opisują wartości licznika wydajności, w tym odstępach czasu. Aby ograniczyć analizę do okresu czasu między dwoma określonymi znacznikami, zaznacz znaki, kliknij prawym przyciskiem myszy, a następnie wybierz **Filtruj wg** ->  **znaczniki** z menu skrótów.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-collect-windows-counter-data"></a>Aby zebrać dane Windows  
  
1.  W Eksploratorze wydajności, kliknij prawym przyciskiem myszy sesję, dla której chcesz skonfigurować liczniki Windows, a następnie wybierz pozycję **właściwości**.  
  
2.  W **stron właściwości**, kliknij przycisk **liczniki Windows**.  
  
3.  Wybierz **zbierania liczników Windows** pole wyboru.  
  
4.  W **interwał zbierania (MS)** tekstu wpisz przedział czasu.  
  
5.  Wybierz kategorię z **kategorii licznika** listy rozwijanej.  
  
6.  Wybierz domyślne wystąpienie z **wystąpienia** listy rozwijanej.  
  
7.  Wybierz liczniki, które chcesz użyć podczas profilowania aplikacji.  
  
8.  Kliknij przycisk **zastosowania.**  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)   
 [Liczniki procesora CPU i systemu Windows](../profiling/cpu-and-windows-counters.md)
