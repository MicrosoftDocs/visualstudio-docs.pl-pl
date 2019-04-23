---
title: 'Błąd: Nie można automatycznie krok po kroku serwera | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d979b53f4bd5962a01fa5eb1b77cc7c81c68a4a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102422"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Błąd: Nie można automatycznie krok po kroku do serwera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Odczytuje błąd:  
  
 Nie można automatycznie krok po kroku do serwera. Debuger nie został powiadomiony, zanim była wykonywana ta procedura zdalnego  
  
 Ten błąd może wystąpić, gdy chcesz wejść do usługi sieci web (zobacz [przechodzenie krok po kroku w usłudze internetowej XML](http://msdn.microsoft.com/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Może wystąpić, gdy [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nie jest skonfigurowany prawidłowo.  
  
 Możliwe przyczyny to:  
  
- Plik web.config dla Twojego [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji nie powoduje ustawienia debugowania na wartość "true" (zobacz [tryb debugowania w aplikacjach ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
- Wersja [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] został zainstalowany po zainstalowaniu programu Visual Studio. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] powinien zostać zainstalowany przed Visual Studio. Aby rozwiązać ten problem, należy użyć Windows **Panelu sterowania**, **programy i funkcje** naprawić instalację programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)
