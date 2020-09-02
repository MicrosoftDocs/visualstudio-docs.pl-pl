---
title: GlobalOn i GlobalOff | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434231"
---
# <a name="globalon-and-globaloff"></a>GlobalOn i GlobalOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcje VSPerfCmd.exe **GlobalOff** i **GlobalOn** wstrzymują i wznawiają profilowanie wszystkich procesów i wątków w sesji profilowania wiersza polecenia.  
  
 Można określić **GlobalOn** i **GlobalOff** jako jedyne opcje w wierszu polecenia VSPerfCmd.exe lub można je uwzględnić w wierszach poleceń, które zawierają również opcje **uruchamiania**, **uruchamiania**lub **dołączania** .  
  
 **GlobalOn** i **GlobalOff** można także łączyć z opcjami **ProcessOn**, **ProcessOff**, **ThreadOn**i **ThreadOff** .  
  
 Opcje **GlobalOn** i **GlobalOff** współpracują z opcjami **ProcessOn** i **ProcessOff** kontrolującymi zbieranie danych dla określonego procesu oraz z opcjami **ThreadOn** i **ThreadOff** kontrolującymi zbieranie danych dla określonego wątku.  
  
 Opcje **GlobalOff** i **GlobalOn** wpływają również na globalną liczbę uruchomień/zatrzymań, które są MANIPULOWANE przez funkcje interfejsu API profilera.  
  
- **GlobalOff** natychmiast ustawia globalną liczbę uruchomień/zatrzymań na 0 i w związku z tym wstrzymuje profilowanie.  
  
- **GlobalOn** natychmiast ustawia globalną liczbę uruchomień/zatrzymań na 1 i w związku z tym wznawia profilowanie.  
  
  Aby uzyskać więcej informacji, zobacz [narzędzia profilowania interfejsów API](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /{GlobalOff|GlobalOn}  
  
VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]  
  
VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 **GlobalOn** i **GlobalOff** można określić w wierszach poleceń, które również zawierają następujące opcje.  
  
 **Rozpocznij:**`Method`  
 Inicjuje sesję profilera wiersza polecenia i ustawia określoną metodę profilowania.  
  
 **Uruchom:**`AppName`  
 Uruchamia określoną aplikację i rozpoczyna profilowanie przy użyciu metody próbkowania.  
  
 **Dołącz:**`PID`  
 Rozpoczyna profilowanie określonego procesu.  
  
 {**ProcessOff**&#124;**ProcessOn**} **:**`PID`  
 Powoduje zatrzymanie lub uruchomienie profilowania dla określonego procesu.  
  
 {**ThreadOff**&#124;**ThreadOn**} **:**`TID`  
 Kończy lub uruchamia profilowanie dla określonego procesu (tylko Metoda Instrumentacji).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie opcje **GlobalOff** i **GlobalOn** są używane w celu uniknięcia zbierania danych profilowania do uruchamiania i zamykania aplikacji.  
  
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
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
