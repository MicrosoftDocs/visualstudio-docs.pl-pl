---
title: Konsola | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e1870870301b4f9812ea9a16fe6089fd72028b8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987430"
---
# <a name="console"></a>Konsola
VSPerfCmd.exe **konsoli** opcji uruchomi aplikację określoną w nowym oknie wiersza polecenia. **Konsola** należy używać tylko przy użyciu narzędzia VSPerfCmd **Uruchom** opcji. Jeśli aplikacja nie jest aplikacją wiersza polecenia **konsoli** nie ma wpływu.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="required-options"></a>Wymagane opcje  
 **Konsola** można określić tylko w wierszu polecenia, który zawiera także **Uruchom** opcji.  
  
 **Uruchom:** `AppName`  
 Uruchamia program profilujący i aplikacji, określonej przez `AppName`.  
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)