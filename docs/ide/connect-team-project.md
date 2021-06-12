---
title: Nawiązywanie połączenia z projektami w programie Team Explorer
description: Dowiedz się, jak używać Team Explorer w Visual Studio do pracy z członkami zespołu w celu opracowywania projektów i zarządzania nimi.
ms.custom: SEO-VS-2020
ms.date: 06/11/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 4d3d2c005f32aaebacc251414218f5ae03edf546
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043019"
---
# <a name="connect-to-projects-in-team-explorer"></a>Nawiązywanie połączenia z projektami w programie Team Explorer

::: moniker range="vs-2017"

Okno **narzędzi Team Explorer** umożliwia koordynowanie pracy nad kodem z innymi członkami zespołu w celu opracowania projektu oraz zarządzanie pracą przypisaną do Ciebie, Twojego zespołu lub Twoich projektów. **Team Explorer** łączy Visual Studio z repozytoriami Git i GitHub, repozytoriami kontroli wersji serwera Team Foundation (TFVC) i projektami hostowanych w usłudze [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) lub lokalnym środowisku [Azure DevOps Server](/azure/devops/index-all) (wcześniej znanym jako TFS). Możesz zarządzać kodem źródłowym, elementami pracy i kompilacjami.

::: moniker-end

::: moniker range="vs-2019"

Team Explorer łączy Visual Studio z repozytoriami kontroli wersji serwera Team Foundation (TFVC) oraz z projektami hostowanych w umacie [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) lub lokalnym programem [Azure DevOps Server](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true) (wcześniej znanym jako TFS). Możesz zarządzać kodem źródłowym, elementami pracy i kompilacjami.

> [!IMPORTANT]
> W wersji [**16.8**](/visualstudio/releases/2019/release-notes-history)programu Visual Studio 2019 środowisko kontroli wersji usługi Git jest domyślnie włączone. Jeśli chcesz dowiedzieć się więcej o tym, jak wypada ona w porównaniu z Team Explorer, zobacz porównanie obok siebie usługi Git i [**Team Explorer**](../version-control/git-team-explorer-feature-comparison.md) usługi.
>
> Jeśli jednak wolisz nadal korzystać z usługi Team Explorer, przejdź do opcji narzędzia Funkcje środowiska w wersji zapoznawczej, a następnie przełącz pole wyboru Nowe środowisko użytkownika usługi  >  >  >  **Git.**

Sposób używania Team Explorer do nawiązywania połączenia z projektem zależy od wersji programu Visual Studio 2019, z których korzystasz.

## <a name="in-version-168-and-later"></a>W wersji 16.8 lub nowszej

1. Otwórz Visual Studio 2019 r.

