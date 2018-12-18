---
title: Dołącz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 136ee79c8fc7a3c6d627d186cb2f0dd0266b7a42
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727335"
---
# <a name="attach"></a>Dołącz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Dołącz** opcji rozpoczyna się profilowanie przykładowe uruchomionego procesu określonego przez identyfikator procesu (PID).  
  
 Do użycia **Attach** opcji, należy określić **przykładowe** metody w opcji uruchamiania.  
  
> [!NOTE]
>  Jeśli **Start** została określona opcja **Crosssession** opcji wszelkie wywołania **VSPerfCmd /Attach** lub **VSPerfCmd/detach** musi również określić **Crosssession**.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `ProcessID`  
 Identyfikator procesu (PID) uruchomionego procesu. Identyfikator PID uruchomionego procesu znajduje się na karcie Procesy Menedżera zadań Windows.  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 Następujące **VSPerfCmd** opcje można łączyć z **Dołącz** opcji w pojedynczym wierszu polecenia.  
  
 **Crosssession**  
 Włącza profilowanie aplikacji w sesjach innych niż sesji logowania. Jeśli wymagane **Start** została określona opcja **Crosssession** opcji.  
  
 **Początek:** `Method`  
 Inicjuje sesji wiersza polecenia profilera i ustawia określonej metody profilowania.  
  
 **TargetCLR**  
 Określa wersję programu .NET Framework języka wspólnego środowiska uruchomieniowego (CLR) do profilowania, gdy więcej niż jedna wersja jest załadowana w sesji profilowania. Domyślnie jest profilowane pierwszy załadowano wersję.  
  
 **GlobalOn GlobalOff**  
 Wznawia (**GlobalOn**) lub zatrzymuje (**GlobalOff**) profilowania, ale nie kończy się sesja profilowania.  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Wznawia (**ProcessOn**) lub zatrzymuje (**ProcessOff**) profilowania dla określonego procesu.  
  
## <a name="interval-options"></a>Opcje interwału  
 W wierszu polecenia Attach można określić jedną z następujących opcji interwału próbkowania. Domyślny interwał próbkowania wynosi 10 000 000 cykli zegara procesora.  
  
 **Czasomierz**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[<strong>:</strong> Zdarzenia]**licznika**[**:**`Name`,`Reload`,`FriendlyName`]  
 Określa numer i typ używanego interwału próbkowania.  
  
-   **Czasomierz** — przykłady co `Cycles` cykli zegara procesora. Jeśli `Cycles` nie zostanie określony, 10 000 000 cykle są używane.  
  
-   **PF** — przykłady co `Events` błędów stron. Jeśli `Events` nie zostanie określony, 10 błędów strony są używane.  
  
-   **Sys** — przykłady co `Events` wywołania systemu operacyjnego. Jeśli `Events` nie zostanie określony, 10 wywołań systemowych są używane.  
  
-   **Licznik** — przykłady co `Reload` liczba wydajność procesora CPU, licznik określonej przez `Name`. Opcjonalnie `FriendlyName` można określić ciąg do użycia jako nagłówek kolumny w raportach profilera.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak można dołączyć do uruchomionego wystąpienia aplikacji z Identyfikatorem procesu 12345.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



