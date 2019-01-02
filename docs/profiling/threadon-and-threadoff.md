---
title: ThreadOn i ThreadOff | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d76548ad85a02df6e2217b28535d268d7823be70
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895509"
---
# <a name="threadon-and-threadoff"></a>ThreadOn i ThreadOff
*VSPerfCmd.exe* **ThreadOff** i **ThreadOn** podpoleceń polecenia są dostępne tylko w sesji profilowania wiersza polecenia, korzystających z metody instrumentacji. **ThreadOff** i **ThreadOn** wstrzymywanie i wznawianie profilowania dla określonego wątku. **ThreadOff** zatrzymuje profilowanie wątku i **ThreadOn** uruchamia profilowanie wątku.  
  
 W większości przypadków należy określić **ThreadOn** lub **ThreadOff** jako jedyną opcję w *VSPerfCmd.exe* wiersza polecenia, ale można również łączyć z  **GlobalOn**, **GlobalOff**, **ProcessOn**, i **ProcessOff** podpoleceń polecenia.  
  
 **ThreadOn** i **ThreadOff** podpoleceń polecenia interakcji z **GlobalOn** i **GlobalOff** podpoleceń polecenia, które kontrolują danych zbieranie dla wszystkich procesów w sesji profilowania wiersza polecenia i **ProcessOn** i **ProcessOff** podpoleceń polecenia, które kontrolują zbieranie danych dla określonego procesu.  
  
 **ThreadOff** i **ThreadOn** podpoleceń polecenia wpływa na liczbę wątków uruchomień/zatrzymań, który jest przetwarzany przez funkcje API profilera.  
  
- **ThreadOff** natychmiast Ustawia liczbę uruchomień/zatrzymań wątek 0 i w związku z tym wstrzymuje profilowania.  
  
- **ThreadOn** natychmiast Ustawia liczbę uruchomień/zatrzymań wątku 1 i w związku z tym wznawia profilowania.  
  
  Aby uzyskać więcej informacji, zobacz [interfejsy API narzędzi profilowania](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `TID`  
 Identyfikator całkowitą wątku, aby rozpocząć lub zatrzymać.  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 **ThreadOn** i **ThreadOff** można określić w wierszach polecenia, które również zawierać następujących podpoleceń polecenia.  
  
 **Początek:** `Method`  
 Inicjuje sesję profilowania wiersza polecenia, a następnie ustawia określonej metody profilowania.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Zatrzymuje się lub uruchamia profilowanie dla wszystkich procesów w sesji profilowania z wiersza polecenia.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 Zatrzymuje się lub uruchamia profilowanie dla określonego procesu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie **ThreadOff** podpolecenia jest używany, aby zatrzymać zbieranie danych profilowania, dzięki czemu są zbierane tylko dane uruchamiania aplikacji.  
  
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
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)