---
title: Nawiązywanie połączenia z projektami w Team Explorer
description: Dowiedz się, jak używać Team Explorer w programie Visual Studio do pracy z członkami zespołu w celu opracowywania projektów i zarządzania nimi.
ms.date: 11/17/2020
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 4e4fdfb26c601ce6b706c1c946ea9afe9b18ecb2
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850094"
---
# <a name="connect-to-projects-in-team-explorer"></a>Nawiązywanie połączenia z projektami w Team Explorer

::: moniker range="vs-2017"

Użyj okna narzędzia **Team Explorer** , aby koordynować wysiłki kodu z innymi członkami zespołu, aby opracować projekt i zarządzać pracą przypisaną do Ciebie, Twojego zespołu lub Twoich projektów. **Team Explorer** łączy program Visual Studio z repozytoriami git i GitHub, repozytoriami wersji Team Foundation Version Control (TFVC) i projektami obsługiwanymi w [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) lub [Azure DevOps Server](/azure/devops/index-all) lokalnymi (wcześniej znanym jako TFS). Możesz zarządzać kodem źródłowym, elementami roboczymi i kompilacjami.

::: moniker-end

::: moniker range="vs-2019"

Możesz użyć okna narzędzia **Team Explorer** , aby koordynować wysiłki kodu z innymi członkami zespołu, aby opracować projekt i zarządzać pracą, która jest przypisana do Ciebie, Twojego zespołu lub Twoich projektów.

> [!IMPORTANT]
> W przypadku najnowszej wersji programu Visual Studio 2019 w [wersji 16,8](/visualstudio/releases/2019/release-notes/)nowe środowisko kontroli wersji Git jest teraz domyślnie włączone. Jeśli jednak wolisz nadal używać Team Explorer, przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **środowiska**  >  **Podgląd funkcji** , a następnie Przełącz nowe pole wyboru **środowisko użytkownika systemu Git** . Aby uzyskać więcej informacji, zobacz [środowisko Git na stronie programu Visual Studio](git-with-visual-studio.md) .

**Team Explorer** łączy program Visual Studio z repozytoriami git i GitHub, repozytoriami wersji Team Foundation Version Control (TFVC) i projektami obsługiwanymi w [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) lub [Azure DevOps Server](/azure/devops/index-all) lokalnymi (wcześniej znanym jako TFS). Możesz zarządzać kodem źródłowym, elementami roboczymi i kompilacjami.

::: moniker-end

![Strona główna Team Explorer w programie Visual Studio](media/team-explorer/team-explorer.png)

::: moniker range="vs-2017"

> [!TIP]
> Jeśli otworzysz program Visual Studio i **Team Explorer** nie jest wyświetlany, otwórz go, wybierając pozycję **Wyświetl**  >  **Team Explorer** z paska menu lub naciskając **klawisze CTRL** + **&#92;**, **Ctrl** + **M**.

::: moniker-end

## <a name="connect-to-a-project-or-repository"></a>Nawiązywanie połączenia z projektem lub repozytorium

Połącz się z projektem lub repozytorium na stronie **Połącz** .

![Połącz stronę w Team Explorer](media/team-explorer/connect.png)

Aby nawiązać połączenie z projektem:

1. Otwórz stronę **Połącz** , wybierając ikonę **Zarządzaj połączeniami** .

   ![Przycisk Zarządzaj połączeniami w Team Explorer](media/team-explorer/manage-connections.png)

1. Na stronie **Połącz** wybierz pozycję **Zarządzaj połączeniami**  >  **Połącz** się z projektem.

   ![Nawiązywanie połączenia z projektem w Team Explorer](media/team-explorer/connect-project.png)

> [!TIP]
> Jeśli chcesz otworzyć projekt z repozytorium, zobacz [Otwieranie projektu z repozytorium](../get-started/tutorial-open-project-from-repo.md). Jeśli chcesz utworzyć nowy projekt lub dodać użytkowników do projektu, zobacz [Tworzenie projektu (Azure DevOps)](/azure/devops/organizations/projects/create-project) i [Dodawanie użytkowników do projektu lub zespołu (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

## <a name="see-also"></a>Zobacz także

- [Nowe środowisko Git w programie Visual Studio](git-with-visual-studio.md)
- [Samouczek: Otwieranie projektu z repozytorium](../get-started/tutorial-open-project-from-repo.md)
- [Dokumentacja wtyczki Team Explorer](reference/team-explorer-reference.md)
- [Nawiązywanie połączenia z projektem (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Rozwiązywanie problemów z nawiązywaniem połączenia z projektem](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
