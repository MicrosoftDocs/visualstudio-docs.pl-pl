---
title: 'Błąd: serwer sieci Web nie jest prawidłowo skonfigurowany | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3cfbcf127b9951ddfce1d3db8fe1177087b0350a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918501"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Błąd: Serwer sieci Web nie jest prawidłowo skonfigurowany
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możliwe przyczyny tego błędu to:  
  
- Podjęto próbę debugowania aplikacji sieci Web platformy .NET, która została skopiowana na inny komputer, została zmieniona ręcznie lub przeniesiona.  
  
- Brak wystarczającej liczby połączeń IIS. Aby uzyskać więcej informacji na temat wdrażania witryny sieci Web w usługach IIS, zobacz [Tworzenie witryny sieci Web](/iis/get-started/getting-started-with-iis/create-a-web-site).  
  
- Jeśli próbujesz debugować aplikację ASP.NET, zobacz [Publikowanie w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html) , aby uzyskać instrukcje dotyczące wdrażania na komputerze zdalnym z programem IIS 8 lub nowszym albo [zdalne debugowanie ASP.NET na zdalnym komputerze z usługami IIS 7,5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) , aby uzyskać instrukcje dotyczące wdrażania na komputerze zdalnym, na którym działa program IIS 7,5.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
