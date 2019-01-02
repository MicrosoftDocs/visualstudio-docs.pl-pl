---
title: 'Instrukcje: Dołączanie do skryptu | Dokumentacja firmy Microsoft'
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
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0fbdbf31c4ff504011a4ab80d50746d87ac3dac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858031"
---
# <a name="how-to-attach-to-script"></a>Instrukcje: Dołączanie do skryptu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie wyjaśniono, jak ręczne dołączenie debugera programu Visual Studio do pliku skryptu w celu debugowania.  
  
### <a name="to-attach-to-a-running-process"></a>Aby dołączyć do uruchomionego procesu  
  
1. Na **debugowania** menu, wybierz **dołączyć do procesu**. (Jeśli projekt nie jest otwarty, wybierz **dołączyć do procesu** na **narzędzia** menu.)  
  
2. W **dołączyć do procesu** okno dialogowe, przyjrzeć **dostępne procesy** chcesz dołączyć do listy i Znajdź skryptu procedur. Procesy skryptu można zidentyfikować, analizując **typu** kolumny.  
  
   1.  Jeśli proces, który chcesz debugować jest uruchomiony na innym komputerze, musisz najpierw wybrać komputera zdalnego. Aby uzyskać więcej informacji, zobacz [jak: Wybierz komputer zdalny](http://msdn.microsoft.com/en-us/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
   2.  Jeśli proces działa przy użyciu konta innego użytkownika, wybierz opcję **Pokaż procesy wszystkich użytkowników** pole wyboru.  
  
   3.  Jeśli są połączone za pośrednictwem **Podłączanie pulpitu zdalnego**, wybierz opcję **Pokaż procesy we wszystkich sesjach** pole wyboru.  
  
3. Kliknij proces, który chcesz dołączyć do.  
  
4. W **dołączyć do** polu, powinien zostać wyświetlony **kod skryptu** lub **automatyczne: Kod skryptu**. Jeśli widzisz czymkolwiek, wykonaj następujące kroki:  
  
   1.  Kliknij przycisk **wybierz**.  
  
   2.  W **Wybieranie typu kodu** okno dialogowe, kliknij przycisk **debugowania tych typów kodu** i wybierz **skryptu**.  
  
   3.  Kliknij przycisk **OK**.  
  
5. Kliknij przycisk **dołączyć**.  
  
    W tym momencie może być wyświetlone ostrzeżenie informujące o tym, że debugowanie skryptów jest wyłączone w programie Internet Explorer. Jeśli ma to miejsce, zobacz [ostrzeżenia: Debugowanie skryptu wyłączone](../debugger/warning-script-debugging-disabled.md).  
  
   **Dostępne procesy** zostanie wyświetlona lista automatycznie po otwarciu **procesy** okno dialogowe. Procesy można uruchomić i zatrzymać w tle, gdy jest otwarte okno dialogowe. W związku z tym zawartość może nie zawsze być nieaktualne. Można odświeżyć listę w dowolnym momencie, aby wyświetlić bieżącą listę procesów, naciskając klawisz **Odśwież** przycisku.  
  
   Można być dołączonym do wielu programów podczas debugowania, ale tylko jeden program jest aktywny w debugerze w dowolnym momencie. Można ustawić aktywny program w pasku narzędzi debugowania lokalizacji. Aby uzyskać więcej informacji, zobacz [jak: Ustaw bieżący proces](http://msdn.microsoft.com/en-us/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
   Wszystkie **debugowania** poleceń menu wpływają na aktywny program. W oknie dialogowym procesów, może przerwać dowolnego debugowanego programu. Zobacz [używanie punktów przerwania](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Jeśli próbujesz dołączyć do procesu, którego właścicielem jest niezaufane konto użytkownika, pojawi się ostrzeżenie okna dialogowego potwierdzenia zabezpieczeń. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub niepewne, nie dołączaj do tego procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).  
  
 W niektórych przypadkach podczas debugowania w sesji usług terminalowych (pulpitu zdalnego), lista dostępnych procesów nie będą wyświetlane wszystkie dostępne procesy. Na [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] lub nowsze wersje, jeśli używasz programu Visual Studio jako użytkownik, lista dostępnych procesów będą wyświetlały procesy uruchomione w sesji 0, które jest używane w przypadku usług i innych procesów serwera, w tym w3wp.exe. Problem można rozwiązać, uruchamiając program Visual Studio przy użyciu konta administratora lub przez uruchomienie programu Visual Studio z konsoli serwera zamiast sesji usług terminalowych. Jeśli żadna z tych obejść nie jest możliwe, trzecią opcją jest dołączenie do procesu, wpisując polecenie vsjitdebugger.exe -p ProcessId w wierszu polecenia Windows. Za pomocą tlist.exe, należy określić identyfikator procesu. Aby uzyskać tlist.exe, Pobierz i zainstaluj debugowanie Tools for Windows, dostępne pod adresem [Windows Hardware Developer Central](http://go.microsoft.com/fwlink/?linkid=1651).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie skryptu po stronie klienta](../debugger/client-side-script-debugging.md)   
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub niepewne, nie dołączaj do tego procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)



