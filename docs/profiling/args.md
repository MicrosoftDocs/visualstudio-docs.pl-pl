---
title: Args | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b6d01a95b7e0872d6bb36c6d9f3917bc6a05b3b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779821"
---
# <a name="args"></a>Args
Opcja VSPerfCmd.exe **Args** określa listę argumentów, które są przekazywane do aplikacji docelowej podpokazyju **Uruchamianie.**

 **Args** może być używany tylko wtedy, gdy **uruchamianie** jest również określone w wierszu polecenia. **Args** jest opcjonalne, gdy określono **Uruchamianie.**

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Parametry
 `Arguments`Lista argumentów do docelowej aplikacji polecenia **Uruchom.**

## <a name="required-options"></a>Wymagane opcje
 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna profilowanie za pomocą metody próbkowania.

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto opcji **Args** do przekazywania argumentów do pliku TestApp.exe.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie ASP.NET aplikacje internetowe](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
