---
title: Konsola | Microsoft Docs
description: Użyj opcji konsoli programu VSPerfCmd.exe, aby uruchomić określoną aplikację w nowym oknie wiersza polecenia. Należy użyć go z opcją uruchomienia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 93c39bfb503bec9858e33b7acf04e0f0433264b9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720908"
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

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
