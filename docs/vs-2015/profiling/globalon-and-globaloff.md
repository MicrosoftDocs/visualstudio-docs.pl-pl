---
title: GlobalOn i GlobalOff | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eae720bdd904c7b904c906022cea700512167617
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434231"
---
# <a name="globalon-and-globaloff"></a>GlobalOn i GlobalOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **GlobalOff** i **GlobalOn** opcje wstrzymywanie i wznawianie profilowania dla wszystkich procesów i wątków w sesji profilowania z wiersza polecenia.  
  
 Można określić **GlobalOn** i **GlobalOff** jak tylko opcje wiersza polecenia VSPerfCmd.exe lub uwzględnić je w wierszy polecenia, które również zawierać **Start**, **Uruchom**, lub **Dołącz** opcje.  
  
 **GlobalOn** i **GlobalOff** można również łączyć z **ProcessOn**, **ProcessOff**, **ThreadOn**i  **ThreadOff** opcje.  
  
 **GlobalOn** i **GlobalOff** opcji interakcji z **ProcessOn** i **ProcessOff** opcje, które kontrolują zbieranie danych dla określony proces, a za pomocą **ThreadOn** i **ThreadOff** opcje, które kontrolują zbieranie danych dla określonego wątku.  
  
 **GlobalOff** i **GlobalOn** opcje wpływa na liczbę globalnego uruchomień/zatrzymań, który jest przetwarzany przez funkcje interfejsu API programu profilującego.  
  
- **GlobalOff** natychmiast ustawia globalne liczbę uruchomień/zatrzymań 0 i w związku z tym wstrzymuje profilowania.  
  
- **GlobalOn** natychmiast Ustawia liczbę uruchomień/zatrzymań globalnego 1 i w związku z tym wznawia profilowania.  
  
  Aby uzyskać więcej informacji, zobacz [API narzędzi profilowania](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
 {**ProcessOff**&#124;**ProcessOn**} **:** `PID`  
 Zatrzymuje się lub uruchamia profilowanie dla określonego procesu.  
  
 {**ThreadOff**&#124;**ThreadOn**} **:** `TID`  
 Zatrzymuje się lub uruchamia profilowanie dla określonego procesu (tylko w przypadku metody Instrumentacji).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie **GlobalOff** i **GlobalOn** opcje są używane do unikanie zbierania danych profilowania dla aplikacji, uruchamiania i zamykania.  
  
```  
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
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