1. W oknie uruchamiania wybierz pozycję **Clone a repository (Sklonuj repozytorium).**

   ![Zrzut ekranu przedstawiający okno dialogowe Klonowanie repozytorium Visual Studio 2019 w wersji 16.8 lub nowszej dla Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. W **sekcji Przeglądanie repozytorium** wybierz pozycję **Azure DevOps**.

    ![Zrzut ekranu przedstawiający sekcję "Przeglądanie repozytorium" okna dialogowego "Łączenie z projektem" w programie Visual Studio 2019 w wersji 16.8 lub nowszej](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Jeśli zostanie otwarte okno logowania, zaloguj się do swojego konta.

1. W **oknie dialogowym Łączenie** z projektem wybierz repopo, z którym chcesz nawiązać połączenie, a następnie wybierz pozycję **Klonuj**.

      ![Zrzut ekranu przedstawiający okno dialogowe "Łączenie z projektem" wygenerowane na podstawie Visual Studio 2019 w wersji 16.8 lub nowszej](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Jeśli nie widzisz wstępnie wypełnionej listy repos, z którym chcesz nawiązać połączenie, wybierz pozycję **Dodaj** Azure DevOps Server, aby wprowadzić adres URL serwera. (Alternatywnie może zostać wyświetlony monit "Nie znaleziono serwerów" z linkami do dodawania istniejącego Azure DevOps Server lub tworzenia Azure DevOps konta).

   Następnie Visual Studio plik **Eksplorator rozwiązań** foldery i pliki.

1. Wybierz **kartę Team Explorer,** aby wyświetlić Azure DevOps akcje.

      ![Zrzut ekranu przedstawiający okno dialogowe Team Explorer "Visual Studio 2019 w wersji 16.8 lub nowszej"](../ide/media/vs-2019/team-explorer-azure-devops.png)

## <a name="in-version-167-and-earlier"></a>W wersji 16.7 i starszych

1. Otwórz Visual Studio 2019 r.

1. W oknie uruchamiania wybierz pozycję **Klonuj lub wyewidencj go.**

   ![Zrzut ekranu przedstawiający okno "Tworzenie nowego projektu" w programie Visual Studio 2019 w wersji 16.7 lub starszej](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. W **sekcji Przeglądanie repozytorium** wybierz pozycję **Azure DevOps**.

   ![Zrzut ekranu przedstawiający okno "Klonowanie lub wyewidencjonaj kod" z sekcją "Przeglądanie repozytorium", która zawiera listę Azure DevOps w wersji 16.7 i starszej w programie Visual Studio 2019](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Jeśli zostanie otwarte okno logowania, zaloguj się do swojego konta.

1. W **oknie dialogowym Łączenie** z projektem wybierz repopo, z którym chcesz nawiązać połączenie, a następnie wybierz pozycję **Klonuj**.

      ![Zrzut ekranu przedstawiający okno dialogowe "Łączenie z projektem" wygenerowane na podstawie Visual Studio 2019 w wersji 16.7 lub starszej](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > To, co widzisz w polu listy, zależy od Azure DevOps repozytoriów, do których masz dostęp.

   Visual Studio zostanie **Team Explorer,** a po zakończeniu klonowania zostanie wyświetlone powiadomienie.

     ![Zrzut ekranu przedstawiający okno Team Explorer w programie Visual Studio 2019 w wersji 16.7 i starszych po zakończeniu klonowania](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. Aby wyświetlić foldery i pliki, wybierz **link Pokaż widok** folderu.

     ![Zrzut ekranu przedstawiający sekcję Rozwiązania okna Team Explorer w programie Visual Studio 2019 w wersji 16.7 lub starszej, po zakończeniu klonowania](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio zostanie otwarty **Eksplorator rozwiązań**.

1. Wybierz link **Rozwiązania i foldery,** aby wyszukać plik rozwiązania (w szczególności plik sln), który ma być otwarty.

      ![Zrzut ekranu przedstawiający powiadomienie "Rozwiązania i foldery" z Team Explorer wersji 2019 16.7 lub starszej Visual Studio 2019](../get-started/media/open-proj-repo-solutions-folders.png)

   Jeśli w swoim repocie nie masz pliku rozwiązania, zostanie wyświetlony komunikat "Nie znaleziono rozwiązań&quot;. Można jednak kliknąć dwukrotnie dowolny plik z menu folderu, aby otworzyć go w Visual Studio kodu.

::: moniker-end

::: moniker range=&quot;vs-2017&quot;

![Team Explorer strona główna w Visual Studio](media/team-explorer/team-explorer.png &quot;Strona Team Explorer — strona główna w Visual Studio.")

> [!TIP]
> Jeśli otworzysz okno Visual Studio, **Team Explorer** nie zostanie wyświetlony, otwórz go, wybierając pozycję **View** Team Explorer (Widok Team Explorer) na pasku menu lub naciskając  >   klawisze **Ctrl** + **&#92;**, **Ctrl** + **M**.

## <a name="connect-to-a-project-or-repository"></a>Nawiązywanie połączenia z projektem lub repozytorium

Połącz się z projektem lub repozytorium na **stronie** Połącz.

![Strona Łączenie w Team Explorer](media/team-explorer/connect.png "Strona Team Explorer — Łączenie w Visual Studio")

Aby nawiązać połączenie z projektem:

1. Otwórz stronę **Połącz,** wybierając **ikonę Zarządzaj połączeniami.**

   ![Przycisk Zarządzaj połączeniami w Team Explorer](media/team-explorer/manage-connections.png "Przycisk Team Explorer — Zarządzanie połączeniami w Visual Studio.")

1. Na stronie **Łączenie** wybierz pozycję Zarządzaj **połączeniami** > **Połącz z projektem.**

   ![Nawiązywanie połączenia z projektem w Team Explorer](media/team-explorer/connect-project.png "Opcja Team Explorer — Połącz z projektem w Visual Studio.")

> [!TIP]
> Jeśli chcesz otworzyć projekt z repo, zobacz Open a project from a repo (Otwieranie [projektu z repo).](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md) Jeśli chcesz utworzyć nowy projekt lub dodać użytkowników do projektu, zobacz Tworzenie projektu [(Azure DevOps)](/azure/devops/organizations/projects/create-project) i Dodawanie użytkowników do projektu lub zespołu [(Azure DevOps).](/azure/devops/organizations/security/add-users-team-project)

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Porównanie usługi Git i Team Explorer obok siebie](git-team-explorer-feature-comparison.md)
- [Nowe środowisko git w usłudze Visual Studio](git-with-visual-studio.md)
- [Dokumentacja wtyczki Team Explorer](reference/team-explorer-reference.md)
- [Łączenie z projektem (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Rozwiązywanie problemów z nawiązywanie połączenia z projektem](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
