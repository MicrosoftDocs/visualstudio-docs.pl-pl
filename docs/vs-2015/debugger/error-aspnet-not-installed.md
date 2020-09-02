---
title: 'Błąd: nie zainstalowano ASP.NET | Microsoft Docs'
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
ms.openlocfilehash: 2198ed401f714353be2dd18846dd527cc433e695
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64823730"
---
# <a name="error-aspnet-not-installed"></a>Błąd: ASP.NET nie jest zainstalowany
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten błąd występuje, gdy program [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nie jest prawidłowo zainstalowany na komputerze, który próbujesz debugować. Może to oznaczać, że [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nigdy nie został zainstalowany lub wcześniej zainstalowany [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] program IIS został zainstalowany później.  
  
### <a name="to-reinstall-aspnet"></a>Aby ponownie zainstalować ASP.NET  
  
1. W oknie wiersza polecenia Uruchom następujące polecenie:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     gdzie *wersja* reprezentuje numer wersji .NET Framework zainstalowanej na komputerze, na przykład v 1.0.370. Możesz określić wersję platformy, przeglądając `\WINDOWS\Microsoft.NET\Framework` katalog.  
  
    > [!NOTE]
    > W systemie Windows Server 2003 można zainstalować [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] za pomocą apletu **Dodaj lub usuń programy** w panelu sterowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
