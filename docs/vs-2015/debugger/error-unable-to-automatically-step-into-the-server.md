---
title: 'Błąd: Nie można automatycznie krok po kroku serwera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: fca696fe9afc979d6775c5b2e97eebb5d82c266c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747818"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Błąd: Nie można automatycznie rozpocząć wykonywania krok po kroku na serwerze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Odczytuje błąd:  
  
 Nie można automatycznie krok po kroku do serwera. Debuger nie został powiadomiony, zanim była wykonywana ta procedura zdalnego  
  
 Ten błąd może wystąpić, gdy chcesz wejść do usługi sieci web (zobacz [przechodzenie krok po kroku w usłudze internetowej XML](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Może wystąpić, gdy [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nie jest skonfigurowany prawidłowo.  
  
 Możliwe przyczyny to:  
  
-   Plik web.config dla Twojego [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji nie powoduje ustawienia debugowania na wartość "true" (zobacz [tryb debugowania w aplikacjach ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Wersja [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] został zainstalowany po zainstalowaniu programu Visual Studio. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] powinien zostać zainstalowany przed Visual Studio. Aby rozwiązać ten problem, należy użyć Windows **Panelu sterowania**, **programy i funkcje** naprawić instalację programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)



