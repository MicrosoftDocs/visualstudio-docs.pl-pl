---
title: ThreadOn i ThreadOff | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 906629eb24f6be097f3e24dfca3e6a231f42357f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778157"
---
# <a name="threadon-and-threadoff"></a>ThreadOn i ThreadOff
Podpolecenia *VSPerfCmd.exe* **ThreadOff** i **ThreadOn** są dostępne tylko w sesjach profilowania wiersza polecenia, które używają metody instrumentacji. **ThreadOff** i **ThreadOn** wstrzymać i wznowić profilowanie dla określonego wątku. **ThreadOff** zatrzymuje profilowanie wątku i **ThreadOn** rozpoczyna profilowanie wątku.

 W większości przypadków można określić **ThreadOn** lub **ThreadOff** jako jedyną opcję w wierszu polecenia *VSPerfCmd.exe,* ale mogą być również łączone z **globalon**, **GlobalOff**, **ProcessOn**i **ProcessOff** podpoleceń.

 **ThreadOn** i **ThreadOff** podpolecenia interakcji z **GlobalOn** i **GlobalOff** podpoleceń, które kontrolują zbieranie danych dla wszystkich procesów w sesji profilowania wiersza polecenia i **ProcessOn** i **ProcessOff** podpoleceń, które kontrolują zbieranie danych dla określonego procesu.

 **ThreadOff** i **ThreadOn** podpolecania również wpływ na licznik start/stop wątku, który jest manipulowany przez funkcje interfejsu API profilera.

- **ThreadOff** natychmiast ustawia liczba start/stop wątku na 0 i w związku z tym wstrzymuje profilowanie.

- **ThreadOn** natychmiast ustawia licznik start/stop wątku na 1 i w związku z tym wznawia profilowanie.

  Aby uzyskać więcej informacji, zobacz [Narzędzia profilowania interfejsów API](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]

```

#### <a name="parameters"></a>Parametry
 `TID`Identyfikator liczby całkowitej wątku do uruchomienia lub zatrzymania.

## <a name="valid-options"></a>Prawidłowe opcje
 **ThreadOn** i **ThreadOff** można określić w wierszach poleceń, które zawierają również następujące podpoleca.

 **Start:** `Method` Inicjuje sesję profilowania wiersza polecenia i ustawia określoną metodę profilowania.

 **GlobalOff**&#124;**GlobalOn** zatrzymuje lub rozpoczyna profilowanie wszystkich procesów w sesji profilowania wiersza polecenia.

 {**ProcessOff**&#124;**ProcessOn**} **:** `TID` Zatrzymuje lub rozpoczyna profilowanie dla określonego procesu.

## <a name="example"></a>Przykład
 W tym przykładzie **ThreadOff** podpolecania jest używany do zatrzymania zbierania danych profilowania, tak aby zbierane są tylko dane uruchamiania aplikacji.

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the thread after startup.
VSPerfCmd.exe /ThreadOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
