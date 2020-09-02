---
title: Zdalne debugowanie ASP.NET na zdalnym komputerze z usługami IIS 7,5 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c43f392cddfd5ea36180d9b2675db82469f86ce0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807154"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikację sieci Web ASP.NET można wdrożyć na komputerze z systemem Windows Server przy użyciu usług IIS i skonfigurować ją na potrzeby zdalnego debugowania. W tym przewodniku wyjaśniono, jak skonfigurować i skonfigurować aplikację Visual Studio 2015 MVC 4.5.2, wdrożyć ją w usługach IIS i dołączyć zdalny debuger z programu Visual Studio.

Te procedury zostały przetestowane na tych konfiguracjach serwera:
* Windows Server 2012 R2 i IIS 10
* Windows Server 2008 R2 i IIS 7,5

Większość informacji w tym artykule dotyczy również debugowania zdalnego ASP.NET Core aplikacji, z wyjątkiem tego, że wdrażanie aplikacji ASP.NET Core jest różne i wymaga dodatkowych kroków. Aby wdrożyć aplikację ASP.NET Core w usługach IIS, należy wykonać wszystkie sekcje [tego artykułu](https://docs.asp.net/en/latest/publishing/iis.html).

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Wymagania wstępne: Instalowanie zdalnego debugera na komputerze z systemem Windows Server

Aby uzyskać instrukcje dotyczące pobierania zdalnego debugera na komputerze z systemem Windows Server, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).

Aby przeprowadzić zdalne debugowanie aplikacji ASP.NET, możesz uruchomić aplikację Remote Debugger jako administrator lub uruchomić zdalny debuger jako usługę. Szczegóły dotyczące sposobu uruchamiania zdalnego debugera jako usługi można znaleźć w temacie [debugowanie zdalne](../debugger/remote-debugging.md).

Po zainstalowaniu programu upewnij się, że zdalny debuger jest uruchomiony na komputerze docelowym. (Jeśli nie jest, Wyszukaj **zdalny debuger** w menu **Start** . ) Okno debugera zdalnego wygląda następująco. (4020 jest domyślnym numerem portu)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Tworzenie aplikacji na komputerze z Visual Studio  
  
