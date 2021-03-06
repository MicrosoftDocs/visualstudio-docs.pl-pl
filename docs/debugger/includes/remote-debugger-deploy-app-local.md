---
title: Wdróż w folderze lokalnym
description: Wdrażanie aplikacji w folderze lokalnym
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: b6ceee76d8c24ccddb41e47c0865d96c79e6fc32
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249896"
---
1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Publikuj** (dla formularzy sieci Web, **Opublikuj aplikację sieci Web**).

    Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, zostanie wyświetlone okienko **Publikowanie** . Kliknij pozycję **Nowy profil**.

1. W oknie dialogowym **Publikowanie** wybierz pozycję **folder**, kliknij pozycję **Przeglądaj**, a następnie utwórz nowy folder **C:\Publish**.

   ::: moniker range=">=vs-2019"

   :::image type="content" source="../media/vs-2019/remotedbg-publish-local.png" alt-text="Zrzut ekranu przedstawiający okno dialogowe Wybieranie elementu docelowego publikowania w programie Visual Studio z folderem &quot;C:\Publish&quot; wybranym jako element docelowy publikowania.":::

   Kliknij przycisk **Zakończ** , aby zapisać profil publikowania.
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Zrzut ekranu przedstawiający okno dialogowe Wybieranie elementu docelowego publikowania w programie Visual Studio z folderem "bin\Release\Publish" wybranym jako element docelowy publikowania.](../media/remotedbg_publish_local.png)
   W przypadku aplikacji formularzy sieci Web wybierz pozycję **niestandardowe** w oknie dialogowym Publikowanie, wprowadź nazwę profilu, a następnie wybierz **przycisk OK**.

   Na liście rozwijanej kliknij pozycję **Utwórz profil** (wartość domyślna to **Opublikuj** ).
   ::: moniker-end

1. Przejdź do konfiguracji debugowania.

   ::: moniker range=">=vs-2019"
   Wybierz pozycję **Edytuj** , aby edytować profil, a następnie wybierz pozycję **Ustawienia**. Wybierz konfigurację **debugowania** , a następnie wybierz pozycję **Usuń dodatkowe pliki w miejscu docelowym** w obszarze Opcje **publikowania plików** .
   ::: moniker-end
   ::: moniker range="vs-2017"
   W oknie dialogowym **Ustawienia** Włącz debugowanie, klikając przycisk **dalej**, wybierz konfigurację **debugowania** , a następnie wybierz pozycję **Usuń dodatkowe pliki w miejscu docelowym** w obszarze Opcje **publikowania plików** .
   ::: moniker-end

   > [!NOTE]
   > Jeśli używasz kompilacji wydania, po opublikowaniu należy wyłączyć debugowanie w pliku *web.config* .

1. Kliknij przycisk **Opublikuj**.

    ![Zrzut ekranu przedstawiający kartę Ustawienia w oknie dialogowym Publikowanie. Konfiguracja jest ustawiona na Debuguj i wybrano przycisk Publikuj.](../media/remotedbg_publish_debug_config.png)

    Aplikacja publikuje konfigurację **debugowania** projektu w folderze lokalnym. Postęp jest wyświetlany w oknie danych wyjściowych.

1. Skopiuj katalog projektu ASP.NET z komputera programu Visual Studio do katalogu lokalnego skonfigurowanego dla aplikacji ASP.NET (w tym przykładzie **C:\Publish**) na komputerze z systemem Windows Server. W tym samouczku przyjęto założenie, że kopiowanie odbywa się ręcznie, ale można użyć innych narzędzi, takich jak PowerShell, XCOPY lub Robocopy.

    > [!CAUTION]
    > Jeśli trzeba wprowadzić zmiany w kodzie lub skompilować ponownie, należy ponownie opublikować i powtórzyć ten krok. Plik wykonywalny skopiowany na komputer zdalny musi dokładnie pasować do lokalnego źródła i symboli. Jeśli tego nie zrobisz, `cannot find or open the PDB file` w programie Visual Studio pojawi się ostrzeżenie podczas próby debugowania tego procesu.

1. Na serwerze z systemem Windows sprawdź, czy można prawidłowo uruchomić aplikację, otwierając aplikację w przeglądarce.

    Jeśli aplikacja nie działa prawidłowo, może wystąpić niezgodność między wersją programu ASP.NET zainstalowaną na serwerze a maszyną programu Visual Studio lub może wystąpić problem z konfiguracją usług IIS lub witryny sieci Web. Ponownie Sprawdź wcześniejsze kroki.
