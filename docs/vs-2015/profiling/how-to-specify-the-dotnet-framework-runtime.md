---
title: 'Instrukcje: Określanie środowiska wykonawczego .NET Framework | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203412"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Instrukcje: Określanie środowiska uruchomieniowego programu .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wraz z wydaniem [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], aplikacje mogą się składać z modułów, które zostały utworzone przy użyciu różnych wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] środowiska wykonawczego. Domyślnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools profilowanie pierwszego środowiska uruchomieniowego, który jest ładowany przez aplikację. Można określić czasu wykonywania, aby przeprowadzić profilowanie, podczas uruchamiania aplikacji przy użyciu profilera i dołączenia programu profilującego do aplikacji już uruchomionego.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Aby określić środowiska wykonawczego .NET Framework do profilowania, podczas uruchamiania aplikacji przy użyciu profilera  
  
1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, kliknij przycisk **właściwości**, a następnie kliknij przycisk **zaawansowane**.  
  
     **Docelowa wersja środowiska CLR** liście wyświetlane są **automatyczne** oraz wersje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] środowiska uruchomieniowego, które są zainstalowane na komputerze.  
  
2. Wykonaj jedną z następujących czynności:  
  
    - Kliknij wersję środowiska CLR, które powinny być profilowane.  
  
    - Kliknij przycisk **automatyczne** profilowanie pierwszej wersji, który jest ładowany przez aplikację.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Aby określić środowiska wykonawczego .NET Framework do profilowania, podczas dołączania profilera do aplikacji  
  
1. W menu Analizuj wskaż Profiler, a następnie kliknij przycisk Attach/Detach.  
  
2. Na dołączyć Profiler do procesu, okno dialogowe kliknij proces, który chcesz profilować.  
  
     **Docelowa wersja środowiska CLR** pole z listy s **automatyczne** oraz wersje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] środowiska uruchomieniowego, które są zainstalowane na komputerze.  
  
3. Wykonaj jedną z następujących czynności:  
  
    - Kliknij wersję środowiska CLR, które powinny być profilowane.  
  
    - Kliknij przycisk **automatyczne** do profilowania, wersji, który jest ładowany, gdy program profilujący jest dołączony do aplikacji.
