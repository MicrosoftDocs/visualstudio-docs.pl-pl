---
title: Argumenty | Microsoft Docs
description: Użyj opcji ARGS VSPerfCmd.exe, aby przekazać listę argumentów do aplikacji docelowej podpolecenia Uruchom.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 44e68822ebd444b8683b85b2df0c49b14d78bcaa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901066"
---
# <a name="args"></a>Args
Opcja VSPerfCmd.exe **args** określa listę argumentów, które są przekazane do aplikacji docelowej podpolecenia **Uruchom** .

 **Argumentów** można używać tylko wtedy, gdy w wierszu polecenia określono również wartość **uruchomienia** . **Argumenty** są opcjonalne w przypadku określenia parametru **Launch** .

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Parametry
 `Arguments` Lista argumentów dla aplikacji docelowej polecenia **uruchamiania** .

## <a name="required-options"></a>Wymagane opcje
 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna profilowanie przy użyciu metody próbkowania.

## <a name="example"></a>Przykład
 Poniższy przykład używa opcji **args** do przekazywania argumentów do TestApp.exe.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
