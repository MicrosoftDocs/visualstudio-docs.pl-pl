---
title: Publikowanie w folderze
ms.date: 01/22/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.openlocfilehash: 9fbcdb0bd9b9bab2afc69a8896cc00bedb98998b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065938"
---
# <a name="publish-a-web-app-to-a-folder-using-visual-studio-for-mac"></a>Publikowanie aplikacji sieci Web w folderze przy użyciu programu Visual Studio dla komputerów Mac

Narzędzie publikowania do publikowania aplikacji platformy ASP.NET Core w folderze.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 for Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) zainstalowane za pomocą programu ASP.NET Core włączone.
- Projekt platformy ASP.NET Core. Jeśli nie masz jeszcze projektu, możesz to zrobić [Utwórz nową](https://docs.microsoft.com/visualstudio/mac/create-new-projects?view=vsmac-2017).

## <a name="publish-to-folder"></a>Publikowanie w folderze

Przy użyciu programu Visual Studio dla komputerów Mac możesz opublikować w folderze za pomocą narzędzia publikowania projektów ASP.NET Core. Po opublikowaniu w folderze można przesyłać pliki do serwera sieci web można pobrać go do innego środowiska. Aby opublikować do folderu wykonaj następujące kroki.

 1. W konsoli rozwiązania, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

    ![Menu kontekstowe Opublikuj](media/publish-context-menu.png)

 2. Jeśli wcześniej zostały opublikowane tego projektu, zobaczysz profil publikowania, w menu. Wybierz ten profil publikowania, aby rozpocząć proces publikowania.

 3. Aby opublikować ten projekt do folderu po raz pierwszy, zaznacz **publikowania do folderu**

    ![Publikowanie w menu kontekstowym folderu](media/publish-to-folder-context-menu.png)

 4. **Publikowania do folderu** zostanie wyświetlone okno dialogowe. W tym oknie dialogowym możesz dostosować folder, w którym projekt zostanie opublikowany. Możesz użyć **Przeglądaj** przycisk, aby to zrobić, lub Wklej w ścieżce.

 5. Po kliknięciu przycisku **Publikuj** dziać kilka rzeczy. Najpierw tworzony jest profil publikowania. Profil publikowania jest plikiem programu MSBuild, który jest importowany do projektu w procesie publikowania. Zawiera właściwości, które są używane w procesie publikowania. Te pliki są przechowywane w `Properties/PublishProfiles` i mają rozszerzenie `.pubxml`. Następnie proces publikowania jest uruchomiona. Postęp można monitorować, obserwując na pasku stanu w programie Visual Studio dla komputerów Mac.

    ![Pasek stanu IDE ze stanu publikowania](media/publish-to-folder-status-bar.png)

 6. Po pomyślnym zakończeniu publikowania do folderu publikowania zostanie otwarte okno wyszukiwania. Teraz, gdy został utworzony profil publikowania, pojawi się w menu kontekstowym publikowania.

    ![Menu kontekstowe folderu profilu publikowania](media/publish-context-menu-with-folder-profile.png)

 7. Aby opublikować projekt ponownie, używając tych samych ustawień możesz kliknąć profil publikowania menu kontekstowego.

## <a name="customize-publish-options"></a>Dostosuj opcje publikowania

Aby zmienić nazwę profilu publikowania (który jest wyświetlany w menu kontekstowym publikowania), Zmień nazwę pliku profilu publikowania. Upewnij się, że nie Zmień rozszerzenie nazwy pliku (`.puxbml`).

Aby zmienić ścieżkę folderu publikowania, Otwórz profil publikowania, a następnie Edytuj `publishUrl` wartość.

Aby zmienić konfigurację kompilacji, który jest używany, należy zmienić `LastUsedBuildConfiguration` właściwości w profilu publikowania.