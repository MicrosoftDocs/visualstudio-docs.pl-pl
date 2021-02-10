---
title: Konsola | Microsoft Docs
description: Użyj opcji konsoli programu VSPerfCmd.exe, aby uruchomić określoną aplikację w nowym oknie wiersza polecenia. Należy użyć go z opcją uruchomienia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 242a5234c2b7368a992676e12ecbdcd5ea36219f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955414"
---
# <a name="console"></a>Konsola
Opcja **konsola** VSPerfCmd.exe uruchamia określoną aplikację w nowym oknie wiersza polecenia. **Konsoli** programu można używać tylko z opcją **uruchamiania** VSPerfCmd. Jeśli aplikacja nie jest aplikacją wiersza polecenia, **konsola** nie ma żadnego efektu.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="required-options"></a>Wymagane opcje
 **Konsolę** można określić tylko w wierszu polecenia, który zawiera również opcję **uruchamiania** .

 **Uruchom:** `AppName` Uruchamia program profilujący i aplikację określoną przez `AppName` .

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
