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
ms.openlocfilehash: 1d049bc8b74b83028e04fe92e7ce96f45907d042
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/24/2020
ms.locfileid: "97762618"
---
1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Publikuj** (dla formularzy sieci Web, **Opublikuj aplikację sieci Web**).

    Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, zostanie wyświetlone okienko **Publikowanie** . Kliknij pozycję **Nowy profil**.

1. W oknie dialogowym **Publikowanie** wybierz pozycję **folder**, kliknij pozycję **Przeglądaj**, a następnie utwórz nowy folder **C:\Publish**.

    ![Zrzut ekranu przedstawiający okno dialogowe Wybieranie elementu docelowego publikowania w programie Visual Studio z folderem "bin\Release\Publish" wybranym jako element docelowy publikowania.](../media/remotedbg_publish_local.png)

    W przypadku aplikacji formularzy sieci Web wybierz pozycję **niestandardowe** w oknie dialogowym Publikowanie, wprowadź nazwę profilu, a następnie wybierz **przycisk OK**.

1. Na liście rozwijanej kliknij pozycję **Utwórz profil** (wartość domyślna to **Opublikuj** ).

1. W oknie dialogowym **Publikowanie** kliknij link **Ustawienia** , a następnie wybierz kartę **Ustawienia** .

1. Ustaw konfigurację na **Debuguj**, wybierz opcję **Usuń wszystkie istniejące pliki przed opublikowaniem**, a następnie kliknij przycisk **Zapisz**.

    > [!NOTE]
    > Jeśli używasz kompilacji wydania, po opublikowaniu należy wyłączyć debugowanie w pliku web.config.

1. Kliknij przycisk **Opublikuj**.

    ![Zrzut ekranu przedstawiający kartę Ustawienia w oknie dialogowym Publikowanie. Konfiguracja jest ustawiona na Debuguj i wybrano przycisk Publikuj.](../media/remotedbg_publish_debug_config.png)

    Aplikacja publikuje konfigurację **debugowania** projektu w folderze lokalnym. Postęp jest wyświetlany w oknie danych wyjściowych.

1. Skopiuj katalog projektu ASP.NET z komputera programu Visual Studio do katalogu lokalnego skonfigurowanego dla aplikacji ASP.NET (w tym przykładzie **C:\Publish**) na komputerze z systemem Windows Server. W tym samouczku przyjęto założenie, że kopiowanie odbywa się ręcznie, ale można użyć innych narzędzi, takich jak PowerShell, XCOPY lub Robocopy.

    > [!CAUTION]
    > Jeśli trzeba wprowadzić zmiany w kodzie lub skompilować ponownie, należy ponownie opublikować i powtórzyć ten krok. Plik wykonywalny skopiowany na komputer zdalny musi dokładnie pasować do lokalnego źródła i symboli.    Jeśli tego nie zrobisz, `cannot find or open the PDB file` w programie Visual Studio pojawi się ostrzeżenie podczas próby debugowania tego procesu.

1. Na serwerze z systemem Windows sprawdź, czy można prawidłowo uruchomić aplikację, otwierając aplikację w przeglądarce.

    Jeśli aplikacja nie działa prawidłowo, może wystąpić niezgodność między wersją programu ASP.NET zainstalowaną na serwerze a maszyną programu Visual Studio lub może wystąpić problem z konfiguracją usług IIS lub witryny sieci Web. Ponownie Sprawdź wcześniejsze kroki.
