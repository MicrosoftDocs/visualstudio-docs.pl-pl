---
title: 'Błąd: nie zainstalowano ASP.NET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 7d754cc2bb7931cdcbdb42abeddd554390ba320c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737917"
---
# <a name="error-aspnet-not-installed"></a>Błąd: ASP.NET nie jest zainstalowany
Ten błąd występuje, gdy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nie jest prawidłowo zainstalowany na komputerze, który próbujesz debugować. Może to oznaczać, że nie zainstalowano jeszcze [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] lub [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] został on zainstalowany w pierwszej kolejności, a usługi IIS zostały zainstalowane później.

### <a name="to-reinstall-aspnet"></a>Aby ponownie zainstalować ASP.NET

1. W oknie wiersza polecenia Uruchom następujące polecenie:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    gdzie *wersja* reprezentuje numer wersji .NET Framework zainstalowanej na komputerze, na przykład v 1.0.370. Możesz określić wersję platformy, przeglądając katalog `\WINDOWS\Microsoft.NET\Framework`.

   > [!NOTE]
   > W systemie Windows Server 2003 można zainstalować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] za pomocą apletu **Dodaj lub usuń programy** w panelu sterowania.

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji internetowych: błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
