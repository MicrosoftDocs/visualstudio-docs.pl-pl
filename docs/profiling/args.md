---
title: Args | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 036b13a7fea5d64e23e2b7d5ccbd8a7b17f91176
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62777053"
---
# <a name="args"></a>Args
VSPerfCmd.exe **Args** opcja określa listy argumentów, które są przekazywane do aplikacji docelowej z **Uruchom** podpolecenia.

 **Argumenty** mogą być używane tylko podczas **Uruchom** również jest określona w wierszu polecenia. **Argumenty** jest opcjonalny, gdy **Uruchom** jest określony.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Parametry
 `Arguments` Lista argumentów do aplikacji docelowej z **Uruchom** polecenia.

## <a name="required-options"></a>Wymagane opcje
 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna się profilowanie przy użyciu metody pobierania próbek.

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto **Args** opcję, aby przekazać argumenty do TestApp.exe.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)