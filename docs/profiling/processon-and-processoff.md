---
title: ProcessOn i ProcessOff | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 62c16c2d578a38187b4a58958466597a5e4d297d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778391"
---
# <a name="processon-and-processoff"></a>ProcessOn i ProcessOff
Podpolecenia programu VSPerfCmd.exe **ProcessOff** i **ProcessOn** wstrzykują i wznawiają profilowanie określonego procesu w sesji profilowania wiersza polecenia. **ProcessOff** zatrzymuje profilowanie procesu i **ProcessOn** rozpoczyna profilowanie procesu.

 W większości przypadków należy określić **ProcessOn** lub **ProcessOff** jako jedyną opcję w wierszu polecenia VSPerfCmd.exe, ale mogą one być również łączone z **globalon,** **GlobalOff**, **ThreadOn**i **ThreadOff** podpoleceń.

 Podpolecenia **ProcessOn** i **ProcessOff** współdziałają z podpoleceniami **GlobalOn** i **GlobalOff,** które kontrolują zbieranie danych dla wszystkich procesów w sesji profilowania wiersza polecenia, a podpolecenia **ThreadOn** i **ThreadOff** kontrolują zbieranie danych dla określonego wątku.

 Podpokazy **ProcessOff** i **ProcessOn** również wpływają na liczbę uruchamiania/zatrzymywania procesu, która jest manipulowana przez funkcje interfejsu API profilera.

- **ProcessOff** natychmiast ustawia licznik uruchamiania/zatrzymywania procesu na 0 i w związku z tym wstrzymuje profilowanie.

- **ProcessOn** natychmiast ustawia licznik uruchamiania/zatrzymywania procesu na 1 i w związku z tym wznawia profilowanie.

  Aby uzyskać więcej informacji, zobacz [interfejsy API narzędzi profilowania](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]

```

#### <a name="parameters"></a>Parametry
 `PID`Identyfikator liczby całkowitej procesu do rozpoczęcia lub zatrzymania. Identyfikatory procesów są wyświetlane na karcie **Proces** Menedżera zadań systemu Windows.

## <a name="required-subcommands"></a>Wymagane podwykazy
 Brak

## <a name="valid-subcommands"></a>Prawidłowe podwykazy
 **ProcessOn** i **ProcessOff** można określić w wierszach poleceń, które zawierają również następujące podpoleczenia.

 **Start:** `Method` Inicjuje sesję profilowania wiersza polecenia i ustawia określoną metodę profilowania.

 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna profilowanie za pomocą metody próbkowania.

 **Dołącz:** `PID` Rozpoczyna profilowanie określonego procesu.

 **GlobalOff**&#124;**GlobalOn** zatrzymuje lub rozpoczyna profilowanie wszystkich procesów w sesji profilowania wiersza polecenia.

 {**ThreadOff**&#124;**ThreadOn**} **:** `TID` Zatrzymuje lub rozpoczyna profilowanie dla określonego wątku (tylko metoda instrumentacji).

## <a name="example"></a>Przykład
 W tym przykładzie **podporządkowanie ProcessOff** służy do zbierania danych profilowania do uruchamiania aplikacji.

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the process after startup.
VSPerfCmd.exe /ProcessOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
