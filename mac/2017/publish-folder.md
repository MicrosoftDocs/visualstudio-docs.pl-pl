---
title: Publikowanie w folderze
ms.date: 01/22/2019
helpviewer_keywords:
- deployment, website
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.openlocfilehash: ff8635db2b472ee3dd79e9082de9d9cc6bd555cb
ms.sourcegitcommit: fe212f8960d7882a1b0fdae9e22f008996aacf3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222676"
---
# <a name="publish-a-web-app-to-a-folder-using-visual-studio-for-mac"></a>Publikowanie aplikacji sieci Web w folderze przy użyciu Visual Studio dla komputerów Mac

Za pomocą narzędzia do publikowania można publikować aplikacje ASP.NET Core w folderze.

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual Studio 2017 dla komputerów Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) został zainstalowany z włączonym ASP.NET Core.
- Projekt ASP.NET Core. Jeśli nie masz jeszcze projektu, możesz [utworzyć nowy](https://docs.microsoft.com/visualstudio/mac/create-new-projects?view=vsmac-2017).

## <a name="publish-to-folder"></a>Publikowanie w folderze

Za pomocą Visual Studio dla komputerów Mac można opublikować projekty ASP.NET Core w folderze za pomocą narzędzia do publikowania. Po opublikowaniu w folderze można przenieść pliki na serwer sieci Web w celu uzyskania ich w innym środowisku. Aby opublikować w folderze, wykonaj następujące kroki.

 1. W okienko rozwiązania kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

    ![Menu kontekstowe publikowania](media/publish-context-menu.png)

 2. Jeśli projekt został wcześniej opublikowany, w menu zostanie wyświetlony profil publikowania. Wybierz ten profil publikowania, aby rozpocząć proces publikowania.

 3. Aby opublikować ten projekt do folderu po raz pierwszy, wybierz pozycję **Opublikuj do folderu**

    ![Menu kontekstowe publikowania w folderze](media/publish-to-folder-context-menu.png)

 4. Zostanie wyświetlone okno dialogowe **Publikowanie do folderu** . W tym oknie dialogowym można dostosować folder, w którym projekt zostanie opublikowany. Możesz użyć przycisku **Przeglądaj** , aby to zrobić, lub wkleić ścieżkę.

 5. Po kliknięciu przycisku **Publikuj** kilka rzeczy. Pierwszy tworzony jest profil publikowania. Profil publikowania to plik programu MSBuild, który jest importowany do projektu podczas procesu publikowania. Zawiera właściwości, które są używane podczas procesu publikowania. Te pliki są przechowywane w `Properties/PublishProfiles` i mają rozszerzenie. `.pubxml` Następnie proces publikowania zostanie uruchomiony. Postęp można monitorować, obserwując pasek stanu w Visual Studio dla komputerów Mac.

    ![Pasek stanu IDE ze stanem publikowania](media/publish-to-folder-status-bar.png)

 6. Po pomyślnym opublikowaniu zostanie otwarte okno wyszukiwania do folderu publikowanie. Teraz, gdy profil publikacji został utworzony, będzie wyświetlany w menu kontekstowym publikowania.

    ![Opublikuj menu kontekstowe z profilem folderu](media/publish-context-menu-with-folder-profile.png)

 7. Aby ponownie opublikować projekt przy użyciu tych samych ustawień, możesz kliknąć profil w menu kontekstowym publikowania.

## <a name="customize-publish-options"></a>Dostosuj opcje publikowania

Aby zmienić nazwę profilu publikacji (która jest wyświetlana w menu kontekstowym publikowania), Zmień nazwę pliku profilu publikacji. Upewnij się, że nie zmieniono rozszerzenia pliku (`.puxbml`).

Aby zmienić ścieżkę folderu publikowania, Otwórz profil publikowania i edytuj `publishUrl` wartość.

Aby zmienić konfigurację kompilacji, która jest używana, Zmień `LastUsedBuildConfiguration` właściwość w profilu publikowania.