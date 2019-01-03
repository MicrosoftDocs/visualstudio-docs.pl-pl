---
title: Zabezpieczenia debugera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], security
- debugger, security
- security [Visual Studio], debugging best practices
ms.assetid: d4fc3c43-e844-419c-8dbb-551cc2a9b09e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14389ec72094b2f6642c74b93bdd5f8a076f6387
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842796"
---
# <a name="debugger-security"></a>Zabezpieczenia debugera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możliwość debugowania inny proces zapewnia bardzo szerokie uprawnienia, których możesz nie mieliby, szczególnie w przypadku debugowania zdalnego. Złośliwy debuger może skutkować problemem dla całego zniszczenia na maszynie debugowany.  
  
 Jednak wielu programistów nie należy pamiętać, że zagrożenia zabezpieczeń również może przepływać w odwrotnym kierunku. Istnieje możliwość, że złośliwy kod obiektu debugowanego procesu w celu zagrozić bezpieczeństwu komputer debugowania: kilka, które muszą być chronione przed lukami w zabezpieczeniach.  
  
## <a name="security-best-practices"></a>Najlepsze praktyki w zakresie zabezpieczeń  
 Istnieje relacja nawiązywanie niejawnych relacji zaufania między kodem, który debugujesz i debugera. Gdy zgadzasz się na coś debugowania, również należy gotowi do jej uruchomienia. Mierzenie to, że użytkownik musi być zapewnienie zaufania wobec jest debugowany. Jeśli nie ufasz, następnie należy nie jej debugowania lub należy debugować ją na komputerze, który można pozwolić sobie na zagrozić i w środowisku izolowanym.  
  
 W celu zmniejszenia potencjalny obszar ataków, debugowanie powinno być wyłączone na komputerach produkcyjnych. Z tego samego powodu debugowanie powinno nigdy nie być włączone na czas nieokreślony.  
  
### <a name="managed-debugging-security"></a>Zarządzanie debugowaniem zabezpieczeń  
 Poniżej przedstawiono ogólne zalecenia, które mają zastosowanie do wszystkich zarządzanych debugowania.  
  
- Należy zachować ostrożność podczas dołączania do procesu niezaufanego użytkownika: Jeśli tak zrobisz, zakładać, że jest zaufane. Podczas próby dołączyć do procesu niezaufanego użytkownika potwierdzenia okno dialogowe Ostrzeżenie zabezpieczeń będą wyświetlane pytaniem, czy chcesz dołączyć do procesu. "Zaufanych użytkowników" należy uwzględnić, a zestaw standardowych użytkowników często definiowane na maszynach mających systemu.NET Framework, takich jak **aspnet**, **localsystem**, **networkservice**, i **localservice**. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub niepewne, nie dołączaj do tego procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).  
  
- Należy zachować ostrożność podczas pobierania z projektem Internetu i załadowanie go do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Jest to bardzo ryzykowne nawet bez debugowania. Gdy to zrobisz, są przy założeniu projektu i kodu, który zawiera są godne zaufania.  
  
  Aby uzyskać więcej informacji, zobacz [debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md).  
  
### <a name="remote-debugging-security"></a>Zdalne debugowanie zabezpieczeń  
 Debugowanie lokalne jest zwykle bezpieczniejsze niż zdalnego debugowania. Zdalne debugowanie zwiększa całkowity obszar powierzchni, który może być sondowany.  
  
 Zdalny Monitor debugowania Visual Studio (msvsmon.exe) jest używany podczas zdalnego debugowania, wiąże się z kilku zalecenia dotyczące zabezpieczeń dla jego konfigurowania. Preferowany sposób, aby skonfigurować tryb uwierzytelniania jest uwierzytelnianie Windows, ponieważ tryb bez uwierzytelniania jest niebezpieczne.  
  
 ![Okno dialogowe błędu](../debugger/media/dbg-err-remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")  
  
 Podczas korzystania z trybu uwierzytelniania Windows należy pamiętać, że udzielanie uprawnień niezaufanego użytkownika do łączenia się polecenia msvsmon jest niebezpieczne, ponieważ użytkownik otrzymuje wszystkie uprawnienia na komputerze...  
  
 Nie Debuguj nieznany proces na maszynie zdalnej: istnieje potencjalne luki w zabezpieczeniach, może mieć wpływ na komputer z programem debuger lub który może spowodować naruszenie msvsmon.exe, zdalny Monitor debugowania Visual Studio. Jeśli bezwzględnie musisz debugować nieznany proces, spróbuj debugowania lokalnego, a za pomocą zapory, aby zachować wszystkie potencjalne zagrożenia zlokalizowane.  
  
 Aby uzyskać więcej informacji, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  
  
### <a name="web-services-debugging-security"></a>Zabezpieczenia debugowania usług sieci Web  
 Bezpieczniej jest Debuguj lokalnie, ale ponieważ prawdopodobnie nie masz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zainstalowany na serwerze sieci web, debugowanie lokalne może być niepraktyczne. Ogólnie rzecz biorąc debugowanie usług sieci Web jest wykonywane zdalnie, z wyjątkiem podczas tworzenia aplikacji, więc zalecenia dotyczące zdalnego debugowania zabezpieczeń dotyczą również usług sieci Web profilowanie. Poniżej przedstawiono pewne dodatkowe najlepsze rozwiązania. Aby uzyskać więcej informacji, zobacz [debugowanie usług XML sieci Web](http://msdn.microsoft.com/en-us/c900b137-9fbd-4f59-91b5-9c2c6ce06f00).  
  
-   Nie należy włączać debugowania na serwerze sieci Web, którego bezpieczeństwo zostało naruszone.  
  
-   Upewnij się, że wiesz, że serwer sieci Web są bezpieczne, przed jej debugowanie. Jeśli nie masz pewności, że jest to bezpieczne, nie debugować go.  
  
-   Uważaj, szczególnie Jeśli debugujesz usługi sieci Web, który jest uwidaczniany w Internecie.  
  
### <a name="external-components"></a>Składniki zewnętrzne  
 Należy pamiętać o stanu zaufania składników zewnętrznych, które program wchodzi w interakcję z, zwłaszcza, jeśli nie napisać kod. Ponadto należy pamiętać o składniki, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub użyć debugera.  
  
### <a name="symbols-and-source-code"></a>Symbole i kod źródłowy  
 Dwa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi, które wymagają myśleć o zabezpieczeniach są następujące:  
  
- Serwer źródłowy zapewnia wersje kodu źródłowego z repozytorium kodu źródłowego. Może to być przydatne, gdy nie masz bieżącą wersję kodu źródłowego programu. [Ostrzeżenie o zabezpieczeniach: Debuger musi wykonać polecenie niezaufane](../debugger/security-warning-debugger-must-execute-untrusted-command.md).  
  
- Serwer symboli służą do określania symbole potrzebnych do debugowania awarii podczas wywołania systemowego.  
  
  Zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub niepewne, nie dołączaj do tego procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)   
 [Ostrzeżenie o zabezpieczeniach: Debuger musi wykonać polecenie niezaufane](../debugger/security-warning-debugger-must-execute-untrusted-command.md)