1. Utwórz nową aplikację MVC ASP.NET. (**Plik/nowy/projekt**, a następnie wybierz pozycję **aplikacja sieci Web Visual C#/Web/ASP.NET** . W sekcji Szablony **ASP.NET 4.5.2** wybierz pozycję **MVC**. Upewnij się, że nie wybrano **hosta w chmurze** w sekcji Azure. Nazwij projekt **MyMVC**.)
1. Otwórz plik HomeController.cs i ustaw punkt przerwania w `About()` metodzie.
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Publikuj**.
1. Dla **opcji wybierz cel publikacji**wybierz pozycję **niestandardowe** i nazwij profil **MyMVC**. Kliknij przycisk **Dalej**.
1. Na karcie **połączenie** ustaw wartość pola **Publikuj metodę** na **system plików** i pole **Lokalizacja docelowa** do katalogu lokalnego. Kliknij przycisk **Dalej**.

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. Ustaw konfigurację na **Debuguj**. Kliknij przycisk **Opublikuj**.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    Aplikacja powinna zostać opublikowana w katalogu lokalnym.

## <a name="deploy-the-aspnet-application-on-the-windows-server-remote-computer"></a><a name="BKMK_deploy_asp_net"></a> Wdrażanie aplikacji ASP.NET na komputerze zdalnym z systemem Windows Server

 W tej sekcji założono, że na komputerze z systemem Windows Server włączono już usługi IIS. W systemie Windows Server 2012 R2 zapoznaj się z tematem [Konfiguracja usług IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) , aby włączyć usługi IIS. (Możesz pominąć inne sekcje tego artykułu, chyba że próbujesz wdrożyć aplikację ASP.NET Core. Aby uzyskać ASP.NET Core, wykonaj kroki opisane w artykule, aby wdrożyć aplikację zamiast kroków opisanych tutaj.)
1. Zainstaluj ASP.NET Użyj składników platformy sieci Web, aby zainstalować ASP.NET 4,5 (z węzła serwera w systemie Windows Server 2012 R2, wybierz pozycję **Pobierz nowe składniki platformy sieci Web** , a następnie wyszukaj ciąg ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    W systemie Windows Server 2008 R2 Zainstaluj ASP.NET 4 zamiast tego za pomocą tego polecenia:   **C:\Windows\Microsoft.NET\Framework (64) \v4.0.30319\aspnet_regiis.exe-IR**
1. Skopiuj katalog projektu ASP.NET z komputera programu Visual Studio do katalogu lokalnego (który zostanie wywołany **C:\Publish**) na komputerze z systemem Windows Server. Projekt można skopiować ręcznie, użyć polecenia xcopy, Web Deploy, Robocopy, PowerShell lub innych opcji.

    > [!CAUTION]
    > Jeśli trzeba wprowadzić zmiany w kodzie lub skompilować ponownie, należy ponownie opublikować i powtórzyć ten krok. Plik wykonywalny skopiowany na komputer zdalny musi dokładnie pasować do lokalnego źródła i symboli.
1. Upewnij się, że w pliku web.config znajduje się poprawna wersja .NET Framework.  Na przykład wersja .NET Framework instalowana domyślnie w systemie Windows Server 2008 R2 to 4.0.30319, ale została utworzona wersja ASP.NET 4.5.2. Jeśli aplikacja ASP.NET 4,0 jest uruchomiona na komputerze z systemem Windows Server, należy zmienić wersję:
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```

1. Otwórz **menedżera Internet Information Services (IIS)** i przejdź do **witryny**.
1. Kliknij prawym przyciskiem myszy **domyślny węzeł witryny sieci Web** i wybierz polecenie **Dodaj aplikację**.
1. Ustaw pole **alias** na **MyMVC** , a pole Pula aplikacji na **ASP.NET v 4.0** (ASP.NET 4,5 nie jest opcją dla puli aplikacji). Ustaw **ścieżkę fizyczną** na **C:\Publish** (w którym skopiowano katalog projektu ASP.NET).

    >[!NOTE] 
    > W przypadku aplikacji ASP.NET Core ustaw wartość pola Pula aplikacji na **Brak kodu zarządzanego**.
1. Przetestuj wdrożenie, klikając prawym przyciskiem myszy pozycję **Domyślna witryna sieci Web** i wybierając pozycję **Przeglądaj**.
    Jeśli aplikacja została pomyślnie wdrożona, zostanie wyświetlona strona sieci Web.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Dołączanie do aplikacji ASP.NET z komputera z programu Visual Studio

1. Na komputerze z Visual Studio Otwórz rozwiązanie **MyMVC** .
1. W programie Visual Studio kliknij pozycję **Debuguj/Dołącz do procesu** (**Ctrl + Alt + P**).
1. Ustaw wartość pola kwalifikator na ** \<remote computer name> : 4020**.
1. Kliknij przycisk **Odśwież**.
    Niektóre procesy powinny być widoczne w oknie **dostępne procesy** .

    Jeśli nie widzisz żadnych procesów, spróbuj użyć adresu IP zamiast nazwy komputera zdalnego (port jest wymagany). Użyj `ipconfig` w wierszu polecenia, aby uzyskać adres IPv4.
1. Zaznacz opcję  **Pokaż procesy wszystkich użytkowników**.
1. Poszukaj **w3wp.exe** i kliknij przycisk **Dołącz**.

     Aby szybko znaleźć nazwę procesu, wpisz pierwszą literę procesu.
     
    >[!NOTE]
    > W przypadku aplikacji ASP.NET Core wybierz proces dnx.exe zamiast w3wp.exe. (Ta nazwa procesu może ulec zmianie w nadchodzącym wydaniu).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Otwórz witrynę sieci Web komputera zdalnego. W przeglądarce przejdź do **http:// \<remote computer name> **.
    
    Powinna zostać wyświetlona strona sieci Web ASP.NET.
1. Na stronie sieci Web ASP.NET kliknij link do strony about ( **informacje** ).

    Punkt przerwania powinien zostać trafiony w programie Visual Studio.
