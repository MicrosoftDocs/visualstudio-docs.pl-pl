---
title: Dołącz | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc094fe4d8ef59a17a64d654edff4a834964df79
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53901324"
---
# <a name="attach"></a>Dołącz
*VSPerfCmd.exe* **Dołącz** opcji rozpoczyna się profilowanie przykładowe uruchomionego procesu określonego przez identyfikator procesu (PID).  
  
 Do użycia **Attach** opcji, należy określić **przykładowe** metody w opcji uruchamiania.  
  
> [!NOTE]
>  Jeśli **Start** została określona opcja **Crosssession** opcji wszelkie wywołania **VSPerfCmd /Attach** lub **VSPerfCmd/detach** musi również określić **Crosssession**.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
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
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)