---
title: Odłącz | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1262e88055fceef0b2170c304c8ff646eea07205
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793077"
---
# <a name="detach"></a>Odłącz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Odłącz** opcji rozłącza profiler określone procesy lub wszystkich procesów, jeśli żaden nie jest określony. Profilowanie musi zostać zainicjowany przy użyciu metody próbkowania.  
  
 Profilowanie, który został uruchomiony z oboma **Uruchom** lub **Attach** opcji może zostać rozłączona za pomocą **Odłącz**. Program profilujący może być reattched przy użyciu kolejnych **Dołącz** poleceń.  
  
 **Odłącz** nie zamknąć plik danych profilowania. Użyj **zamknięcia** opcję, aby zakończyć, profilowanie i zamknąć plik danych.  
  
> [!NOTE]
>  Jeśli **Start** została określona opcja **Crosssession** opcji wszelkie wywołania **VSPerfCmd /Attach** lub **VSPerfCmd/detach** musi również określić **Crosssession**.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### <a name="parameters"></a>Parametry  
 `PIDs|ProcessNames`  
 `PID` Identyfikator systemu liczbowego jeden lub więcej procesów.  
  
 `ProcessNames` — Nazwa procesu. Jeśli korzystasz z wielu wystąpień procesu o nazwie, wyniki są nieprzewidywalne.  
  
 Wiele procesów należy oddzielić przecinkami.  
  
 Jeśli żaden proces nie zostanie określony, program profilujący jest odłączony od wszystkich profilowanych procesów.  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 Następujące **VSPerfCmd** opcje można łączyć z **Dołącz** opcji w pojedynczym wierszu polecenia.  
  
 **Crosssession**  
 Włącza profilowanie aplikacji w sesjach innych niż sesji logowania. Jeśli wymagane **Start** została określona opcja **Crosssession** opcji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie **Odłącz** polecenie wstrzymuje, profilowanie i **zamknięcia** polecenia zamyka pliku danych profilera.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
