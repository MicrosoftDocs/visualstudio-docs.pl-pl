---
title: GlobalOn i GlobalOff | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fc5a353b87d8dbe945e73d828269c38b18274a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961653"
---
# <a name="globalon-and-globaloff"></a>GlobalOn i GlobalOff
*VSPerfCmd.exe* **GlobalOff** i **GlobalOn** opcje wstrzymywanie i wznawianie profilowania dla wszystkich procesów i wątków w sesji profilowania z wiersza polecenia.  
  
 Można określić **GlobalOn** i **GlobalOff** jako tylko opcje *VSPerfCmd.exe* wiersza polecenia lub można je dołączać do wierszy polecenia, które również zawierać  **Rozpocznij**, **Uruchom**, lub **Dołącz** opcje.  
  
 **GlobalOn** i **GlobalOff** można również łączyć z **ProcessOn**, **ProcessOff**, **ThreadOn**i  **ThreadOff** opcje.  
  
 **GlobalOn** i **GlobalOff** opcji interakcji z **ProcessOn** i **ProcessOff** opcje, które kontrolują zbieranie danych dla określony proces, a za pomocą **ThreadOn** i **ThreadOff** opcje, które kontrolują zbieranie danych dla określonego wątku.  
  
 **GlobalOff** i **GlobalOn** opcje wpływa na liczbę globalnego uruchomień/zatrzymań, który jest przetwarzany przez funkcje interfejsu API programu profilującego.  
  
- **GlobalOff** natychmiast ustawia globalne liczbę uruchomień/zatrzymań 0 i w związku z tym wstrzymuje profilowania.  
  
- **GlobalOn** natychmiast Ustawia liczbę uruchomień/zatrzymań globalnego 1 i w związku z tym wznawia profilowania.  
  
  Aby uzyskać więcej informacji, zobacz [interfejsy API narzędzi profilowania](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /{GlobalOff|GlobalOn}  
  
VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]  
  
VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 **GlobalOn** i **GlobalOff** można określić w wierszach polecenia, które również zawierać następujące opcje.  
  
 **Początek:** `Method`  
 Inicjuje sesji wiersza polecenia profilera i ustawia określonej metody profilowania.  
  
 **Uruchom:** `AppName`  
 Uruchamia określoną aplikację i rozpoczyna się profilowanie przy użyciu metody pobierania próbek.  
  
 **Dołącz:** `PID`  
 Rozpoczyna się profilowanie określonego procesu.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`PID`  
 Zatrzymuje się lub uruchamia profilowanie dla określonego procesu.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Zatrzymuje się lub uruchamia profilowanie dla określonego procesu (tylko w przypadku metody Instrumentacji).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie **GlobalOff** i **GlobalOn** opcje są używane do unikanie zbierania danych profilowania dla aplikacji, uruchamiania i zamykania.  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)