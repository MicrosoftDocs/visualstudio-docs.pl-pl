---
title: PF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 243d5fada7342bc05d8768a7e33cca6f55e309ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811368"
---
# <a name="pf"></a>PF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja VSPerfCmd.exe **PF** ustawia zdarzenie profilowania, które jest próbkowane do błędów strony i opcjonalnie zmienia liczbę błędów stron w interwale próbkowania z wartości domyślnej 10.  
  
> [!NOTE]
> Nie można używać PF w systemach 64 bitowych.  
  
 **Uwaga PF** nie jest obsługiwana na komputerach 64 bitowych. **PF** można użyć tylko w wierszu polecenia, który zawiera również opcję **uruchamiania** lub **dołączania** .  
  
 Domyślnie zdarzenie próbkowania jest ustawione na niezatrzymane cykle zegara procesora, a interwał próbkowania jest ustawiony na 10 000 000. Opcje **Timer**, **PF**, **sys**i **Counter** umożliwiają ustawienie interwału próbkowania i próbkowania. Opcja **GC** zbiera dane pamięci .NET dla każdego zdarzenia alokacji i wyrzucania elementów bezużytecznych. W wierszu polecenia można określić tylko jedną z tych opcji.  
  
 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w pierwszym wierszu polecenia, który zawiera opcję **uruchamiania** lub **dołączania** .  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Events`  
 Wartość całkowita określająca liczbę zdarzeń błędów stron w interwale próbkowania. Jeśli `Events` nie jest określony, interwał jest ustawiony na wartość 10.  
  
## <a name="required-options"></a>Wymagane opcje  
 **PF** można określić tylko w wierszu polecenia, który zawiera jedną z następujących opcji.  
  
 **Uruchom:**`AppName`  
 Uruchamia Profiler i aplikację określoną przez nazwa_aplikacji.  
  
 **Dołącz:**`PID`  
 Dołącza Profiler do procesu określonego przez nazwa_aplikacji.  
  
## <a name="invalid-options"></a>Nieprawidłowe opcje  
 Nie można określić następujących opcji w tym samym wierszu polecenia co **PF**.  
  
 **Czasomierz**[**:** `Cycles` ]  
 Ustawia zdarzenie próbkowania na cykle zegara procesora i opcjonalnie ustawia interwał próbkowania na `Cycles` . Domyślny interwał czasomierza to 10 000 000.  
  
 **Sys**[**:** `Events` ]  
 Ustawia zdarzenie próbkowania na wywołania z profilowanej aplikacji do jądra systemu operacyjnego (systemowe) i opcjonalnie ustawia interwał próbkowania na `Events` . Domyślny interwał sys to 10.  
  
 **Licznik:** `Name` [`,Reload`[`,FriendlyName`]]  
 Ustawia dla zdarzenia próbkowania licznik wydajności procesora CPU określony przez `Name` i ustawia interwał próbkowania na `Reload` .  
  
 **GC**[**:**{**przydział**&#124;**czas istnienia**}]  
 Zbiera dane pamięci platformy .NET. Domyślnie (**alokacja**) dane są zbierane przy każdym zdarzeniu przydziału pamięci. Gdy określono parametr **okresu istnienia** , dane są również zbierane przy każdym zdarzeniu odzyskiwania pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak ustawić zdarzenie przykładu profilowania na błędy stron i ustawić interwał próbkowania na 20 błędów stron.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
