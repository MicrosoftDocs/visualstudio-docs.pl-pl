---
title: Konsola | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9450254620fff8981aa9330dc41535ec69c0d842
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944142"
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
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)