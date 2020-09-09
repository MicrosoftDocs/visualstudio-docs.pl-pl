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
ms.openlocfilehash: 647f51314d5506e817fa6982aa693b62f62125cf
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599913"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Błąd: Nie można automatycznie rozpocząć wykonywania krok po kroku na serwerze
Błąd:

 Nie można automatycznie wkroczyć do serwera. Debuger nie został powiadomiony przed wykonaniem zdalnej procedury

 Ten błąd może wystąpić, gdy próbujesz przejść do usługi sieci Web (zobacz krok po kroku do [usługi sieci Web XML](/previous-versions/zc57803s(v=vs.100))). Może się tak zdarzyć, gdy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nie zostanie prawidłowo skonfigurowany.

 Możliwe przyczyny są następujące:

- Plik web.config dla aplikacji nie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ustawił debugowania na wartość "true" w (zobacz [tryb debugowania w aplikacjach ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Wersja programu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] została zainstalowana po zainstalowaniu programu Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] należy zainstalować przed Visual Studio. Aby rozwiązać ten problem, użyj **Panelu sterowania systemu Windows > programów i funkcji** w celu naprawy instalacji programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)