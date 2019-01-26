---
title: Uruchom | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcd6a5d9008a53e1ae6cd25954d047b68e3168de
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033222"
---
# <a name="launch"></a>Uruchom
**Uruchom** opcji uruchamiania profilera za pomocą metody pobierania próbek i uruchomieniu określonej aplikacji.  
  
 Do użycia **Uruchom** opcji, należy określić **przykładowe** method in Class metoda **Start** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
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
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)