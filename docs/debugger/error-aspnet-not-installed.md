---
title: Platforma ASP.NET nie jest zainstalowana
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 1c4138b1f3d102e235bb03ebcfd5a80808d8762c
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852800"
---
# <a name="error-aspnet-not-installed"></a>Błąd: ASP.NET nie jest zainstalowany
Ten błąd występuje, gdy program [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nie jest prawidłowo zainstalowany na komputerze, który próbujesz debugować. Może to oznaczać, że [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nigdy nie został zainstalowany lub wcześniej zainstalowany [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] program IIS został zainstalowany później.

### <a name="to-reinstall-aspnet"></a>Aby ponownie zainstalować ASP.NET

1. W oknie wiersza polecenia Uruchom następujące polecenie:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    gdzie *wersja* reprezentuje numer wersji .NET Framework zainstalowanej na komputerze, na przykład v 1.0.370. Możesz określić wersję platformy, przeglądając `\WINDOWS\Microsoft.NET\Framework` katalog.

   > [!NOTE]
   > W systemie Windows Server 2003 można zainstalować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] za pomocą apletu **Dodaj lub usuń programy** w panelu sterowania.

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
