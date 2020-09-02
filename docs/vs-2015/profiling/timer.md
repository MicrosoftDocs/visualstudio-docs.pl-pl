---
title: Czasomierz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e5f6c6db903b3ecced2ac3ebc4aaa0a3e60910c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145502"
---
# <a name="timer"></a>Czasomierz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja **czasomierza** VSPerfCmd.exe ustawia zdarzenie profilowania, które jest próbkowane do cykli zegara procesora i opcjonalnie zmienia liczbę cykli w interwale próbkowania z wartości domyślnej 10 000 000. W przypadku procesora 1GH (jeden gigaherca) 10 000 000 cykle zegara wynosi około 100 próbek na sekundę. Minimalna liczba cykli, które można określić, to 50 000.  
  
 **Czasomierza** można używać tylko wtedy, gdy używana jest metoda profilowania próbkowania i może być używana tylko w wierszu polecenia, który zawiera również opcję **uruchamiania** lub **dołączania** .  
  
 Domyślnie zdarzenie próbkowania profilera jest ustawione na cykle zegara procesora, a interwał próbkowania jest ustawiony na 10 000 000. Opcje **Timer**, **PF**, **sys**i **Counter** umożliwiają ustawienie zdarzenia próbkowania i interwału próbkowania. Opcja **GC** zbiera dane pamięci .NET dla każdego zdarzenia alokacji i wyrzucania elementów bezużytecznych. W wierszu polecenia można określić tylko jedną z tych opcji.  
  
 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w pierwszym wierszu polecenia zawierającym opcję **uruchamiania** lub **dołączania** .  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Cycles`  
 Wartość całkowita określająca liczbę cykli zegara procesora w interwale próbkowania. Jeśli `Cycles` nie jest określony, interwał jest ustawiony na 10 000 000. Określ wartość bez przecinków.  
  
## <a name="required-options"></a>Wymagane opcje  
 **Czasomierz** może być określony tylko w wierszu polecenia, który zawiera jedną z następujących opcji.  
  
 **Uruchom:**`AppName`  
 Uruchamia program profilujący i aplikację określoną przez `AppName` .  
  
 **Dołącz:**`PID`  
 Dołącza Profiler do procesu określonego przez identyfikator procesu ( `PID` ).  
  
## <a name="invalid-options"></a>Nieprawidłowe opcje  
 Nie można określić następujących opcji w tym samym wierszu polecenia co **czasomierz**.  
  
 **PF**[**:** `Events` ]  
 Ustawia zdarzenie próbkowania na błędy stron i opcjonalnie ustawia interwał próbkowania na `Events` . Domyślny interwał PF wynosi 10.  
  
 **Sys**[**:** `Events` ]  
 Ustawia zdarzenie próbkowania na wywołania systemu operacyjnego i opcjonalnie ustawia interwał próbkowania na `Events` . Domyślny interwał sys to 10.  
  
 **Licznik**[**:** `Name,Reload,FriendlyName` ]  
 Ustawia dla zdarzenia próbkowania licznik wydajności procesora CPU określony przez `Name` i ustawia interwał próbkowania na `Reload` .  
  
 **GC**[**:**{**przydział**&#124;**czas istnienia**}]  
 Zbiera dane pamięci platformy .NET. Domyślnie (**alokacja**) dane są zbierane przy każdym zdarzeniu przydziału pamięci. Gdy określono parametr **okresu istnienia** , dane są również zbierane przy każdym zdarzeniu odzyskiwania pamięci.  
  
## <a name="example"></a>Przykład  
 Ten przykład ilustruje sposób ustawiania interwału próbkowania profilera do 1 000 000 cykli procesora.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
