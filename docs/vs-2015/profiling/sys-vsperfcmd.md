---
title: Sys (VSPerfCmd) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7968d35050c7b36957b56b9c707fe0404842a07a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749826"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Sys** opcja umożliwia ustawienie profilowania zdarzenia, które są próbkowane tak, aby zdarzenia wywołania systemowe (wywołania funkcji w profilowanej aplikacji do systemu operacyjnego) i opcjonalnie zmiany liczby system wywołań podczas próbkowania Interwał od domyślna wartość wynosząca 10.  
  
 **Sys** należy używać tylko w wierszu polecenia, który zawiera także **Uruchom** lub **Dołącz** opcji.  
  
 Domyślnie ustawiono profiler zdarzenie próbkowania cykli zegara procesora oraz interwał próbkowania jest ustawiony na 10 000 000. **Czasomierza**, **PF**, **Sys**, i **licznika** opcje umożliwiają skonfigurowanie zdarzenie próbkowania i interwał próbkowania. **GC** opcja służy do zbierania danych pamięci .NET na każde zdarzenie kolekcji alokacji i odzyskiwanie. W wierszu polecenia można określić tylko jeden z tych opcji.  
  
 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w przypadku pierwszego wiersza polecenia, który zawiera **Uruchom** lub **Dołącz** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Events`  
 Wartość całkowitą, która określa liczbę system wywołać zdarzenia w interwale próbkowania. Jeśli `Events` nie zostanie określony, interwał wynosi 10.  
  
## <a name="required-options"></a>Wymagane opcje  
 **Sys** wymaga jednej z następujących opcji.  
  
 **Uruchom:** `AppName`  
 Uruchamia program profilujący i aplikacji, określonej przez `AppName`.  
  
 **Dołącz:** `PID`  
 Dołącza profiler do procesu określonego przez `PID`.  
  
## <a name="invalid-options"></a>Nieprawidłowe opcje  
 Nie można określić następujące opcje w wierszu polecenia jako **Sys**.  
  
 **PF**[**:**`Events`]  
 Ustawia zdarzenie próbkowania błędów strony i opcjonalnie ustawia interwał próbkowania `Events`. Domyślny interwał PF wynosi 10.  
  
 **Czasomierz**[**:**`Cycles`]  
 Ustawia zdarzenie próbkowania zegara procesora cykli i opcjonalnie ustawia interwał próbkowania `Cycles`. Domyślny interwał czasomierza wynosi 10 000 000.  
  
 **Licznik:** `Name`[`,Reload`[`,FriendlyName`]]  
 Ustawia zdarzenie próbkowania wydajności procesorów CPU, licznik określonej przez `Name` i ustawia interwał próbkowania `Reload`.  
  
 **GC**[**:**{**alokacji**&#124;**okres istnienia**}]  
 Zbiera dane pamięci platformy .NET. Domyślnie (**alokacji**), dane są zbierane na każde zdarzenie alokacji pamięci. Gdy **okres istnienia** parametr jest określony, dane są również zbierane przy każdym zdarzeniu kolekcji wyrzucania elementów.  
  
## <a name="example"></a>Przykład  
 W przykładzie pokazano, jak skonfigurować program profilujący zdarzenie próbkowania na wywołania systemowe i jak ustawić interwał próbkowania do 20 połączeń na próbkę.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



