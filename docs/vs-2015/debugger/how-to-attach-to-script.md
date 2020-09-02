---
title: 'Instrukcje: dołączanie do skryptu | Microsoft Docs'
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
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 719654916087e7c7f4249ff52abbed628a2c56a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704495"
---
# <a name="how-to-attach-to-script"></a>Porady: dołączanie do skryptu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie wyjaśniono, jak ręcznie dołączyć debuger programu Visual Studio do pliku skryptu w celu debugowania.  
  
### <a name="to-attach-to-a-running-process"></a>Aby dołączyć do uruchomionego procesu  
  
1. W menu **debugowanie** wybierz **Dołącz do procesu**. (Jeśli żaden projekt nie jest otwarty, wybierz opcję **Dołącz do procesu** w menu **Narzędzia** .)  
  
2. W oknie dialogowym **Dołącz do procesu** Sprawdź listę **dostępne procesy** i Znajdź proces skryptu, do którego chcesz dołączyć. Można zidentyfikować procesy skryptów, przeglądając kolumnę **Type** .  
  
   1. Jeśli proces, który ma być debugowany, jest uruchomiony na innym komputerze, należy najpierw wybrać komputer zdalny. Aby uzyskać więcej informacji, zobacz [How to: Select a Remote Computer](https://msdn.microsoft.com/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
   2. Jeśli proces jest uruchomiony przy użyciu innego konta użytkownika, zaznacz pole wyboru **Pokaż procesy dla wszystkich użytkowników** .  
  
   3. Jeśli masz połączenie za pomocą **Podłączanie pulpitu zdalnego**, zaznacz pole wyboru **Pokaż procesy we wszystkich sesjach** .  
  
3. Kliknij proces, do którego chcesz dołączyć.  
  
4. W polu **Dołącz do** powinien zostać wyświetlony **kod skryptu** lub **automatyczny: kod skryptu**. Jeśli zobaczysz coś innego, wykonaj następujące kroki:  
  
   1. Kliknij pozycję **Wybierz**.  
  
   2. W oknie dialogowym **Wybierz typ kodu** kliknij pozycję **Debuguj te typy kodu** i wybierz pozycję **skrypt**.  
  
   3. Kliknij przycisk **OK**.  
  
5. Kliknij przycisk **Dołącz**.  
  
    W tym momencie może zostać wyświetlone ostrzeżenie informujące o tym, że debugowanie skryptów jest wyłączone w programie Internet Explorer. W takim przypadku zobacz [Ostrzeżenie: debugowanie skryptów jest wyłączone](../debugger/warning-script-debugging-disabled.md).  
  
   Lista **dostępne procesy** jest wyświetlana automatycznie po otwarciu okna dialogowego **procesy** . Procesy można uruchamiać i zatrzymywać w tle, gdy okno dialogowe jest otwarte. W związku z tym zawartość może być niezawsze aktualna. Można odświeżyć listę w dowolnym momencie, aby wyświetlić bieżącą listę procesów, naciskając przycisk **Odśwież** .  
  
   Podczas debugowania można dołączyć do wielu programów, ale tylko jeden program jest aktywny w debugerze w dowolnym momencie. Można ustawić aktywny program na pasku narzędzi Lokalizacja debugowania. Aby uzyskać więcej informacji, zobacz [How to: Set the current Process](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
   Wszystkie polecenia wykonywania menu **debugowania** mają wpływ na aktywny program. Można przerwać wszystkie debugowane programy z okna dialogowego procesy. Zobacz [Używanie punktów przerwania](../debugger/using-breakpoints.md).  
  
> [!NOTE]
> W przypadku próby dołączenia do procesu należącego do niezaufanego konta użytkownika zostanie wyświetlone potwierdzenie okna dialogowego z ostrzeżeniem o zabezpieczeniach. Aby uzyskać więcej informacji, zobacz [Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).  
  
 W niektórych przypadkach podczas debugowania w sesji usług terminalowych (Pulpit zdalny) na liście Dostępne procesy nie będą wyświetlane wszystkie dostępne procesy. W systemie [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] lub nowszym, jeśli używasz programu Visual Studio jako użytkownika ograniczonego, lista dostępne procesy nie będzie wyświetlać procesów uruchomionych w sesji 0, która jest używana w przypadku usług i innych procesów serwera, w tym w3wp.exe. Problem można rozwiązać przez uruchomienie programu Visual Studio w ramach konta administratora lub przez uruchomienie programu Visual Studio z poziomu konsoli serwera, a nie sesji usług terminalowych. Jeśli żadne z tych obejść nie jest możliwe, trzecią opcją jest dołączenie do procesu, wpisując vsjitdebugger.exe-p ProcessId w wierszu polecenia systemu Windows. Identyfikator procesu można określić za pomocą tlist.exe. Aby uzyskać tlist.exe, Pobierz i zainstaluj narzędzia debugowania dla systemu Windows, które są dostępne pod kątem [sprzętu Windows Developer Central](https://developer.microsoft.com/windows/hardware).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie skryptu po stronie klienta](../debugger/client-side-script-debugging.md)   
 [Dołącz do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)
