---
title: Zbieranie danych o interakcji między warstwami | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a20266c870316be9b6be67e661d13eb4e6fdbaee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568050"
---
# <a name="collecting-tier-interaction-data"></a>Zbieranie danych o interakcji między warstwami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilowanie interakcji między warstwami zawiera dodatkowe informacje o czasach wykonywania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pomocą usług ADO.NET Services. Dane są zbierane tylko dla wywołań funkcji synchronicznych.  
  
 **Wersje programu Visual Studio**  
  
 Dane profilowania interakcji między warstwami można zbierać przy użyciu Visual Studio Ultimate, Visual Studio Premium lub Visual Studio Professional. Jednak dane profilowania interakcji między warstwami mogą być wyświetlane tylko w programie VS Ultimate i VS Premium.  
  
 **Windows 8 i Windows Server 2012**  
  
 Aby zbierać dane interakcji warstwy w aplikacjach klasycznych systemu Windows 8 i aplikacjach systemu Windows Server 2012, należy użyć metody instrumentacji. Nie można zbierać danych o interakcji między warstwami dla aplikacji ze sklepu Windows. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Możesz uwzględnić dane interakcji warstwy we wszystkich metodach profilowania w innej obsługiwanej wersji systemu Windows.  
  
 **Kreator Wydajności**  
  
 Ze względu na usterkę w Kreatorze wydajności należy dodać opcję zbierania danych interakcja warstwy do przebiegu profilowania z Eksplorator wydajności. Należy również dodać projekt, plik wykonywalny lub witrynę sieci Web do węzła docelowego Eksplorator wydajności.  
  
### <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Aby dodać dane interakcji warstwy do przebiegu profilowania przy użyciu stron właściwości sesji wydajności  
  
1. W Eksplorator wydajności, wybierz **Właściwości** z menu kontekstowego.  
  
2. Wybierz stronę **interakcje warstwy** , a następnie zaznacz pole wyboru **Włącz profilowanie interakcji między warstwami** .  
  
3. W Eksplorator wydajności Wybierz węzeł **targets** , a następnie określ projekt, plik wykonywalny lub witrynę sieci Web, którą chcesz profilować.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok interakcji warstwowych](../profiling/tier-interactions-view.md)
