---
title: Błąd — nie można automatycznie wkroczyć do serwera | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: fd85d5564bb6f8a0a5f4ead8c5a4ef8e1be48598
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460289"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Błąd: Nie można automatycznie rozpocząć wykonywania krok po kroku na serwerze
Błąd:

 Nie można automatycznie wkroczyć do serwera. Debuger nie został powiadomiony przed wykonaniem zdalnej procedury

 Ten błąd może wystąpić, gdy próbujesz przejść do usługi sieci Web (zobacz krok po kroku do [usługi sieci Web XML](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Może się tak zdarzyć, gdy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nie zostanie prawidłowo skonfigurowany.

 Możliwe przyczyny są następujące:

- Plik web.config dla aplikacji nie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ustawił debugowania na wartość "true" w (zobacz [tryb debugowania w aplikacjach ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Wersja programu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] została zainstalowana po zainstalowaniu programu Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]należy zainstalować przed Visual Studio. Aby rozwiązać ten problem, użyj **Panelu sterowania systemu Windows > programów i funkcji** w celu naprawy instalacji programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)