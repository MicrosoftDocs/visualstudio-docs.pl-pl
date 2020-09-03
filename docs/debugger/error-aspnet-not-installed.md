---
title: Błąd — ASP.NET nie został zainstalowany | Microsoft Docs
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
ms.openlocfilehash: 3a768a1a3a0295190701cacc9bbf017baee507b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460908"
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

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
