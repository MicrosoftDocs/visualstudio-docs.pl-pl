---
title: Zabezpieczenia debugera | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: c1c56b3081f9e74ff9ab864639772c18bd758df6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686777"
---
# <a name="debugger-security"></a>Zabezpieczenia debugera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możliwość debugowania innego procesu daje użytkownikowi wyjątkowo szerokie uprawnienia, zwłaszcza w przypadku zdalnego debugowania. Złośliwy debuger może spowodować rozległe uszkodzenie na debugowanym komputerze.  
  
 Jednak wielu deweloperów nie zakłada, że zagrożenie bezpieczeństwa może również przepływać w odwrotnym kierunku. Złośliwy kod w procesie debugowanego obiektu może zagrażać bezpieczeństwu maszyny debugowania: istnieje wiele luk w zabezpieczeniach, które muszą być chronione.  
  
## <a name="security-best-practices"></a>Najlepsze praktyki w zakresie zabezpieczeń  
 Istnieje niejawna relacja zaufania między debugowanym kodem a debugerem. Jeśli chcesz debugować coś, należy również je uruchomić. Dolna linia polega na tym, że musisz mieć możliwość zaufania do elementów debugowania. Jeśli nie można go zaufać, nie należy go debugować lub należy go debugować z komputera, który można zagrażać, i w środowisku izolowanym.  
  
 Aby zmniejszyć potencjalną podatność na ataki, debugowanie powinno być wyłączone na maszynach produkcyjnych. Z tego samego powodu debugowanie nie powinno być nigdy włączone na czas nieokreślony.  
  
### <a name="managed-debugging-security"></a>Zabezpieczenia debugowania zarządzanego  
 Poniżej przedstawiono niektóre ogólne zalecenia dotyczące wszystkich zarządzanych debugowania.  
  
- Należy zachować ostrożność podczas dołączania do procesu niezaufanego użytkownika: po wykonaniu tej czynności należy założyć, że jest ona godna zaufania. Podczas próby dołączenia do procesu niezaufanego użytkownika zostanie wyświetlone potwierdzenie okna dialogowego ostrzeżenia o zabezpieczeniach z pytaniem, czy chcesz dołączyć do procesu. "Zaufani użytkownicy" obejmują użytkownika i zestaw standardowych użytkowników, które są powszechnie zdefiniowane na komputerach, na których zainstalowano .NET Framework, takich jak **ASPNET**, **LocalSystem**, **NetworkService**i **LocalService**. Aby uzyskać więcej informacji, zobacz [Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).  
  
- Należy zachować ostrożność podczas pobierania projektu z Internetu i ładowania go do programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Jest to bardzo ryzykowne, nawet bez debugowania. Gdy to zrobisz, zakładasz, że projekt i kod, który zawiera, są wiarygodne.  
  
  Aby uzyskać więcej informacji, zobacz [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md).  
  
### <a name="remote-debugging-security"></a>Zabezpieczenia debugowania zdalnego  
 Debugowanie lokalne jest ogólnie bezpieczniejsze niż debugowanie zdalne. Debugowanie zdalne zwiększa łączny obszar powierzchni, który może być sondowany.  
  
 Program Visual Studio Monitor zdalnego debugowania (msvsmon.exe) jest używany podczas zdalnego debugowania i istnieje kilka zaleceń dotyczących zabezpieczeń dotyczących jego konfigurowania. Preferowanym sposobem skonfigurowania trybu uwierzytelniania jest uwierzytelnianie systemu Windows, ponieważ tryb uwierzytelniania nie jest bezpieczny.  
  
 ![Okno dialogowe błędu](../debugger/media/dbg-err-remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")  
  
 W przypadku korzystania z trybu uwierzytelniania systemu Windows należy pamiętać, że udzielenie niezaufanego uprawnienia użytkownika do nawiązania połączenia z usługą msvsmon jest niebezpieczne, ponieważ użytkownik otrzymuje wszystkie uprawnienia na komputerze.  
  
 Nie Debuguj nieznanego procesu na komputerze zdalnym: istnieją potencjalne luki w zabezpieczeniach, które mogą mieć wpływ na maszynę z uruchomionym debugerem lub które mogą naruszyć msvsmon.exe, Monitor zdalnego debugowania programu Visual Studio. Jeśli konieczne jest debugowanie nieznanego procesu, należy przeprowadzić debugowanie lokalnie i użyć zapory, aby mieć zlokalizowane potencjalne zagrożenia.  
  
 Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).  
  
### <a name="web-services-debugging-security"></a>Zabezpieczenia debugowania usług sieci Web  
 Istnieje bezpieczniejsze debugowanie lokalne, ale ponieważ prawdopodobnie nie zostały [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zainstalowane na serwerze sieci Web, debugowanie lokalne może nie być praktyczne. Ogólnie rzecz biorąc, debugowanie usług sieci Web odbywa się zdalnie, z wyjątkiem sytuacji, w której zalecenia dotyczące zdalnego debugowania zabezpieczeń mają zastosowanie również do debugowania usług sieci Web. Poniżej przedstawiono kilka dodatkowych najlepszych rozwiązań. Aby uzyskać więcej informacji, zobacz [debugowanie usług sieci Web XML](https://msdn.microsoft.com/c900b137-9fbd-4f59-91b5-9c2c6ce06f00).  
  
- Nie należy włączać debugowania na serwerze sieci Web, którego zabezpieczenia zostały naruszone.  
  
- Przed debugowaniem upewnij się, że serwer sieci Web jest bezpieczny. Jeśli nie masz pewności, czy jest to bezpieczne, nie Debuguj.  
  
- Należy zachować szczególną ostrożność w przypadku debugowania usługi sieci Web, która jest dostępna w Internecie.  
  
### <a name="external-components"></a>Składniki zewnętrzne  
 Należy pamiętać o stanie zaufania zewnętrznych składników, z którymi korzysta Twój program, szczególnie jeśli kod nie został napisany. Należy również zwrócić uwagę na składniki, które [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mogą być używane przez debuger.  
  
### <a name="symbols-and-source-code"></a>Symbole i kod źródłowy  
 Dwa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Narzędzia, które wymagają zamyślenia o zabezpieczeniach, są następujące:  
  
- Serwer źródłowy, który udostępnia wersje kodu źródłowego z repozytorium kodu źródłowego. Jest to przydatne, gdy nie masz bieżącej wersji kodu źródłowego programu. [Ostrzeżenie o zabezpieczeniach: debuger musi wykonać niezaufane polecenie](../debugger/security-warning-debugger-must-execute-untrusted-command.md).  
  
- Serwer symboli, który służy do dostarczania symboli wymaganych do debugowania awarii podczas wywołania systemowego.  
  
  Zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)   
 [Ostrzeżenie o zabezpieczeniach: debuger musi wykonać niezaufane polecenie](../debugger/security-warning-debugger-must-execute-untrusted-command.md)
