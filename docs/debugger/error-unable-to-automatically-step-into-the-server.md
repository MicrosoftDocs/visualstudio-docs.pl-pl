---
title: Nie można automatycznie wkroczyć do serwera | Microsoft Docs
description: Nie można automatycznie wkroczyć do serwera. Debuger nie został powiadomiony przed wykonaniem procedury zdalnej.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a374afef2dea92fbad72c45e35ca06904d75cbbe
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146486"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Błąd: Nie można automatycznie rozpocząć wykonywania krok po kroku na serwerze
Błąd:

 Nie można automatycznie wkroczyć do serwera. Debuger nie został powiadomiony przed wykonaniem zdalnej procedury

 Ten błąd może wystąpić, gdy próbujesz przejść do usługi sieci Web (zobacz krok po kroku do [usługi sieci Web XML](/previous-versions/zc57803s(v=vs.100))). Może się tak zdarzyć, gdy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nie zostanie prawidłowo skonfigurowany.

 Możliwe przyczyny są następujące:

- Plik web.config dla aplikacji nie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ustawił debugowania na wartość "true" w (zobacz [tryb debugowania w aplikacjach ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Wersja programu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] została zainstalowana po zainstalowaniu programu Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] należy zainstalować przed Visual Studio. Aby rozwiązać ten problem, użyj **Panelu sterowania systemu Windows > programów i funkcji** w celu naprawy instalacji programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
