---
title: CrossSession | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 06de982643a08e1af88073dde0fb0a9abc029900
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779457"
---
# <a name="crosssession"></a>CrossSession
Opcja *VSPerfCmd.exe* **CrossSession** umożliwia profilera zbieranie danych z dowolnej sesji konsoli. Opcja **CrossSession** musi być używana z opcją **Start.**

 Zamiast **CrossSession**można użyć skrótu **CS.**

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="valid-options"></a>Prawidłowe opcje
 Aby włączyć profilowanie w innej sesji, opcja **CrossSession** musi być określona za pomocą opcji **Start.** **CrossSession** musi być również określony w każdym kolejnym **VSPerfCmd Dołączyć** i **Odłącz.**

 **Start:** `Method` Opcja **Start** inicjuje profiler do określonej metody profilowania.

 **Dołącz:** _PID_[**,**_PID_] Rozpoczyna profilowanie określonych procesów.

 **Odłącz**[**:**_PID_[,_PID_]] Zatrzymuje profilowanie określonych procesów.

## <a name="example"></a>Przykład
 W tym przykładzie **CrossSession** opcja służy do dołączania do aplikacji, która została uruchomiona w innej sesji konsoli.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
