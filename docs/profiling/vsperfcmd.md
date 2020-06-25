---
title: VSPerfCmd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: caf145213c41215d518cf42d0a69975c8580e817
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330016"
---
# <a name="vsperfcmd"></a>VSPerfCmd
Narzędzie *VSPerfCmd.exe* służy do uruchamiania i zatrzymywania zbierania danych o wydajności. Używa następującej składni:

```cmd
VSPerfCmd [/U] [/options]
```

 W poniższych tabelach opisano opcje narzędzia *VSPerfCmd.exe* .

|Opcja|Opis|
|------------|-----------------|
|**'T**|Przekierowane dane wyjściowe konsoli są zapisywane w formacie Unicode. Musi być pierwszą określoną opcją.|
|[Rozpocznij](../profiling/start.md) **:**`mode`|Uruchamia usługę profilowania w określonym trybie.|
|[Dane wyjściowe](../profiling/output.md) **:**`filename`|Określa nazwę pliku wyjściowego. Użyj tylko z **menu Start**.|
|[CrossSession&#124;CS](../profiling/crosssession.md)|Włącza profilowanie między sesjami systemu Windows. Używać tylko z poleceniem **Start**, **Attach** **lub Launch**.|
|[Użytkownik](../profiling/user-vsperfcmd.md) **:**[ `domain\` ]`username`|Umożliwia określonemu kontu dostęp do usługi profilera. Użyj tylko z **menu Start**.|
|[WaitStart](../profiling/waitstart.md)[**:** `n` ]|Czeka na zainicjowanie rejestratora zbierania danych. Jeśli `n` jest określony, **VSPerfCmd** będzie oczekiwać co najwyżej `n` sekund. Jeśli `n` nie jest określony, **VSPerfCmd** będzie czekać w nieskończoność. Ułatwia to użycie **VSPerfCmd** w ramach procesu wsadowego.|
|[Licznik](../profiling/counter.md) **:**`cfg`|Gdy używana jest przykładowa Metoda profilowania, określa licznik procesora i liczbę zdarzeń, które mają być używane jako interwał próbkowania. Można próbkować tylko jedną wartość licznika.<br /><br /> Gdy używana jest metoda profilowania instrumentacji, określa licznik procesora CPU do zebrania w każdym punkcie Instrumentacji. Użyj tylko z poleceniem **Start:** `Trace` , **Attach**lub **Launch**.|
|[QueryCounters](../profiling/querycounters.md)|Przedstawia listę prawidłowych liczników procesora dla bieżącej maszyny.|
|[WinCounter](../profiling/wincounter.md) **:** *ścieżka*|Określa zdarzenie licznika wydajności systemu Windows, które ma zostać dołączone do danych znacznika profilu. Użyj tylko z **menu Start**.|
|[Autoznacznik](../profiling/automark.md) **:** *n*|Określa interwał czasu (w milisekundach) między zdarzeniami zbierania danych licznika wydajności systemu Windows. Używany z **WinCounter**.|
|[Zdarzenia](../profiling/events-vsperfcmd.md) **:**`option`|Kontroluje zbieranie danych o określonych zdarzeniach śledzenia zdarzeń systemu Windows (ETW). Dane ETW są zbierane do programu. plik *ITL* , który nie jest profilem danych (.* VSP*).|
|[Stan](../profiling/status.md)|Wyświetla stan profilera, informacje o procesach, które są aktualnie profilowane, oraz kont, które mają uprawnienia do sterowania profilerem.|
|[Zamknięcie](../profiling/shutdown.md)[**:** `n` ]|Zamyka plik danych profilowania i wyłącza Profiler.|
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Wznawia zbieranie danych po wywołaniu **VSPerfCmdGlobalOff**.|
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Kończy zbieranie wszystkich danych, ale nie kończy sesji profilowania.|
|[ProcessOn](../profiling/processon-and-processoff.md) **:**`pid`|Wznawia zbieranie danych dla określonego procesu, gdy profilowanie zostało wstrzymane przez wywołanie **VSPerfCmdProcessOff**.|
|[ProcessOff](../profiling/processon-and-processoff.md) **:**`pid`|Kończy zbieranie danych dla określonego procesu.|
|[ThreadOn i ThreadOff](../profiling/threadon-and-threadoff.md) **:** *TID*|Wznawia profilowanie określonego procesu po wstrzymaniu profilowania przez wywołanie do **VSPerfCmdThreadOff**. Używaj **ThreadOn** tylko w przypadku profilowania przy użyciu metody instrumentacji.|
|[ThreadOn i ThreadOff](../profiling/threadon-and-threadoff.md) **:** *TID*|Wstrzymuje profilowanie określonego wątku. Używaj **ThreadOff** tylko w przypadku profilowania przy użyciu metody instrumentacji.|
|[Mark](../profiling/mark.md) **:** _MarkNum_[**,**_MarkText_**]**|Wstawia znacznik do pliku danych profilowania z opcjonalnym tekstem.|

## <a name="sample-method-options"></a>Przykładowe opcje metody
 Poniższe opcje są dostępne tylko w przypadku korzystania z metody profilowania próbkowania.

|Opcja|Opis|
|------------|-----------------|
|[Uruchom](../profiling/launch.md) **:** *plik wykonywalny*|Uruchamia określoną aplikację i rozpoczyna profilowanie.|
|[Args](../profiling/args.md) **:** *argumenty*|Określa argumenty wiersza polecenia do przekazania do uruchomionej aplikacji.|
|[Konsola](../profiling/console.md)|Uruchamia określone polecenie w nowym oknie wiersza polecenia.|
|[Attach](../profiling/attach.md) **:** *PID*[**,**_PID_]|Rozpoczyna profilowanie określonych procesów. Procesy mogą być identyfikowane przez identyfikator procesu lub nazwę procesu.|
|[Odłącz](../profiling/detach.md)[**:**_PID_[,_PID_]]|Powoduje zatrzymanie profilowania określonych procesów. Procesy mogą być identyfikowane przez identyfikator procesu lub nazwę procesu. Jeśli żaden proces nie zostanie określony, profilowanie zostanie zatrzymane dla wszystkich procesów.|
|[GC](../profiling/gc-vsperfcmd.md)[**:**{**Allocation** `&#124;` **okres istnienia**alokacji}]|Zbiera dane alokacji pamięci .NET i okresu istnienia obiektu. Użyj tylko z opcją **VSPerfCmdLaunch** .|

### <a name="sample-interval-options"></a>Opcje interwału próbkowania
 Poniższe opcje określają typ i czas trwania interwałów próbkowania. Wartość domyślna to **Timer**. Licznik procesora można także określić jako interwał przy użyciu opcji **licznik** . Te opcje można określić tylko przy użyciu opcji **Uruchom** lub przy pierwszym **dołączeniu** sesji profilowania.

|Opcja|Opis|
|------------|-----------------|
|[PF](../profiling/pf.md)[**:**_n_]|Próbki na każdym n-tym błędzie strony (domyślnie 10).|
|[Sys](../profiling/sys-vsperfcmd.md)[**:**_n_]|Próbki na każdym n-tym wywołaniu systemu (domyślnie 10).|
|[Czasomierz](../profiling/timer.md)[**:**_n_]|Próbki na każdym n-tym cyklu procesora (domyślnie = 10000000).|

## <a name="service-component-and-kernel-mode-device-options"></a>Opcje składnika usługi i trybu jądra
 Poniższe opcje administratora obsługują profilowania składników usługi lub sterowników urządzeń trybu jądra. Opcje administratora ustawiają uprawnienia profilowania i kontrolują profilowaną usługę lub sterownik urządzenia.

 Opcje administratora należy wykonać w wierszu polecenia, który jest uruchamiany z poświadczeniami administracyjnymi.

|Opcja|Opis|
|------------|-----------------|
|**Administrator: zabezpieczenia**, \<**ALLOW&#124;DENY**> , *prawa*[ *prawo*],\<*User*&#124;*Group*>|Zezwala lub nie ma dostępu do usługi profilowania określonemu użytkownikowi lub grupie.<br /><br /> `Right`może to być:<br /><br /> CrossSession — umożliwia użytkownikowi dostęp do usługi w celu przeprowadzenia profilowania między sesjami.<br /><br /> SampleProfiling — umożliwia użytkownikowi uzyskiwanie dostępu do sterownika w celu włączenia profilowania próbkowania. Używane również do uzyskiwania dostępu do informacji o przejściach jądra podczas profilowania śledzenia.<br /><br /> FullAccess — umożliwia użytkownikowi CrossSession i SampleProfiling dostęp.|
|**Administrator: zabezpieczenia, lista**|Wyświetla bieżący stan usług profilowania i wyświetla listę uprawnień użytkownika.|
|**Administrator:**\<*Service*&#124;*Driver*>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**>|Uruchamia, kończy, instaluje lub Odinstalowuje składnik usługi profilowania (usługa) lub sterownik urządzenia trybu jądra (sterownika).|
|**Administrator:** \<*Service*&#124;*Driver*> **Autostart**\<**ON**&#124;**OFF**>|Włącza lub wyłącza automatyczne uruchamianie usługi profilowania (usługi) lub sterownika urządzenia trybu jądra (sterownika) po ponownym uruchomieniu.|

## <a name="vsperfcmd-driver"></a>VSPerfCmd
 Opcja **VSPerfCmd** = jest obecnie przestarzała. Użyj opcji **administracyjnych VSPerfCmd** dla tej funkcji.

## <a name="see-also"></a>Zobacz też
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfReport](../profiling/vsperfreport.md)
