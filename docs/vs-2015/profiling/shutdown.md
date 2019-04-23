---
title: Zamknięcie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbbbd27cfe7d720349592050419f5c73d1843c70
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60115409"
---
# <a name="shutdown"></a>Zamykanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Zamknięcia** opcji oczekuje żadnego obecnie profilowane procesu, aby zakończyć lub odłączyć, a następnie wyłącza profilera i zamyka plik danych profilowania. **Zamknięcia** opcja musi być ostatnie polecenie uruchomienia profilowania.  
  
 Jeśli nie określono parametr limitu czasu, **zamknięcia** opcja będzie czekać w nieskończoność. Jeśli określono parametr limitu czasu, opcja zwraca po określonej liczbie sekund bez konieczności wyłączania program profilujący lub zamykania pliku danych.  
  
 **Zamknięcia** opcja musi być jedyną opcją, określone w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Parametry  
`Timeout`  
- (Opcjonalnie) Jeśli zostanie określony, opcja zwraca po określonej liczbie sekund bez konieczności wyłączania program profilujący lub zamykania pliku danych profilowania.  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
