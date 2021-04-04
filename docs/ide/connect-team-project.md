---
title: Nawiązywanie połączenia z projektami w programie Team Explorer
description: Dowiedz się, jak używać Team Explorer w programie Visual Studio do pracy z członkami zespołu w celu opracowywania projektów i zarządzania nimi.
ms.custom: SEO-VS-2020
ms.date: 03/31/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 78a71911bb4334e04a085d91ff51238d34981beb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216608"
---
# <a name="connect-to-projects-in-team-explorer"></a>Nawiązywanie połączenia z projektami w programie Team Explorer

::: moniker range="vs-2017"

Użyj okna narzędzia **Team Explorer** , aby koordynować wysiłki kodu z innymi członkami zespołu, aby opracować projekt i zarządzać pracą przypisaną do Ciebie, Twojego zespołu lub Twoich projektów. **Team Explorer** łączy program Visual Studio z repozytoriami git i GitHub, repozytoriami wersji Team Foundation Version Control (TFVC) i projektami obsługiwanymi w [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) lub [Azure DevOps Server](/azure/devops/index-all) lokalnymi (wcześniej znanym jako TFS). Możesz zarządzać kodem źródłowym, elementami roboczymi i kompilacjami.

::: moniker-end

::: moniker range="vs-2019"

Team Explorer łączy program Visual Studio z repozytoriami kontroli wersji programu Team Foundation (TFVC) oraz z projektami hostowanymi na [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) lub [Azure DevOps Server](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true) lokalnymi (wcześniej znanym jako TFS). Możesz zarządzać kodem źródłowym, elementami roboczymi i kompilacjami.

> [!IMPORTANT]
> W przypadku najnowszej wersji programu Visual Studio 2019 w [**wersji 16,8**](/visualstudio/releases/2019/release-notes/)nowe środowisko kontroli wersji Git jest teraz domyślnie włączone. Jeśli chcesz dowiedzieć się więcej na temat porównywania z Team Explorer, zobacz [**porównanie Side-by-Side na stronie git i Team Explorer**](git-team-explorer-feature-comparison.md) .
>
> Jeśli jednak wolisz nadal używać Team Explorer, przejdź do pozycji **Narzędzia** > **Opcje** > **środowiska** > **Podgląd funkcji** , a następnie Przełącz nowe pole wyboru **środowisko użytkownika systemu Git** .

Sposób używania Team Explorer do nawiązywania połączenia z projektem zależy od używanej wersji programu Visual Studio 2019.

