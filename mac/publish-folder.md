---
title: Publikowanie w folderze
ms.date: 04/02/2019
helpviewer_keywords:
- deployment, website, console, publish
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.openlocfilehash: 0ea70fb1a5898e2415b7f74e93233ca03ea52c45
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224501"
---
# <a name="publish-to-a-folder-using-visual-studio-for-mac"></a>Publikowanie w folderze przy użyciu programu Visual Studio dla komputerów Mac

Za pomocą narzędzia Publikowanie można publikować w folderze .NET Core Console lub ASP.NET aplikacje Core.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019 dla komputerów Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019) zainstalowany z włączoną funkcją .NET Core.
- Konsola .NET Core lub projekt ASP.NET Core. Jeśli nie masz jeszcze projektu, możesz [utworzyć nowy](/visualstudio/mac/create-new-projects?view=vsmac-2019).

## <a name="publish-to-folder"></a>Publikowanie w folderze

Za pomocą programu Visual Studio dla komputerów Mac można publikować projekty .NET Core w folderze za pomocą narzędzia Publikowania. Po opublikowaniu w folderze można przenieść pliki do innego środowiska. Aby opublikować w folderze, wykonaj następujące kroki.

 1. W panelu rozwiązania kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

    ![Menu kontekstowe Publikowania](media/publish-context-menu.png)

 2. Jeśli ten projekt został wcześniej opublikowany, w menu zobaczysz profil publikowania. Wybierz profil publikowania, aby rozpocząć proces publikowania.

 3. Aby opublikować ten projekt w folderze po raz pierwszy, wybierz **pozycję Publikuj w folderze**

    ![Menu kontekstowe Publikowania w folderze](media/publish-to-folder-context-menu.png)

 4. Zostanie wyświetlone okno dialogowe **Publikuj w folderze.** W tym oknie dialogowym można dostosować folder, w którym zostanie opublikowany projekt. Możesz użyć przycisku **Przeglądaj,** aby to zrobić lub wkleić ścieżkę.

 5. Po kliknięciu **przycisku Opublikuj** kilka rzeczy się zdarzyć. Najpierw tworzony jest profil publikowania. Profil publikowania to plik MSBuild, który jest importowany do projektu podczas procesu publikowania. Zawiera właściwości, które są używane podczas procesu publikowania. Pliki te są `Properties/PublishProfiles` przechowywane w `.pubxml`i mają rozszerzenie . Następnie rozpoczyna się proces publikowania. Postęp można monitorować, obserwując pasek stanu w programie Visual Studio dla komputerów Mac.

    ![Pasek stanu IDE ze stanem Publikowania](media/publish-to-folder-status-bar.png)

 6. Po pomyślnym zakończeniu publikowania zostanie otwarte okno Findera do folderu publikowania. Teraz, gdy profil publikowania został utworzony, zostanie wyświetlony w menu kontekstowym Publikowania.

    ![Menu kontekstowe Publikowania z profilem folderu](media/publish-context-menu-with-folder-profile.png)

 7. Aby ponownie opublikować projekt z tymi samymi ustawieniami, możesz kliknąć na profil w menu kontekstowym publikowania.

## <a name="customize-publish-options"></a>Dostosowywanie opcji publikowania

Aby zmienić nazwę profilu publikowania (który jest wyświetlany w menu kontekstowym publikowania), zmień nazwę pliku profilu publikowania. Upewnij się, że nie należy`.pubxml`zmieniać rozszerzenia pliku ( ).

Aby zmienić ścieżkę publikowania folderu, `publishUrl` otwórz profil publikowania i edytuj wartość.

Aby zmienić konfigurację kompilacji, `LastUsedBuildConfiguration` która jest używana, zmień właściwość w profilu publikowania.
