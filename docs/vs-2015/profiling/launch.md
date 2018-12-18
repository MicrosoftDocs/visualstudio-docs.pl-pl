---
title: Uruchom | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d8f745a775f8cad3932f20525b09fe55fb857ee
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791842"
---
# <a name="launch"></a>Uruchom
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Uruchom** opcji uruchamiania profilera za pomocą metody pobierania próbek i uruchomieniu określonej aplikacji.  
  
 Do użycia **Uruchom** opcji, należy określić **przykładowe** method in Class metoda **Start** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `AppName`  
 Nazwa aplikacji do uruchomienia. Pełne i częściowe ścieżki z bieżącego katalogu są obsługiwane.  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 Można łączyć z następujących opcji VSPerfCmd **Uruchom** opcji w pojedynczym wierszu polecenia.  
  
 **Początek:** `Method`  
 Inicjuje sesji wiersza polecenia profilera i ustawia określonej metody profilowania.  
  
 **GlobalOn** i **GlobalOff**  
 Wznawia (**GlobalOn**) lub zatrzymuje (**GlobalOff**) profilowania, ale nie kończy się sesja profilowania.  
  
 **ProcessOn:** `PID` i **ProcessOff**:`PID`  
 Wznawia (**ProcessOn**) lub zatrzymuje (**ProcessOff**) profilowania dla określonego procesu.  
  
 **TargetCLR**  
 Określa wersję programu .NET Framework języka wspólnego środowiska uruchomieniowego (CLR) do profilowania, gdy więcej niż jedna wersja jest załadowana w sesji profilowania. Domyślnie jest profilowane pierwszy załadowano wersję.  
  
## <a name="exclusive-options"></a>Wykluczających się opcji  
 Następujące opcje można używać tylko z **Uruchom** opcji.  
  
 **Console**  
 Uruchamia określony aplikacji wiersza polecenia w nowym oknie.  
  
 **Argumenty:** `ArgList`  
 Określa listę argumenty do przekazania do aplikacji.  
  
 **LineOff**  
 Wyłącza kolekcję profilowania danych na poziomie wiersza.  
  
## <a name="sampling-options"></a>Opcje próbkowania  
 Można określić tylko jedną z następujących opcji Interwał próbkowania na **Uruchom** wiersza polecenia. Domyślny interwał próbkowania wynosi 10 000 000 cykli zegara procesora.  
  
 **Czasomierz**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:**`Events`] **Licznik**[**:**`Name`,`Reload`,`FriendlyName`]**GC**[:**alokacji** &#124;  **okres istnienia**]  
 Określa liczbę i typ interwału próbkowania.  
  
-   **Czasomierz** — przykłady co `Cycles` cykli zegara procesora niewstrzymanych. Jeśli `Cycles` nie zostanie określony, 10 000 000 cykle są używane.  
  
-   **PF** — przykłady co `Events` błędów stron. Jeśli `Events` nie zostanie określony, 10 błędów stron.  
  
-   **Sys** — przykłady co `Events` wywołania systemu operacyjnego. Jeśli `Events` nie zostanie określony, 10 wywołań systemowych są używane.  
  
-   **Licznik** — przykłady co `Reload` liczba wydajność procesora CPU, licznik określonej przez `Name`. Opcjonalnie `FriendlyName` można określić ciąg do użycia jako nagłówek kolumny w raportach profilera.  
  
-   **GC** — .NET umożliwia zbieranie danych pamięci. Domyślnie (**alokacji**), dane są zbierane na każde zdarzenie alokacji pamięci. Gdy **okres istnienia** parametr jest określony, dane są również zbierane przy każdym zdarzeniu kolekcji wyrzucania elementów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano użycie **Uruchom** uruchomić aplikację.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



