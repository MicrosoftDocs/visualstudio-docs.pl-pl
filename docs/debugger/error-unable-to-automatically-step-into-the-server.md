---
title: 'Błąd: nie można automatycznie wkroczyć do serwera | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34b298b299bb4911bfe64b362d94c3e90ecfa585
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736873"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Błąd: Nie można automatycznie rozpocząć wykonywania krok po kroku na serwerze
Błąd:

 Nie można automatycznie wkroczyć do serwera. Debuger nie został powiadomiony przed wykonaniem zdalnej procedury

 Ten błąd może wystąpić, gdy próbujesz przejść do usługi sieci Web (zobacz krok po kroku do [usługi sieci Web XML](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Może się to zdarzyć, gdy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nie jest prawidłowo skonfigurowany.

 Możliwe przyczyny są następujące:

- Plik Web. config aplikacji [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nie ustawił debugowania na wartość "true" w (zobacz [tryb debugowania w aplikacjach ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Wersja [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] została zainstalowana po zainstalowaniu programu Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] należy zainstalować przed Visual Studio. Aby rozwiązać ten problem, użyj **Panelu sterowania systemu Windows > programów i funkcji** w celu naprawy instalacji programu Visual Studio.

## <a name="see-also"></a>Zobacz także
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)