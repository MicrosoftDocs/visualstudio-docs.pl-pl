---
title: Użytkownik (VSPerfCmd) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7dbb1a155e8e0ffd2690b5850299b8075a63ea3d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779964"
---
# <a name="user-vsperfcmd"></a>Użytkownik (VSPerfCmd)
**Opcja Użytkownik** określa domenę i nazwę użytkownika konta, które jest właścicielem procesu profilowanego. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie **Procesy** w Menedżerze zadań systemu Windows.

 Opcję **Użytkownik** można określić tylko w wierszu polecenia, który zawiera również opcję **Start.**

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parametry
 `Domain`Nazwa domeny użytkownika.

 `UserName`Nazwa użytkownika.

## <a name="required-options"></a>Wymagane opcje
 **Opcji Użytkownik** można używać tylko z opcją **Start.**

 **Start:** `Method` Inicjuje profiler do określonej metody profilowania.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje użycie opcji **Użytkownik.**

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
