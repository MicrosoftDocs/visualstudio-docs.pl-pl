---
title: Użytkownik (VSPerfCmd) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7039422a6934eb4dfa007d216fdc0a70e0da32e9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636596"
---
# <a name="user-vsperfcmd"></a>Użytkownik (VSPerfCmd)
**Użytkownika** opcja określa nazwę domeny i użytkownika konta, które jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika, na **procesy** kartę w Menedżerze zadań Windows.

 **Użytkownika** opcji można określić tylko w wierszu polecenia, który zawiera także **Start** opcji.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parametry
 `Domain` Nazwa domeny użytkownika.

 `UserName` Nazwa użytkownika.

## <a name="required-options"></a>Wymagane opcje
 **Użytkownika** opcja może być używana tylko z **Start** opcji.

 **Początek:** `Method` Inicjuje profiler do określonej metody profilowania.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano użycie **użytkownika** opcji.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)