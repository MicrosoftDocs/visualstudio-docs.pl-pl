---
title: 'Błąd: nie można automatycznie wkroczyć do serwera | Microsoft Docs'
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
ms.openlocfilehash: c8dcb8fa757f1cccf2f3aef6c2520e0c61da0b9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682676"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Błąd: Nie można automatycznie rozpocząć wykonywania krok po kroku na serwerze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Błąd:  
  
 Nie można automatycznie wkroczyć do serwera. Debuger nie został powiadomiony przed wykonaniem zdalnej procedury  
  
 Ten błąd może wystąpić, gdy próbujesz przejść do usługi sieci Web (zobacz krok po kroku do [usługi sieci Web XML](https://msdn.microsoft.com/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Może się tak zdarzyć, gdy [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nie zostanie prawidłowo skonfigurowany.  
  
 Możliwe przyczyny są następujące:  
  
- Plik web.config dla aplikacji nie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ustawił debugowania na wartość "true" w (zobacz [tryb debugowania w aplikacjach ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
- Wersja programu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] została zainstalowana po zainstalowaniu programu Visual Studio. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] należy zainstalować przed Visual Studio. Aby rozwiązać ten problem, użyj **Panelu sterowania**systemu Windows, **programów i funkcji** do naprawy instalacji programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)
