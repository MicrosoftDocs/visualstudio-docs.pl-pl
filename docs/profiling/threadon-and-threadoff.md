---
title: ThreadOn i ThreadOff | Microsoft Docs
description: Dowiedz się, w jaki sposób VSPerfCmd.exe ThreadOff i ThreadOn podpolecenia są dostępne tylko w sesjach profilowania wiersza polecenia, które korzystają z metody instrumentacji.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f8b2e51857fc799c7b60f7650b823b77c9c6a283
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718775"
---
# <a name="threadon-and-threadoff"></a>ThreadOn i ThreadOff
Podpolecenia *VSPerfCmd.exe* **ThreadOff** i **ThreadOn** są dostępne tylko w sesjach profilowania wiersza polecenia, które korzystają z metody instrumentacji. **ThreadOff** i **ThreadOn** Wstrzymywanie i wznawianie profilowania dla określonego wątku. **ThreadOff** przerywa Profilowanie wątku, a **ThreadOn** uruchamia Profilowanie wątku.

 W większości przypadków należy określić **ThreadOn** lub **ThreadOff** jako jedyną opcję w wierszu polecenia *VSPerfCmd.exe* , ale można je również łączyć z podpoleceniami **GlobalOn**, **GlobalOff**, **ProcessOn** i **ProcessOff** .

 Podpolecenia **ThreadOn** i **ThreadOff** współpracują z podpoleceniami **GlobalOn** i **GlobalOff** , które kontrolują zbieranie danych dla wszystkich procesów w sesji profilowania wiersza polecenia i polecenia **ProcessOn** i **ProcessOff** , które kontrolują zbieranie danych dla określonego procesu.

 Podpolecenia **ThreadOff** i **ThreadOn** wpływają również na licznik uruchomienia/zatrzymania wątku, który jest MANIPULOWANY przez funkcje interfejsu API profilera.

- **ThreadOff** natychmiast ustawia liczbę uruchomień/zatrzymań wątku na wartość 0, w związku z tym wstrzymuje profilowanie.

- **ThreadOn** natychmiast ustawia liczbę uruchomień/zatrzymań wątku na 1, w związku z tym wznawia profilowanie.

  Aby uzyskać więcej informacji, zobacz [interfejsy API narzędzi profilowania](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]

```

#### <a name="parameters"></a>Parametry
 `TID` Identyfikator liczby całkowitej wątku, który ma zostać uruchomiony lub zatrzymany.

## <a name="valid-options"></a>Prawidłowe opcje
 **ThreadOn** i **ThreadOff** można określić w wierszach poleceń, które również zawierają następujące podpolecenia.

 **Rozpocznij:** `Method` Inicjuje sesję profilowania wiersza polecenia i ustawia określoną metodę profilowania.

 **GlobalOff**&#124;**GlobalOn** zatrzymanie lub uruchomienie profilowania dla wszystkich procesów w sesji profilowania wiersza polecenia.

 {**ProcessOff**&#124;**ProcessOn**} **:**`TID` Powoduje zatrzymanie lub uruchomienie profilowania dla określonego procesu.

## <a name="example"></a>Przykład
 W tym przykładzie podpolecenie **ThreadOff** służy do zatrzymania zbierania danych profilowania, tak że zbierane są tylko dane uruchamiania aplikacji.

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

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
