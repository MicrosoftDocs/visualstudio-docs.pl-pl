---
title: Konsola | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e947fb28c92323f0d4d66c697c272699fc63450e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161312"
---
# <a name="console"></a>Konsola
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja **konsola** VSPerfCmd.exe uruchamia określoną aplikację w nowym oknie wiersza polecenia. **Konsoli** programu można używać tylko z opcją **uruchamiania** VSPerfCmd. Jeśli aplikacja nie jest aplikacją wiersza polecenia, **konsola** nie ma żadnego efektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="required-options"></a>Wymagane opcje  
 **Konsolę** można określić tylko w wierszu polecenia, który zawiera również opcję **uruchamiania** .  
  
 **Uruchom:**`AppName`  
 Uruchamia program profilujący i aplikację określoną przez `AppName` .  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
