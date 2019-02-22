---
title: ProcessOn i ProcessOff | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab218f8dabb2b4360c1be17d809399a752f7cc2c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611805"
---
# <a name="processon-and-processoff"></a>ProcessOn i ProcessOff
VSPerfCmd.exe **ProcessOff** i **ProcessOn** podpoleceń polecenia wstrzymywanie i wznawianie profilowania dla określonego procesu w sesji profilowania z wiersza polecenia. **ProcessOff** zatrzymuje profilowanie procesu i **ProcessOn** uruchamia profilowanie procesu.

 W większości przypadków należy określić **ProcessOn** lub **ProcessOff** jako jedyną opcję w VSPerfCmd.exe wiersza polecenia, ale można również łączyć z **GlobalOn**, **GlobalOff**, **ThreadOn**, i **ThreadOff** podpoleceń polecenia.

 **ProcessOn** i **ProcessOff** podpoleceń polecenia interakcji z **GlobalOn** i **GlobalOff** podpoleceń polecenia, które kontrolują danych zbieranie dla wszystkich procesów w sesji profilowania wiersza polecenia i **ThreadOn** i **ThreadOff** podpoleceń polecenia, które kontroluje zbierania danych dla określonego wątku.

 **ProcessOff** i **ProcessOn** podpoleceń polecenia wpływa na liczbę procesu uruchamiania/zatrzymywania, który jest przetwarzany przez profiler interfejsu API funkcji.

- **ProcessOff** natychmiast Ustawia liczbę uruchomień/zatrzymań procesu 0 i w związku z tym wstrzymuje profilowania.

- **ProcessOn** natychmiast Ustawia liczbę uruchomień/zatrzymań procesu 1 i w związku z tym wznawia profilowania.

  Aby uzyskać więcej informacji, zobacz [API narzędzi profilowania](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]

```

#### <a name="parameters"></a>Parametry
 `PID` Liczba całkowita identyfikator procesu, aby rozpocząć lub zatrzymać. Identyfikatory procesów są wyświetlane na **procesu** kartę w Menedżerze zadań Windows.

## <a name="required-subcommands"></a>Wymagane podpoleceń polecenia.
 Brak

## <a name="valid-subcommands"></a>Nieprawidłowa podpoleceń polecenia.
 **ProcessOn** i **ProcessOff** można określić w wierszach polecenia, które również zawierać następujących podpoleceń polecenia.

 **Początek:** `Method` Inicjuje sesję profilowania wiersza polecenia, a następnie ustawia określonej metody profilowania.

 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna się profilowanie przy użyciu metody pobierania próbek.

 **Dołącz:** `PID` Rozpoczyna się profilowanie określonego procesu.

 **GlobalOff**&#124;**GlobalOn** zatrzymaniu lub uruchomieniu profilowania dla wszystkich procesów w sesji profilowania z wiersza polecenia.

 {**ThreadOff**&#124;**ThreadOn**}**:**`TID` Zatrzymuje się lub uruchamia profilowanie dla określonego wątku (tylko w przypadku metody Instrumentacji).

## <a name="example"></a>Przykład
 W tym przykładzie **ProcessOff** podpolecenia jest używany do zbierania danych profilowania dla uruchamiania aplikacji.

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

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)