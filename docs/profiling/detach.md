---
title: Odłącz | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad079afe3202f7261f8de60d0616df57715e6717
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919060"
---
# <a name="detach"></a>Odłącz
VSPerfCmd.exe **Odłącz** opcji rozłącza profiler określone procesy lub wszystkich procesów, jeśli żaden nie jest określony. Profilowanie musi zostać zainicjowany przy użyciu metody próbkowania.  
  
 Profilowanie, który został uruchomiony z oboma **Uruchom** lub **Attach** opcji może zostać rozłączona za pomocą **Odłącz**. Program profilujący może być reattched przy użyciu kolejnych **Dołącz** poleceń.  
  
 **Odłącz** nie zamknąć plik danych profilowania. Użyj **zamknięcia** opcję, aby zakończyć, profilowanie i zamknąć plik danych.  
  
> [!NOTE]
>  Jeśli **Start** została określona opcja **Crosssession** opcji wszelkie wywołania **VSPerfCmd /Attach** lub **VSPerfCmd/detach** musi również określić **Crosssession**.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
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
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)