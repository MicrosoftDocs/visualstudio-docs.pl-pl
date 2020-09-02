---
title: Dołącz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b9adb5a0a47c1ee98e0e390cfaf8b3a6dc78146
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831150"
---
# <a name="attach"></a>Dołącz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja **Dołączania** VSPerfCmd.exe rozpoczyna przykładowe profilowanie uruchomionego procesu określonego przez identyfikator procesu (PID).  
  
 Aby użyć opcji **Attach** , należy określić **przykładową** metodę w opcji Start.  
  
> [!NOTE]
> Jeśli opcja **Start** została określona przy użyciu opcji **CrossSession** , wszystkie wywołania **VSPerfCmd/Attach** lub **VSPerfCmd/detach** muszą również określać **CrossSession**.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `ProcessID`  
 Identyfikator procesu (PID) uruchomionego procesu. Identyfikator PID uruchomionego procesu jest wyświetlany na karcie procesy w Menedżerze zadań systemu Windows.  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 Następujące opcje **VSPerfCmd** można łączyć z opcją **Attach** w pojedynczym wierszu polecenia.  
  
 **CrossSession**  
 Włącza Profilowanie aplikacji w sesjach innych niż sesja logowania. Wymagane, jeśli opcja **Start** została określona z opcją **CrossSession** .  
  
 **Rozpocznij:**`Method`  
 Inicjuje sesję profilera wiersza polecenia i ustawia określoną metodę profilowania.  
  
 **TargetCLR**  
 Określa wersję .NET Framework środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja zostanie załadowana w sesji profilowania. Domyślnie pierwsza załadowana wersja jest profilowana.  
  
 **GlobalOn GlobalOff**  
 Wznawia (**GlobalOn**) lub wstrzymuje (**GlobalOff**) profilowanie, ale nie kończy sesji profilowania.  
  
 **ProcessOn:** `PID` **ProcessOff:**`PID`  
 Wznawia (**ProcessOn**) lub wstrzymuje (**ProcessOff**) profilowania dla określonego procesu.  
  
## <a name="interval-options"></a>Opcje interwału  
 Jedną z następujących opcji interwału próbkowania można określić w wierszu polecenia Attach. Domyślny interwał próbkowania to 10 000 000 cykli zegara procesora.  
  
 **Czasomierz**[**:** `Cycles` ]**PF**[**:** `Events` ]**sys**[<strong>:</strong>Events]**licznik**[**:** `Name` , `Reload` , `FriendlyName` ]  
 Określa liczbę i typ interwału próbkowania.  
  
- **Czasomierz** — przykłady dla każdego `Cycles` cyklu zegara procesora. Jeśli `Cycles` nie jest określona, używane są 10 000 000 cykli.  
  
- **PF** — przykłady `Events` błędów każdej strony. Jeśli `Events` nie jest określony, używane są 10 błędów stron.  
  
- **Sys** -przykłady każdego `Events` wywołania systemu operacyjnego. Jeśli `Events` nie jest określony, używane są 10 wywołań systemowych.  
  
- **Licznik** próbek każdej `Reload` liczby liczników wydajności procesora CPU określonych przez `Name` . Opcjonalnie `FriendlyName` można określić ciąg, który ma być używany jako nagłówek kolumny w raportach profilera.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak dołączyć do uruchomionego wystąpienia aplikacji z IDENTYFIKATORem procesu 12345.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
