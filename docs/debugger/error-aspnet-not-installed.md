---
title: 'Błąd: ASP.NET nie jest zainstalowany | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 09c10019f4a3efd369398964eb1cf957968b4d10
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976501"
---
# <a name="error-aspnet-not-installed"></a>Błąd: ASP.NET nie jest zainstalowany
Ten błąd występuje, gdy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nie jest poprawnie zainstalowany na komputerze, który chcesz debugować. Może to oznaczać, że [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nigdy nie został zainstalowany lub [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] została zainstalowana jako pierwsza i IIS został zainstalowany później.  
  
### <a name="to-reinstall-aspnet"></a>Ponowna instalacja programu ASP.NET  
  
1. Z poziomu okna wiersza polecenia Uruchom następujące polecenie:  
  
   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
   ```  
  
    gdzie *wersji* reprezentuje numer wersji .NET Framework zainstalowanej na komputerze, na przykład v1.0.370. Można określić framework w wersji, przeszukując `\WINDOWS\Microsoft.NET\Framework` katalogu.  
  
   > [!NOTE]
   >  Windows Server 2003, można zainstalować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] przy użyciu **apletu Dodaj lub usuń programy** w Panelu sterowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
