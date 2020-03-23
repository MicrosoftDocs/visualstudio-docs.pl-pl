---
title: VSPerfCmd | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, VSPerfCmd tool
- command-line tools, VSPerfCmd tool
- command line, tools
- profiling tools,VSPerfCmd
- VSPerfCmd tool
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 53378c3d210ef9666df251d68a3eec570f8caa2f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778001"
---
# <a name="vsperfcmd"></a>VSPerfCmd
Narzędzie *VSPerfCmd.exe* służy do uruchamiania i zatrzymywania zbierania danych o wydajności. Używa następującej składni:

```cmd
VSPerfCmd [/U] [/options]
```

 W poniższych tabelach opisano opcje narzędzia *VSPerfCmd.exe.*

|Opcja|Opis|
|------------|-----------------|
|**U**|Przekierowane wyjście konsoli jest zapisywane jako Unicode. Musi być pierwszą określoną opcją.|
|[Start](../profiling/start.md) **:**`mode`|Uruchamia usługę profilowania w określonym trybie.|
|[Wyjście:](../profiling/output.md) **:**`filename`|Określa nazwę pliku wyjściowego. Używaj tylko z **startem**.|
|[CrossSession&#124;CS](../profiling/crosssession.md)|Umożliwia profilowanie w sesjach systemu Windows. Używaj tylko z **startem,** **dołączam** **lub uruchamianiem**.|
|[Użytkownik](../profiling/user-vsperfcmd.md) **:**:`domain\`[ ]`username`|Włącza określony dostęp do konta do usługi profilera. Używaj tylko z **startem**.|
|[WaitStart](../profiling/waitstart.md)[**:**`n`]|Czeka na zainicjowanie rejestratora zbierania danych. Jeśli `n` jest określony, **VSPerfCmd** `n` będzie czekać co najwyżej sekund. Jeśli `n` nie zostanie określony, **VSPerfCmd** będzie czekać przez czas nieokreślony. Ułatwia to korzystanie z **programu VSPerfCmd** w ramach procesu wsadowego.|
|[Licznik](../profiling/counter.md) **:**`cfg`|Gdy używana jest metoda profilowania próbki, określa licznik procesora CPU i liczbę zdarzeń do użycia jako interwał próbkowania. Można pobrać próbkę tylko jednej wartości licznika.<br /><br /> Gdy używana jest metoda profilowania instrumentacji, określa licznik procesora CPU, który ma być zbierany w każdym punkcie instrumentacji. Używaj tylko z **startem:**`Trace`, **Dołącz**lub **Uruchom**.|
|[QueryCounters](../profiling/querycounters.md)|Wyświetla listę prawidłowych liczników procesora dla bieżącego komputera.|
|[WinCounter](../profiling/wincounter.md) **:** *ścieżka*|Określa zdarzenie licznika wydajności systemu Windows, które ma być dołączane do danych znacznika profilu. Używaj tylko z **startem**.|
|[AutoMark](../profiling/automark.md) **:** *n*|Określa przedział czasu (w milisekundach) między zdarzeniami zbierania danych licznika wydajności systemu Windows. Użyj z **WinCounter**.|
|[Wydarzenia](../profiling/events-vsperfcmd.md) **:**`option`|Steruje zbieraniem określonych zdarzeń śledzenia zdarzeń dla systemu Windows (ETW). Dane ETW są zbierane do pliku . *itl,* który nie jest dane profilowania (.* vsp).*|
|[Stan](../profiling/status.md)|Wyświetla stan profilera, informacje o procesach, które są obecnie profilowane, oraz konta, które mają uprawnienia do kontrolowania profilera.|
|[Zamykanie](../profiling/shutdown.md)[**:**`n`]|Zamyka plik danych profilowania i wyłącza profiler.|
|[GlobalOn (GlobalOn)](../profiling/globalon-and-globaloff.md)|Wznawia zbieranie danych po wywołaniu **vsperfCmdGlobalOff**.|
|[Globaloff](../profiling/globalon-and-globaloff.md)|Zatrzymuje zbieranie wszystkich danych, ale nie kończy sesji profilowania.|
|[ProcesOn](../profiling/processon-and-processoff.md) **:**`pid`|Wznawia zbieranie danych dla określonego procesu po profilowaniu został wstrzymany przez wywołanie **VSPerfCmdProcessOff**.|
|[ProcessOff](../profiling/processon-and-processoff.md) **:**`pid`|Zatrzymuje zbieranie danych dla określonego procesu.|
|[ThreadOn i ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Wznawia profilowanie dla określonego procesu po profilowaniu został wstrzymany przez wywołanie **VSPerfCmdThreadOff**. **ThreadOn** należy używać tylko podczas profilowania za pomocą metody instrumentacji.|
|[ThreadOn i ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Wstrzymuje profilowanie dla określonego wątku. **ThreadOff** należy używać tylko podczas profilowania za pomocą metody instrumentacji.|
|[Znak](../profiling/mark.md) **:** _Marknum_[**,**_MarkText_**]**|Wstawia znacznik do pliku danych profilowania z opcjonalnym tekstem.|

## <a name="sample-method-options"></a>Przykładowe opcje metody
 Następujące opcje są dostępne tylko wtedy, gdy używasz metody profilowania próbkowania.

|Opcja|Opis|
|------------|-----------------|
|[Uruchomienie](../profiling/launch.md) **:** *Wykonywalne*|Uruchamia określoną aplikację i rozpoczyna profilowanie.|
|[Args](../profiling/args.md) **:** *Argumenty*|Określa argumenty wiersza polecenia, które mają być przerzucewane do uruchomionej aplikacji.|
|[Console](../profiling/console.md)|Uruchamia określone polecenie w nowym oknie wiersza polecenia.|
|[Dołącz](../profiling/attach.md) **:** *PID*[**,**_PID_]|Rozpoczyna profilowanie określonych procesów. Procesy można zidentyfikować za pomocą identyfikatora procesu lub nazwy procesu.|
|[Odłączyć](../profiling/detach.md)[**:**_PID_[,_PID_]]|Zatrzymuje profilowanie określonych procesów. Procesy można zidentyfikować za pomocą identyfikatora procesu lub nazwy procesu. Jeśli nie określono żadnego procesu, profilowanie jest zatrzymywana dla wszystkich procesów.|
|[Gc](../profiling/gc-vsperfcmd.md)[**:**{**Okres istnienia****alokacji**`&#124;`}]|Zbiera dane alokacji pamięci .NET i okresu istnienia obiektu. Używaj tylko z opcją **VSPerfCmdLaunch.**|

### <a name="sample-interval-options"></a>Opcje interwału próbek
 Następujące opcje określają typ i czas trwania interwałów pobierania próbek. Wartość domyślna to **Timer**. Licznik procesora CPU można również określić jako interwał, używając opcji **Licznik.** Te opcje można określić tylko za pomocą **uruchom** lub z pierwszym **Dołącz** sesji profilowania.

|Opcja|Opis|
|------------|-----------------|
|[PF](../profiling/pf.md)[**:**_n_]|Przykłady na każdej awarii strony n-th (default=10).|
|[Sys](../profiling/sys-vsperfcmd.md)[**:**_n_]|Przykłady przy każdym wywołaniu systemowym n-th (default=10).|
|[Zegar](../profiling/timer.md)[**:**_n_]|Próbki na każdym cyklu procesora n-th (domyślnie = 10000000).|

## <a name="service-component-and-kernel-mode-device-options"></a>Opcje urządzenia składnika usługi i trybu jądra
 Następujące opcje administratora obsługują składniki usługi profilowania lub sterowniki urządzeń w trybie jądra. Opcje administratora ustawiają uprawnienia do profilowania i kontrolują profilowane usługi lub sterownik urządzenia.

 Opcje administracyjne muszą być wykonywane w wierszu polecenia, który jest uruchomiony z poświadczeniami administracyjnymi.

|Opcja|Opis|
|------------|-----------------|
|**Admin:Security** \<, **ALLOW&#124;DENY**>, *Right*[ \< *Right*], *User*&#124;*Group*>|Zezwala lub odmawia określonemu użytkownikowi lub grupom dostępu do usług profilowania.<br /><br /> `Right`może to być:<br /><br /> CrossSession - daje użytkownikowi dostęp do usługi do profilowania sesji krzyżowej.<br /><br /> SampleProfiling — daje użytkownikowi dostęp do sterownika, aby włączyć profilowanie próbkowania. Używany również do uzyskiwania dostępu do informacji o przejściu jądra podczas profilowania śledzenia.<br /><br /> FullAccess - daje użytkownikowi dostęp zarówno CrossSession, jak i SampleProfiling.|
|**Administrator:Zabezpieczenia, Lista**|Wyświetla bieżący stan profilowania usług i wyświetla listę uprawnień użytkowników.|
|**Administrator:** \< *Sterownik&#124;* *Driver*>\<&#124;**&#124;** **ZAINSTALUJ**&#124;**ODINSTALUJ** **INSTALL**>|Uruchamia, zatrzymuje, instaluje lub odinstalowuje składnik usługi profilowania (usługa) lub sterownik urządzenia trybu jądra.|
|**Administrator:** \< *Funkcja* **automatycznego uruchamiania**\< *sterownika*>&#124;**w&#124;** **wył.**>|Włącza lub wyłącza automatyczne uruchamianie sterownika urządzenia (usługi) w trybie profilowania (usługi) lub trybu jądra po ponownym uruchomieniu.|

## <a name="vsperfcmd-driver"></a>VSPerfCmd /Sterownik
 **Opcja VSPerfCmd /Driver** jest teraz przestarzała. Użyj opcji **Administrator VsPerfCmd** dla tej funkcji.

## <a name="see-also"></a>Zobacz też
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfReport](../profiling/vsperfreport.md)
