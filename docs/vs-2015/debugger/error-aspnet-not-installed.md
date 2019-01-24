---
title: 'Błąd: ASP.NET nie jest zainstalowany | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 31268b94ab632e598badcba3def387ef1fc2ba1d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54752203"
---
# <a name="error-aspnet-not-installed"></a>Błąd: ASP.NET nie jest zainstalowany
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten błąd występuje, gdy [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nie jest poprawnie zainstalowany na komputerze, który chcesz debugować. Może to oznaczać, że [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nigdy nie został zainstalowany lub [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] została zainstalowana jako pierwsza i IIS został zainstalowany później.  
  
### <a name="to-reinstall-aspnet"></a>Ponowna instalacja programu ASP.NET  
  
1.  Z poziomu okna wiersza polecenia Uruchom następujące polecenie:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     gdzie *wersji* reprezentuje numer wersji .NET Framework zainstalowanej na komputerze, na przykład v1.0.370. Można określić framework w wersji, przeszukując `\WINDOWS\Microsoft.NET\Framework` katalogu.  
  
    > [!NOTE]
    >  Windows Server 2003, można zainstalować [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] przy użyciu **apletu Dodaj lub usuń programy** w Panelu sterowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
