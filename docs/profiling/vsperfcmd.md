---
title: Narzędzia VSPerfCmd | Dokumentacja firmy Microsoft
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab432c5dfe316dc540fdfe6937263bc12abc967c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990428"
---
# <a name="vsperfcmd"></a>VSPerfCmd
*VSPerfCmd.exe* narzędzie umożliwia uruchamianie i zatrzymywanie zbierania danych o wydajności. Używa następującej składni:  
  
```cmd  
VSPerfCmd [/U] [/options]  
```  
  
 W poniższych tabelach opisano *VSPerfCmd.exe* opcje narzędzia.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**U**|Dane wyjściowe przekierowanego konsoli są zapisywane jako Unicode. Musi być pierwsza opcja określona.|  
|[Rozpocznij](../profiling/start.md) **:** `mode`|Uruchamia usługę profilowania w określonym trybie.|  
|[Dane wyjściowe](../profiling/output.md) **:** `filename`|Określa nazwę pliku wyjściowego. Za pomocą tylko **Start**.|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Włącza profilowanie między sesjami Windows. Za pomocą tylko **Start**, **dołączyć**, **lub uruchom**.|  
|[Użytkownik](../profiling/user-vsperfcmd.md) **:**[`domain\`]`username`|Umożliwia dostęp do określonego konta do usługi profilera. Za pomocą tylko **Start**.|  
|[WaitStart](../profiling/waitstart.md)[**:**`n`]|Oczekuje na zainicjowanie rejestratora zbierania danych. Jeśli `n` jest określony, **VSPerfCmd** poczeka co najwyżej `n` sekund. Jeśli `n` nie zostanie określony, **VSPerfCmd** będzie czekać w nieskończoność. To ułatwia korzystanie z **VSPerfCmd** w ramach procesu wsadowego.|  
|[Licznik](../profiling/counter.md) **:** `cfg`|Gdy używany jest przykładowy metoda profilowania, określa licznika procesora CPU oraz liczby zdarzeń do użycia jako interwał próbkowania. Można przykładowe tylko jedna wartość licznika.<br /><br /> Gdy jest używana metoda profilowania Instrumentacja, określa on Licznik użycia Procesora, mają być zbierane w każdym punkcie instrumentacji. Za pomocą tylko **Start:**`Trace`, **dołączyć**, lub **Uruchom**.|  
|[QueryCounters](../profiling/querycounters.md)|Wyświetla listę prawidłowych liczników procesora CPU dla bieżącej maszyny.|  
|[WinCounter](../profiling/wincounter.md) **:** *ścieżki*|Określa zdarzenia licznika wydajności Windows obejmujący z danymi znacznika profilu. Za pomocą tylko **Start**.|  
|[AutoMark](../profiling/automark.md) **:** *n*|Określa przedział czasu (w milisekundach) między zdarzeniami zbierania danych licznika wydajności Windows. Za pomocą **WinCounter**.|  
|[Zdarzenia](../profiling/events-vsperfcmd.md) **:** `option`|Określa, kolekcji określone zdarzenia śledzenie zdarzeń dla Windows (ETW). Dane ETW są zbierane do. *itl* pliku, który nie jest danych profilowania (. *Vsp*) pliku.|  
|[Status](../profiling/status.md)|Wyświetla stan profiler, informacje dotyczące procesów, które są aktualnie profilowane i kont, które mają uprawnienia do kontrolowania profilera.|  
|[Zamknięcie](../profiling/shutdown.md)[**:**`n`]|Zamyka plik danych profilowania i wyłącza profilera.|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Wznawia zbieranie danych po wywołaniu **VSPerfCmdGlobalOff**.|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Zatrzymuje wszystkie zbieranie danych, ale nie kończy się sesja profilowania.|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|Wznawia działanie funkcji zbierania danych dla określonego procesu, po profilowanie została wstrzymana przez wywołanie **VSPerfCmdProcessOff**.|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|Zatrzymuje zbieranie danych dla określonego procesu.|  
|[ThreadOn i ThreadOff](../profiling/threadon-and-threadoff.md) **:** *identyfikatora tid*|Wznawia profilowania dla określonego procesu po profilowanie została wstrzymana przez wywołanie **VSPerfCmdThreadOff**. Użyj **ThreadOn** tylko wtedy, gdy profilowanie przy użyciu metody instrumentacji.|  
|[ThreadOn i ThreadOff](../profiling/threadon-and-threadoff.md) **:** *identyfikatora tid*|Wstrzymano profilowanie dla określonego wątku. Użyj **ThreadOff** tylko wtedy, gdy profilowanie przy użyciu metody instrumentacji.|  
|[Oznacz](../profiling/mark.md) **:** _MarkNum_[**,**_Tekst_znacznika_**]**|Wstawia znacznik do pliku danych profilowania z opcjonalnym tekstem.|  
  
## <a name="sample-method-options"></a>Przykładowe opcje metody  
 Poniższe opcje są dostępne tylko w przypadku, gdy używana jest metoda profilowania próbkowanie.  
  
|Opcja|Opis|  
|------------|-----------------|  
|[Uruchom](../profiling/launch.md) **:** *pliku wykonywalnego*|Uruchamia określoną aplikację i rozpoczyna się profilowanie.|  
|[Argumenty](../profiling/args.md) **:** *argumenty*|Określa argumenty wiersza polecenia do przekazania do uruchomionej aplikacji.|  
|[Console](../profiling/console.md)|Uruchamia określone polecenie w nowym oknie wiersza polecenia.|  
|[Dołącz](../profiling/attach.md) **:** *IDENTYFIKATOR PID*[**,**_PID_]|Rozpoczyna się profilowanie określonych procesów. Procesy można zidentyfikować za pomocą Identyfikatora procesu lub nazwę procesu.|  
|[Odłącz](../profiling/detach.md)[**:**_PID_[,_PID_]]|Zatrzymuje profilowanie określonych procesów. Procesy można zidentyfikować za pomocą Identyfikatora procesu lub nazwę procesu. Jeśli żaden proces nie zostanie określony, profilowanie zostało zatrzymane dla wszystkich procesów.|  
|[GC](../profiling/gc-vsperfcmd.md)[**:**{**alokacji**`&#124;`**okres istnienia**}]|Służy do zbierania danych pamięci .NET alokacji i obiekt okresu istnienia. Za pomocą tylko **VSPerfCmdLaunch** opcji.|  
  
### <a name="sample-interval-options"></a>Przykładowe opcje interwału  
 Poniższe opcje, określ typ i czas trwania próbkowania odstępach czasu. Wartość domyślna to **czasomierza**. Można również określić licznika Procesora jako interwał, za pomocą **licznika** opcji. Te opcje można określić tylko z **Uruchom** lub z pierwszym **Dołącz** sesji profilowania.  
  
|Opcja|Opis|  
|------------|-----------------|  
|[PF](../profiling/pf.md)[**:**_n_]|Próbki na każdym n tej strony błędów (domyślny = 10).|  
|[Sys](../profiling/sys-vsperfcmd.md)[**:**_n_]|Przykłady w przypadku każdego wywołania n tego systemu (domyślne = 10).|  
|[Czasomierz](../profiling/timer.md)[**:**_n_]|Próbki na każdy procesor n tym cyklu (domyślny 10 000 000).|  
  
## <a name="service-component-and-kernel-mode-device-options"></a>Usługa składnika i jądra tryb opcje urządzenia  
 Następujące opcje administratora pomocy technicznej profilowania składniki usługi lub sterowniki urządzeń trybu jądra. Opcje administratora Ustawianie uprawnień profilowania i kontrolować profilowanych usługi lub sterownika urządzenia.  
  
 Opcje administratora musi zostać wykonana w wierszu polecenia, w którym jest uruchomiony przy użyciu poświadczeń administracyjnych.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Admin:Security**, \< **Zezwalaj&#124;ODMÓW**>, *po prawej stronie*[ *po prawej stronie*], \< *użytkownika* &#124; *Grupy*>|Zezwala lub nie zezwala określonemu użytkownikowi lub grupie dostępu do usług profilowania.<br /><br /> `Right` może być:<br /><br /> CrossSession — zapewnia użytkownikowi dostęp do usługi w celu krzyżowego sesji profilowania.<br /><br /> SampleProfiling — daje użytkownikowi dostęp do sterownika, aby włączyć profilowanie próbkowania. Umożliwia również dostęp do informacji przejścia jądra podczas profilowania śledzenia.<br /><br /> FullAccess — zapewnia dostęp zarówno CrossSession, jak i SampleProfiling.|  
|**Admin:Security, lista**|Wyświetla listę bieżącego stanu usług profilowania i wyświetla listę uprawnień użytkownika.|  
|**Administrator:** \<*Usługa*&#124;*sterownika*>\<**START**&#124;**ZATRZYMAĆ**&#124;**instalacji** &#124; **DEZINSTALACJI**>|Uruchamia, zatrzymuje, instaluje lub odinstalowuje składnik usługi profilowania (service) lub sterownik urządzenia trybu jądra (driver).|  
|**Administrator:** \<*Usługa*&#124;*sterownika*>**AutoStart**\<**ON**&#124;**OFF**>|Włącza lub wyłącza automatyczne uruchamianie usługi profilowania (service) lub sterownik urządzenia trybu jądra (driver) po ponownym uruchomieniu.|  
  
## <a name="vsperfcmd-driver"></a>Driver/Driver narzędzia VSPerfCmd  
 **Driver/Driver narzędzia VSPerfCmd** opcja jest obecnie przestarzała. Użyj **Admin narzędzia VsPerfCmd** opcje dla tej funkcji.  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzie VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)