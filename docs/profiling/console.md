---
title: Konsola | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777819"
---
# <a name="console"></a>Konsola
**Opcja** konsoli vsPerfCmd.exe uruchamia określoną aplikację w nowym oknie wiersza polecenia. **Konsoli** można używać tylko z opcją VSPerfCmd **Launch.** Jeśli aplikacja nie jest aplikacją wiersza polecenia, **konsola** nie ma wpływu.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="required-options"></a>Wymagane opcje
 **Konsolę** można określić tylko w wierszu polecenia, który zawiera również opcję **Uruchom.**

 **Uruchom:** `AppName` Uruchamia profiler i aplikację `AppName`określoną przez .

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
