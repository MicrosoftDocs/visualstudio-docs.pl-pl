---
title: Licznik | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5da78c33af599accf5ff3a2e09a9afb52982573a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149279"
---
# <a name="counter"></a>Licznik
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Licznika** opcji zbiera dane z liczników wydajności procesora (sprzęt).  
  
- Gdy używana jest metoda profilowania próbkowanie **licznika** Określa licznik wydajności na układ i liczbę zdarzeń licznika do użycia jako interwał próbkowania. Można określić tylko jeden licznik, korzystając z próbkowania.  
  
- Gdy używana jest metoda profilowania Instrumentacja, liczbę zdarzeń licznika, które wystąpiły w przedziale między zdarzeniami poprzedni i bieżącej kolekcji są wyświetlane jako oddzielne pola w raportach profilera. Wiele **licznika** opcji można określić, gdy używasz instrumentacji.  
  
  Każdy typ procesora ma swój własny zestaw liczników wydajności sprzętu. Program profilujący definiuje zestaw liczników ogólnych problemów z wydajnością, które są wspólne dla prawie wszystkich procesorów. Aby wyświetlić listę liczników ogólnych i specyficznych dla procesora na komputerze, należy użyć narzędzia VSPerfCmd **QueryCounters** polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]  
```  
  
```  
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Name`  
 Nazwa licznika. Użyj VSPerfCmd.exe **/querycounters** opcję, aby wyświetlić listę nazw dostępne liczniki na komputerze.  
  
 `Reload`  
 Liczba zdarzeń licznika w interwale próbkowania. Nie należy używać przy użyciu metody instrumentacji.  
  
 `FriendlyName`  
 (Opcjonalnie) Ciąg używany zamiast `Name` w nagłówkach kolumn widoków i raportów profilera.  
  
## <a name="required-options"></a>Wymagane opcje  
 Opcja liczników należy używać tylko z jedną z następujących opcji:  
  
 **Początek:** `Trace`  
 Inicjuje profiler przy użyciu metody instrumentacji.  
  
 **Uruchom:** `AppName`  
 Rozpoczyna się określonej aplikacji i programu profilującego. Program profilujący musi zostać zainicjowany przy użyciu metody pobierania próbek.  
  
 **Dołącz:** `PID`  
 Uruchamia program profilujący i dołącza je do procesu określonego przez identyfikator procesu. Program profilujący musi zostać zainicjowany przy użyciu metody pobierania próbek.  
  
## <a name="example"></a>Przykład  
 Przykład metody pobierania próbek demonstracja przykładowej aplikacji w każdym 1000 wystąpień, licznika ogólnego profiler NonHaltedCycles.  
  
 Przykład metody Instrumentacji pokazuje, jak zainicjować profilera służąca do gromadzenia zdarzeń licznika L2InstructionFetches. Nazwa licznika L2InstructionFetches dotyczy procesora.  
  
```  
; Sample Method Example  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"  
  
;INSTRUMENTATION METHOD EXAMPLE  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
