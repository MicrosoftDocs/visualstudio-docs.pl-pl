---
title: PF | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67663c067188a703ff6228a703a71ac8a1a0b355
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757092"
---
# <a name="pf"></a>PF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **PF** opcja umożliwia ustawienie profilowania zdarzenia, które są próbkowane tak, błędów stron i opcjonalnie zmienia liczbę błędów stron w interwale próbkowania domyślna wartość wynosząca 10.  
  
> [!NOTE]
>  Nie można PF w systemach 64-bitowych.  
  
 **Należy pamiętać, PF** nie jest obsługiwane na komputerach 64-bitowym. **PF** należy używać tylko w wierszu polecenia, który zawiera także **Uruchom** lub **Dołącz** opcji.  
  
 Domyślnie ustawiono zdarzenie próbkowania cykli zegara procesora niewstrzymanych, a interwał próbkowania jest ustawiony na 10 000 000. **Czasomierza**, **PF**, **Sys**, i **licznika** opcje umożliwiają skonfigurowanie interwału próbkowania zdarzeń i pobieranie próbek. **GC** opcja służy do zbierania danych pamięci .NET na każde zdarzenie kolekcji alokacji i odzyskiwanie. W wierszu polecenia można określić tylko jeden z tych opcji.  
  
 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w przypadku pierwszego wiersza polecenia, który zawiera **Uruchom** lub **Dołącz** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Events`  
 Wartość całkowita, która określa liczbę zdarzeń błędów strony w interwale próbkowania. Jeśli `Events` nie zostanie określony, interwał wynosi 10.  
  
## <a name="required-options"></a>Wymagane opcje  
 **PF** można określić tylko w wierszu polecenia, który zawiera jeden z następujących opcji.  
  
 **Uruchom:** `AppName`  
 Uruchamia program profilujący i aplikacji określonej przez AppName.  
  
 **Dołącz:** `PID`  
 Dołącza profiler do procesu określonego przez AppName.  
  
## <a name="invalid-options"></a>Nieprawidłowe opcje  
 Nie można określić następujące opcje w wierszu polecenia jako **PF**.  
  
 **Czasomierz**[**:**`Cycles`]  
 Ustawia zdarzenie próbkowania zegara procesora cykli i opcjonalnie ustawia interwał próbkowania `Cycles`. Domyślny interwał czasomierza wynosi 10 000 000.  
  
 **Sys**[**:**`Events`]  
 Ustawia zdarzenie próbkowania na wywołania z profilowaną aplikację do jądra systemu operacyjnego (syscalls) i opcjonalnie ustawia interwał próbkowania `Events`. Domyślny interwał Sys wynosi 10.  
  
 **Licznik:** `Name`[`,Reload`[`,FriendlyName`]]  
 Ustawia zdarzenie próbkowania wydajności procesorów CPU, licznik określonej przez `Name` i ustawia interwał próbkowania `Reload`.  
  
 **GC**[**:**{**alokacji**&#124;**okres istnienia**}]  
 Zbiera dane pamięci platformy .NET. Domyślnie (**alokacji**), dane są zbierane na każde zdarzenie alokacji pamięci. Gdy **okres istnienia** parametr jest określony, dane są również zbierane przy każdym zdarzeniu kolekcji wyrzucania elementów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak ustawić profilowania zdarzenie próbkowania błędów strony i ustawić interwału próbkowania 20 błędów stron.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