## <a name="in-version-168-and-later"></a>W wersji 16,8 i nowszych

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz pozycję **Klonuj repozytorium**.

   ![Zrzut ekranu okna dialogowego klonowanie repozytorium w programie Visual Studio 2019 w wersji 16,8 i nowszej dla usługi Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. W sekcji **Przeglądaj repozytorium** wybierz pozycję **Azure DevOps**.

    ![Zrzut ekranu przedstawiający sekcję "przeglądanie repozytorium" okna dialogowego "łączenie z projektem" w programie Visual Studio 2019 w wersji 16,8 i nowszej](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Jeśli zobaczysz okno logowania, zaloguj się do swojego konta.

1. W oknie dialogowym **Połącz z projektem** wybierz repozytorium, z którym chcesz się połączyć, a następnie wybierz pozycję **Klonuj**.

      ![Zrzut ekranu przedstawiający okno dialogowe "łączenie z projektem", które zostało wygenerowane z programu Visual Studio 2019 w wersji 16,8 lub nowszej](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Jeśli nie widzisz wstępnie wypełnionej listy repozytoriów, z którymi chcesz nawiązać połączenie, wybierz pozycję **dodaj Azure DevOps Server** , aby wprowadzić adres URL serwera. (W przeciwnym razie może zostać wyświetlony monit "nie znaleziono serwerów", który zawiera linki do dodania istniejącego Azure DevOps Server lub utworzenia konta usługi Azure DevOps).

   Następnie program Visual Studio otwiera **Eksplorator rozwiązań** , w którym są wyświetlane foldery i pliki.

1. Wybierz kartę **Team Explorer** , aby wyświetlić akcje usługi Azure DevOps.

      ![Zrzut ekranu przedstawiający okno dialogowe "Team Explorer", które zostało wygenerowane z programu Visual Studio 2019 w wersji 16,8 lub nowszej](../ide/media/vs-2019/team-explorer-azure-devops.png)

## <a name="in-version-167-and-earlier"></a>W wersji 16,7 i starszej

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz opcję **klonowanie lub wyewidencjonowywanie kodu**.

   ![Zrzut ekranu przedstawiający okno "Tworzenie nowego projektu" w programie Visual Studio 2019 w wersji 16,7 i starszej](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. W sekcji **Przeglądaj repozytorium** wybierz pozycję **Azure DevOps**.

   ![Zrzut ekranu przedstawiający okno "klonowanie lub wyewidencjonowywanie kodu" z sekcją "przeglądanie repozytorium" przedstawiającą usługę Azure DevOps w programie Visual Studio 2019 w wersji 16,7 i starszej](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Jeśli zobaczysz okno logowania, zaloguj się do swojego konta.

1. W oknie dialogowym **Połącz z projektem** wybierz repozytorium, z którym chcesz się połączyć, a następnie wybierz pozycję **Klonuj**.

      ![Zrzut ekranu przedstawiający okno dialogowe "łączenie z projektem", które zostało wygenerowane z programu Visual Studio 2019 w wersji 16,7 i starszej](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Elementy wyświetlane w polu listy zależą od repozytoriów usługi Azure DevOps, do których masz dostęp.

   Program Visual Studio otwiera **Team Explorer** i zostanie wyświetlone powiadomienie po zakończeniu klonowania.

     ![Zrzut ekranu okna Team Explorer w programie Visual Studio 2019 w wersji 16,7 i starszej po ukończeniu klonowania](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. Aby wyświetlić foldery i pliki, wybierz łącze **Pokaż widok folderu** .

     ![Zrzut ekranu przedstawiający sekcję Solutions okna Team Explorer w programie Visual Studio 2019 w wersji 16,7 i starszej po ukończeniu klonowania](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Program Visual Studio otwiera **Eksplorator rozwiązań**.

1. Wybierz łącze **rozwiązania i foldery** , aby wyszukać plik rozwiązania (w odniesieniu do pliku. sln), aby go otworzyć.

      ![Zrzut ekranu przedstawiający powiadomienie "rozwiązania i foldery" z Team Explorer w programie Visual Studio 2019 w wersji 16,7 i starszej](../get-started/media/open-proj-repo-solutions-folders.png)

   Jeśli nie masz pliku rozwiązania w repozytorium, zostanie wyświetlony komunikat "nie znaleziono rozwiązań". Można jednak kliknąć dwukrotnie dowolny plik z menu folder, aby otworzyć go w edytorze kodu programu Visual Studio.

::: moniker-end

::: moniker range="vs-2017"

![Strona główna Team Explorer w programie Visual Studio](media/team-explorer/team-explorer.png "Strona główna Team Explorer w programie Visual Studio.")

> [!TIP]
> Jeśli otworzysz program Visual Studio i **Team Explorer** nie jest wyświetlany, otwórz go, wybierając pozycję **Wyświetl**  >  **Team Explorer** z paska menu lub naciskając **klawisze CTRL** + **&#92;**, **Ctrl** + **M**.

## <a name="connect-to-a-project-or-repository"></a>Nawiązywanie połączenia z projektem lub repozytorium

Połącz się z projektem lub repozytorium na stronie **Połącz** .

![Połącz stronę w Team Explorer](media/team-explorer/connect.png "Strona Team Explorer-Connect w programie Visual Studio")

Aby nawiązać połączenie z projektem:

1. Otwórz stronę **Połącz** , wybierając ikonę **Zarządzaj połączeniami** .

   ![Przycisk Zarządzaj połączeniami w Team Explorer](media/team-explorer/manage-connections.png "Przycisk Team Explorer-Manage Connections w programie Visual Studio.")

1. Na stronie **Połącz** wybierz pozycję **Zarządzaj połączeniami** > **Połącz** się z projektem.

   ![Nawiązywanie połączenia z projektem w Team Explorer](media/team-explorer/connect-project.png "Opcja Team Explorer — Połącz z projektem w programie Visual Studio.")

> [!TIP]
> Jeśli chcesz otworzyć projekt z repozytorium, zobacz [Otwieranie projektu z repozytorium](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md). Jeśli chcesz utworzyć nowy projekt lub dodać użytkowników do projektu, zobacz [Tworzenie projektu (Azure DevOps)](/azure/devops/organizations/projects/create-project) i [Dodawanie użytkowników do projektu lub zespołu (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Porównaj narzędzia Git i Team Explorer obok siebie](git-team-explorer-feature-comparison.md)
- [Nowe środowisko Git w programie Visual Studio](git-with-visual-studio.md)
- [Dokumentacja wtyczki Team Explorer](reference/team-explorer-reference.md)
- [Nawiązywanie połączenia z projektem (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Rozwiązywanie problemów z nawiązywaniem połączenia z projektem](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
