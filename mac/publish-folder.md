---
title: Publikowanie w folderze
description: Jak opublikować aplikację sieci Web w folderze przy użyciu Visual Studio dla komputerów Mac.
ms.date: 11/09/2020
helpviewer_keywords:
- deployment, website, console, publish
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: 99127416b6a488cd7e795b3c4a1888ff103c8029
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607395"
---
# <a name="publish-to-a-folder-using-visual-studio-for-mac"></a>Publikowanie w folderze przy użyciu Visual Studio dla komputerów Mac

Za pomocą narzędzia do publikowania można opublikować konsolę .NET Core lub ASP.NET Core aplikacje w folderze.

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual Studio 2019 for Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019) został zainstalowany z włączonym platformą .NET Core.
- Konsola .NET Core lub projekt ASP.NET Core. Jeśli nie masz jeszcze projektu, możesz [utworzyć nowy](./create-new-projects.md).

## <a name="publish-to-folder"></a>Publikowanie w folderze

Za pomocą Visual Studio dla komputerów Mac można opublikować projekty platformy .NET Core w folderze za pomocą narzędzia do publikowania. Po opublikowaniu w folderze można przenieść pliki do innego środowiska. Aby opublikować w folderze, wykonaj następujące kroki.

 1. W oknie rozwiązanie kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

    ![Menu kontekstowe publikowania](media/publish-context-menu.png)

 2. Jeśli projekt został wcześniej opublikowany, w menu zostanie wyświetlony profil publikowania. Wybierz ten profil publikowania, aby rozpocząć proces publikowania.

 3. Aby opublikować ten projekt do folderu po raz pierwszy, wybierz pozycję **Opublikuj do folderu**

    ![Menu kontekstowe publikowania w folderze](media/publish-to-folder-context-menu.png)

 4. Zostanie wyświetlone okno dialogowe **Publikowanie do folderu** . W tym oknie dialogowym można dostosować folder, w którym projekt zostanie opublikowany. Możesz użyć przycisku **Przeglądaj** , aby to zrobić, lub wkleić ścieżkę.

 5. Po kliknięciu przycisku **Publikuj** kilka rzeczy. Pierwszy tworzony jest profil publikowania. Profil publikowania to plik programu MSBuild, który jest importowany do projektu podczas procesu publikowania. Zawiera właściwości, które są używane podczas procesu publikowania. Te pliki są przechowywane w `Properties/PublishProfiles` i mają rozszerzenie `.pubxml` . Następnie proces publikowania zostanie uruchomiony. Postęp można monitorować, obserwując pasek stanu w Visual Studio dla komputerów Mac.

    ![Pasek stanu IDE ze stanem publikowania](media/publish-to-folder-status-bar.png)

 6. Po pomyślnym opublikowaniu zostanie otwarte okno wyszukiwania do folderu publikowanie. Teraz, gdy profil publikacji został utworzony, będzie wyświetlany w menu kontekstowym publikowania.

    ![Opublikuj menu kontekstowe z profilem folderu](media/publish-context-menu-with-folder-profile.png)

 7. Aby ponownie opublikować projekt przy użyciu tych samych ustawień, możesz kliknąć profil w menu kontekstowym publikowania.

## <a name="customize-publish-options"></a>Dostosuj opcje publikowania

Aby zmienić nazwę profilu publikacji (która jest wyświetlana w menu kontekstowym publikowania), Zmień nazwę pliku profilu publikacji. Upewnij się, że nie zmieniono rozszerzenia pliku ( `.pubxml` ).

Aby zmienić ścieżkę folderu publikowania, Otwórz profil publikowania i edytuj `publishUrl` wartość.

Aby zmienić konfigurację kompilacji, która jest używana, Zmień `LastUsedBuildConfiguration` Właściwość w profilu publikowania.

## <a name="see-also"></a>Zobacz też
 - [dotnet publish](https://docs.microsoft.com/dotnet/core/tools/dotnet-publish)
 - [Publikowanie aplikacji sieci Web w witrynie sieci Web przy użyciu programu Visual Studio ](https://docs.microsoft.com/visualstudio/deployment/quickstart-deploy-to-a-web-site?view=vs-2019)