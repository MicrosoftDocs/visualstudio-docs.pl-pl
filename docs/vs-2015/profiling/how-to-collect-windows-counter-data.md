---
title: 'Instrukcje: zbieranie danych licznika systemu Windows | Microsoft Docs'
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
ms.openlocfilehash: 9743fa7defbbf3321636d2ba4799454713a647db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64836779"
---
# <a name="how-to-collect-windows-counter-data"></a>Porady: zbieranie danych liczników systemu Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Liczniki systemu Windows są licznikami wydajności systemu, które można zbierać w ustalonych odstępach czasu podczas profilowania. W widoku znaczniki raportu narzędzia profilowania wiersz ma etykietę **autoznaczników** dla każdego interwału kolekcji. Wiersz zawiera kolumny, które opisują wartości licznika wydajności w tym interwale. Aby ograniczyć analizę do okresu między dwoma określonymi znakami, zaznacz znaczniki, kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **Filtruj według**  ->   **znaczników** z menu skrótów.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-collect-windows-counter-data"></a>Aby zebrać dane liczników systemu Windows  
  
1. W Eksplorator wydajności kliknij prawym przyciskiem myszy sesję, dla której chcesz skonfigurować liczniki systemu Windows, a następnie wybierz pozycję **Właściwości**.  
  
2. Na **stronie właściwości**kliknij pozycję **liczniki systemu Windows**.  
  
3. Zaznacz pole wyboru **Zbierz liczniki systemu Windows** .  
  
4. W polu tekstowym **Interwał kolekcji (MS)** wpisz przedział czasu.  
  
5. Wybierz kategorię z listy rozwijanej **Kategoria licznika** .  
  
6. Wybierz wystąpienie z listy rozwijanej **wystąpienie** .  
  
7. Wybierz liczniki, które mają być używane podczas profilowania aplikacji.  
  
8. Kliknij przycisk **Zastosuj.**  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)   
 [Liczniki procesora i systemu Windows](../profiling/cpu-and-windows-counters.md)
