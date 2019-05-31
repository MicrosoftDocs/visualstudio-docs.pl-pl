---
title: Zdalne debugowanie platformy ASP.NET na zdalnym serwerze IIS 7.5 komputera | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446076"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wdrożyć aplikację sieci Web platformy ASP.NET do komputera systemu Windows Server z usługami IIS i skonfigurować je dla zdalnego debugowania. Ten przewodnik wyjaśnia, jak skonfigurować i konfigurowanie aplikacji programu Visual Studio 2015 MVC 4.5.2, wdrożyć ją w usługach IIS i dołączyć debuger zdalny z programu Visual Studio.

Procedury te zostały przetestowane na te konfiguracje serwera:
* Windows Server 2012 R2 oraz usług IIS 10
* Windows Server 2008 R2 i IIS 7.5

Większość informacji w tym artykule dotyczą również zdalne debugowanie aplikacji ASP.NET Core, z tą różnicą, że wdrażanie aplikacji ASP.NET core jest inna i wymaga wykonania dodatkowych czynności. Aby wdrożyć aplikację ASP.NET Core w usługach IIS, należy ukończyć wszystkie sekcje [w tym artykule](https://docs.asp.net/en/latest/publishing/iis.html).

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Wymagania wstępne: Zainstaluj zdalny debuger na komputerze z systemem Windows Server

Aby uzyskać instrukcje dotyczące sposobu pobierania zdalnego debugera na komputerze z systemem Windows Server, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

Aby zrobić, zdalne debugowanie aplikacji ASP.NET, możesz Uruchom aplikację zdalny debuger jako Administrator lub uruchomić zdalny debuger jako usługę. Szczegółowe informacje na temat uruchamiania zdalnego debugera jako usługi można znaleźć w [zdalne debugowanie](../debugger/remote-debugging.md).

Po zainstalowaniu, upewnij się, że debuger zdalny jest uruchomiony na komputerze docelowym. (Jeśli nie jest dostępne, wyszukaj **zdalny debuger** w **Start** menu. ) W oknie debugera zdalnego wygląda następująco. (domyślny numer portu jest 4020)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Tworzenie aplikacji na komputerze programu Visual Studio  
  
1. Utwórz nową aplikację MVC ASP.NET. (**Plik / nowy / Project**, a następnie wybierz **Visual C# / Web / aplikacja sieci Web ASP.NET** . W **ASP.NET 4.5.2** szablony zaznacz **MVC**. Upewnij się, że **Host w chmurze** nie jest zaznaczona w sekcji platformy Azure. Nadaj projektowi nazwę **MyMVC**.)
1. Otwórz plik HomeController.cs, a następnie ustaw punkt przerwania `About()` metody.
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Publikuj**.
1. Dla **wybierz lokalizację docelową publikowania**, wybierz opcję **niestandardowe** i nazwij ten profil **MyMVC**. Kliknij przycisk **Dalej**.
1. Na **połączenia** kartę, należy ustawić **metody publikowania** pole **System plików** i **lokalizacja docelowa** pola do katalogu lokalnego. Kliknij przycisk **Dalej**.

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. Ustaw konfigurację **debugowania**. Kliknij przycisk **publikowania**.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    Aplikacja, powinny być publikowane do katalogu lokalnego.

## <a name="BKMK_deploy_asp_net"></a> Wdrażanie aplikacji ASP.NET na komputerze zdalnym w systemie Windows Server

 W tej sekcji założono, że komputer z systemem Windows Server ma już włączoną usługą IIS. W systemie Windows Server 2012 R2, zobacz [konfiguracji programu IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) Aby włączyć program IIS. (Inne sekcje w tym artykule można pominąć, jeśli nie chcesz wdrożyć aplikację ASP.NET Core. Dla platformy ASP.NET Core postępuj zgodnie z instrukcjami w artykule, aby wdrożyć aplikację zamiast kroki opisane w tym miejscu.)
1. Instalowanie programu ASP.NET, użyj składników platformy sieci Web, aby zainstalować program ASP.NET 4.5 (z węzła serwera w systemie Windows Server 2012 R2, wybierz **pobieranie nowych składników platformy sieci Web** i wyszukaj program ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    W systemie Windows Server 2008 R2 zainstaluj platformy ASP.NET 4, zamiast tego za pomocą tego polecenia:   **C:\Windows\Microsoft.NET\Framework(64)\v4.0.30319\aspnet_regiis.exe -ir**
1. Skopiuj katalog projektu ASP.NET z komputera, program Visual Studio do katalogu lokalnego (którym Zadzwonimy **C:\Publish**) na komputerze z systemem Windows Server. Można ręcznie skopiować projektu, użyj polecenia Xcopy, narzędzie Web Deploy, Robocopy, programu Powershell lub innych opcji.

    > [!CAUTION]
    > Jeśli musisz wprowadzić zmiany w kodzie lub ponownej kompilacji, należy ponownie opublikować i powtórz ten krok. Plik wykonywalny, który został skopiowany na komputerze zdalnym musi dokładnie odpowiadać, lokalne źródła i symboli.
1. Upewnij się, że plik web.config zawiera poprawną wersję programu .NET Framework.  Na przykład wersja programu .NET Framework, instalowany domyślnie w systemie Windows Server 2008 R2 jest 4.0.30319, ale utworzyliśmy platformy ASP.NET 4.5.2 wersji. Aplikacja ASP.NET 4.0 jest uruchomiona na komputerze z systemem Windows Server, musisz zmienić wersję:
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```

1. Otwórz **Internet Information Services (IIS) Manager** i przejdź do **witryn**.
1. Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** a następnie wybierz węzeł **Add Application**.
1. Ustaw **Alias** pole **MyMVC** i pole puli aplikacji do **ASP.NET v4.0** (ASP.NET 4.5 nie jest opcją dla puli aplikacji). Ustaw **ścieżkę fizyczną** do **C:\Publish** (której skopiowany katalogu projektu programu ASP.NET).

    >[!NOTE] 
    > W przypadku aplikacji platformy ASP.NET Core Ustaw pole puli aplikacji **bez kodu zarządzanego**.
1. Testowanie wdrożenia, klikając prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **Przeglądaj**.
    Jeśli aplikacja została wdrożona pomyślnie, zostanie wyświetlona strona sieci web.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Dołącz do aplikacji platformy ASP.NET z komputera z programu Visual Studio

1. Na komputerze programu Visual Studio, otwórz **MyMVC** rozwiązania.
1. W programie Visual Studio, kliknij przycisk **debugowanie / dołączanie do procesu** (**Ctrl + Alt + P**).
1. Ustaw pole kwalifikator  **\<nazwy komputera zdalnego >: 4020**.
1. Kliknij przycisk **Odśwież**.
    Powinien zostać wyświetlony niektóre procesy, które są wyświetlane w **dostępne procesy** okna.

    Jeśli nie widzisz wszystkie procesy, spróbuj przy użyciu adresu IP zamiast nazwy komputera zdalnego (port jest wymagany). Użyj `ipconfig` w wierszu polecenia, aby uzyskać adres IPv4.
1. Sprawdź **Pokaż procesy wszystkich użytkowników**.
1. Wyszukaj **w3wp.exe** i kliknij przycisk **Dołącz**.

     Aby szybko znaleźć nazwę procesu, wpisz pierwszą literę procesu.
     
    >[!NOTE]
    > W przypadku aplikacji ASP.NET Core wybierz proces dnx.exe zamiast w3wp.exe. (Ta nazwa procesu mogą ulec zmianie w kolejnej wersji).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Otwórz witrynę sieci Web na komputerze zdalnym. W przeglądarce przejdź do **http://\<nazwy komputera zdalnego >** .
    
    Powinna zostać wyświetlona strona sieci web platformy ASP.NET.
1. Na stronie sieci web platformy ASP.NET, kliknij link, aby **o** strony.

    W programie Visual Studio powinny trafiony punkt przerwania.
