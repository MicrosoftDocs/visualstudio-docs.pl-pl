---
title: GlobalOn i GlobalOff | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 518f41557809cdeaaae9f9e1ac79e3797a854395
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776969"
---
# <a name="globalon-and-globaloff"></a>GlobalOn i GlobalOff
Opcje *vsPerfCmd.exe* **GlobalOff** i **GlobalOn** wstrzymują i wznawiają profilowanie wszystkich procesów i wątków w sesji profilowania wiersza polecenia.

 **GlobalOn** i **GlobalOff** można określić jako jedyne opcje w wierszu polecenia *VSPerfCmd.exe* lub dołączyć je do wierszy poleceń, które zawierają również opcje **Start,** **Launch**lub **Attach.**

 **GlobalOn** i **GlobalOff** można również łączyć z opcjami **ProcessOn**, **ProcessOff**, **ThreadOn**i **ThreadOff.**

 **GlobalOn** i **GlobalOff** opcje interakcji z **ProcessOn** i **ProcessOff** opcje, które kontrolują zbieranie danych dla określonego procesu i **ThreadOn** i **ThreadOff** opcje, które kontrolują zbieranie danych dla określonego wątku.

 **GlobalOff** i **GlobalOn** opcje mają również wpływ na globalną liczbę start/stop, który jest manipulowany przez funkcje interfejsu API profilera.

- **GlobalOff** natychmiast ustawia globalną liczbę start/stop na 0 i w związku z tym wstrzymuje profilowanie.

- **GlobalOn** natychmiast ustawia globalną liczbę start/stop na 1 i w związku z tym wznawia profilowanie.

  Aby uzyskać więcej informacji, zobacz [Narzędzia profilowania interfejsów API](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /{GlobalOff|GlobalOn}

VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]

VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="valid-options"></a>Prawidłowe opcje
 **GlobalOn** i **GlobalOff** można określić w wierszach poleceń, które również zawierają następujące opcje.

 **Start:** `Method` Inicjuje sesję profilera wiersza polecenia i ustawia określoną metodę profilowania.

 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna profilowanie za pomocą metody próbkowania.

 **Dołącz:** `PID` Rozpoczyna profilowanie określonego procesu.

 {**ProcessOff**&#124;**ProcessOn**} **:** `PID` Zatrzymuje lub rozpoczyna profilowanie dla określonego procesu.

 {**ThreadOff**&#124;**ThreadOn**} **:** `TID` Zatrzymuje lub rozpoczyna profilowanie dla określonego procesu (tylko metoda instrumentacji).

## <a name="example"></a>Przykład
 W tym przykładzie **GlobalOff** i **GlobalOn** opcje są używane w celu uniknięcia zbierania danych profilowania do uruchamiania aplikacji i zamykania.

```cmd
; Initialize the profiler with profiling stopped.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff
; Start an instrumented application and wait for it to warm up.
; Start profiling.
VSPerfCmd.exe /GlobalOn
; Exercise the application functionality that you want to profile.
; Stop profiling.
VSPerfCmd.exe /GlobalOff
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
