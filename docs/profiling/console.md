---
title: Konsola | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6ec56665b546f962e8b3f4fd35460715390aee30
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777819"
---
# <a name="console"></a>Konsola programu
Opcja **konsoli** VSPerfCmd. exe uruchamia określoną aplikację w nowym oknie wiersza polecenia. **Konsoli** programu można używać tylko z opcją **uruchamiania** VSPerfCmd. Jeśli aplikacja nie jest aplikacją wiersza polecenia, **konsola** nie ma żadnego efektu.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="required-options"></a>Wymagane opcje
 **Konsolę** można określić tylko w wierszu polecenia, który zawiera również opcję **uruchamiania** .

 **Uruchom:** `AppName` uruchamia Profiler i aplikację określoną przez `AppName`.

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
