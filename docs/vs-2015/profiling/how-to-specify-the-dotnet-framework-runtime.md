---
title: 'Instrukcje: Określanie środowiska uruchomieniowego .NET Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f631e8639c1004fa2cb005da3b6c8bcb27f1a9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203412"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Instrukcje: Określanie środowiska uruchomieniowego .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W wersji programu [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] aplikacje mogą składać się z modułów, które zostały skompilowane przy użyciu różnych wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] czasu wykonywania. Domyślnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania profiluje pierwsze środowisko uruchomieniowe, które jest ładowane przez aplikację. Możesz określić czas wykonywania do profilowania, gdy uruchamiasz aplikację za pomocą profilera i po dołączeniu profilera do już uruchomionej aplikacji.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Aby określić .NET Framework czas wykonywania do profilowania podczas uruchamiania aplikacji za pomocą profilera  
  
1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy sesję wydajności, kliknij polecenie **Właściwości**, a następnie kliknij przycisk **Zaawansowane**.  
  
     Pole listy **docelowa wersja środowiska CLR** zawiera **Automatyczne** i wersje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] środowiska uruchomieniowego, które są zainstalowane na komputerze.  
  
2. Wykonaj jedną z następujących czynności:  
  
    - Kliknij wersję środowiska CLR, które chcesz profilować.  
  
    - Kliknij pozycję **Automatyczne** , aby profilować pierwszą wersję, która jest ładowana przez aplikację.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Aby określić .NET Framework czasie wykonywania do profilowania podczas dołączania profilera do aplikacji  
  
1. W menu Analizuj wskaż polecenie Profiler, a następnie kliknij pozycję Dołącz/Odłącz.  
  
2. W oknie dialogowym Dołącz profiler do procesu kliknij proces, który chcesz profilować.  
  
     Pole listy **docelowej wersji środowiska CLR** — **Automatyczne** i wersje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] środowiska uruchomieniowego, które są zainstalowane na komputerze.  
  
3. Wykonaj jedną z następujących czynności:  
  
    - Kliknij wersję środowiska CLR, które chcesz profilować.  
  
    - Kliknij pozycję **Automatyczne** , aby profilować wersję załadowana podczas dołączania profilera do aplikacji.
