---
title: Wdrażanie na folder lokalny
description: Wdrażanie aplikacji do folderu lokalnego
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 3fa0569739ee81ec4b2aa0eec8157068ffc949cd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407783"
---
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Publikuj** (formularzy sieci Web **publikowania aplikacji sieci Web**).

    Jeśli wcześniej skonfigurowano żadnych profilów publikowania **Publikuj** zostanie wyświetlone okienko. Kliknij przycisk **nowy profil**.

1. W **Publikuj** okno dialogowe, wybierz opcję **folderu**, kliknij przycisk **Przeglądaj**i Utwórz nowy folder **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    W przypadku aplikacji formularzy sieci Web wybierz **niestandardowe** w oknie dialogowym Publikowanie, wprowadź nazwę profilu, a następnie wybierz **OK**.

1. Kliknij przycisk **Utwórz profil** na liście rozwijanej (**Publikuj** jest wartością domyślną).

1. W **Publikuj** okno dialogowe, kliknij przycisk **ustawienia** połączyć, a następnie wybierz pozycję **ustawienia** kartę.

1. Ustaw konfigurację **debugowania**, wybierz opcję **Usuń wszystkie istniejące pliki przez opublikowaniem**, a następnie kliknij przycisk **Zapisz**.

    > [!NOTE]
    > Jeśli używasz kompilację wydania, można wyłączyć debugowania w pliku web.config po opublikowaniu.

1. Kliknij przycisk **publikowania**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")

    Aplikacja publikuje **debugowania** konfigurację projektu do folderu lokalnego. Postęp pokazuje, w oknie danych wyjściowych.

1. Skopiuj katalog projektu platformy ASP.NET z komputera programu Visual Studio do katalogu lokalnego, skonfigurować dla aplikacji platformy ASP.NET (w tym przykładzie **C:\Publish**) na komputerze z systemem Windows Server. W tym samouczku przyjęto założenie, kopiowane są ręcznie, ale można użyć innych narzędzi, takich jak program PowerShell, polecenia Xcopy lub Robocopy.

    > [!CAUTION]
    > Jeśli musisz wprowadzić zmiany w kodzie lub ponownej kompilacji, należy ponownie opublikować i powtórz ten krok. Plik wykonywalny, który został skopiowany na komputerze zdalnym musi dokładnie odpowiadać, lokalne źródła i symboli.    Jeśli tego nie zrobi to otrzymasz `cannot find or open the PDB file` ostrzeżenie w programie Visual Studio, podczas próby debugowania procesu.

1. W systemie Windows Server Sprawdź, czy aplikacja może działa poprawnie, otwierając aplikację w przeglądarce.

    Jeśli aplikacja nie działa poprawnie, może być niezgodność między wersją platformy ASP.NET jest zainstalowany na serwerze i komputerze programu Visual Studio lub może wystąpić problem z konfiguracją usług IIS lub witryny sieci Web. Sprawdź ponownie wcześniejszych krokach.
