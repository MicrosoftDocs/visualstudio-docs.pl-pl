---
title: 'Samouczek: Otwieranie projektu z repozytorium'
description: Dowiedz się, jak otworzyć projekt w repozytorium Git lub Azure DevOps za pomocą programu Visual Studio.
ms.custom: get-started
ms.date: 11/03/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 56005faa4475f040375108ca02abbca40cd2652d
ms.sourcegitcommit: e132a870ec198fdcec289227f1a0c1c48fef070c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344543"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Samouczek: Otwieranie projektu z repozytorium

W tym samouczku użyjesz programu Visual Studio, aby połączyć się z repozytorium po raz pierwszy, a następnie otworzyć projekt.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Otwieranie projektu z repozytorium GitHub

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **plik** > **Otwórz** > **Otwórz z kontroli źródła**.

   Zostanie otwarte okienko **Team Explorer-Connect** .

    ![Okno Team Explorer w środowisku IDE programu Visual Studio](./media/open-proj-repo-team-explorer.png)

1. W sekcji **lokalne repozytoria Git** wybierz **klon**.

    ![Wybierz klon z lokalnej sekcji repozytoria Git](./media/open-proj-repo-local-git-repo-clone.png)

1. W polu tekstowym **_wprowadź adres URL repozytorium git do klonowania_*_ wpisz lub wklej adres URL repozytorium, a następnie naciśnij klawisz _* Enter**. (Może pojawić się monit o zalogowanie się do usługi GitHub; Jeśli tak, zrób to).

   Po sklonowaniu repozytorium przez program Visual Studio Team Explorer zamyka się i Eksplorator rozwiązań otwiera. Zostanie wyświetlony komunikat z informacją, że *kliknij pozycję rozwiązania i foldery powyżej, aby wyświetlić listę rozwiązań*. Wybierz **rozwiązania i foldery**.

   ![Wybierz pozycję "rozwiązania i foldery" z Eksplorator rozwiązań](./media/open-proj-repo-github-solutions-folders.png)

1. Jeśli masz dostępny plik rozwiązania, zostanie on wyświetlony w menu "roztwory i foldery". Wybierz go, a program Visual Studio otwiera Twoje rozwiązanie.

   ![Wybierz, co chcesz otworzyć z listy rozwijanej Eksplorator rozwiązań](./media/open-proj-repo-github-solutions-folders-picker.png)

   Jeśli w repozytorium nie ma pliku rozwiązania (w odniesieniu do pliku. sln), w menu rozwijanym zostanie wyświetlona informacja "nie znaleziono rozwiązań". Można jednak kliknąć dwukrotnie dowolny plik z menu folder, aby otworzyć go w edytorze kodu programu Visual Studio.

### <a name="review-your-work"></a>Przejrzyj swoją służbę

Wyświetl poniższą animację, aby sprawdzić pracę zakończono w poprzedniej sekcji.

   ![Animacja otwierania projektu w repozytorium GitHub przy użyciu programu Visual Studio](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz **klonowanie lub wyewidencjonowywanie kodu**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Wprowadź lub wpisz lokalizację repozytorium, a następnie wybierz **klon**.

   ![Wyświetl okno "klonowanie lub Wyewidencjonuj kod"](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Program Visual Studio otwiera projekt z repozytorium.

1. Jeśli masz dostępny plik rozwiązania, zostanie on wyświetlony w menu "roztwory i foldery". Wybierz go, a program Visual Studio otwiera Twoje rozwiązanie.

   ![Wybierz, co chcesz otworzyć z listy rozwijanej Eksplorator rozwiązań](./media/open-proj-repo-github-solutions-folders-picker.png)

   Jeśli w repozytorium nie ma pliku rozwiązania (w odniesieniu do pliku. sln), w menu rozwijanym zostanie wyświetlona informacja "nie znaleziono rozwiązań". Można jednak kliknąć dwukrotnie dowolny plik z menu folder, aby otworzyć go w edytorze kodu programu Visual Studio.

> [!TIP]
> Jeśli chcesz wypróbować nowe środowisko usługi Git w programie Visual Studio i korzystać z [wersji 16,6](/visualstudio/releases/2019/release-notes-v16.6) lub nowszej, możesz ją przełączać, przechodząc do opcji **Narzędzia**  >  **Opcje**  >  **środowisko** w  >  **wersji zapoznawczej** , a następnie zaznaczając pole wyboru **nowe środowisko użytkownika systemu Git** . Aby uzyskać więcej informacji, zobacz [nowe środowisko Git na stronie programu Visual Studio](../ide/git-with-visual-studio.md) .

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Otwieranie projektu z repozytorium usługi Azure DevOps

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **plik** > **Otwórz** > **Otwórz z kontroli źródła**.

   Zostanie otwarte okienko **Team Explorer-Connect** .

    ![Okno Team Explorer w środowisku IDE programu Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Poniżej przedstawiono dwa sposoby nawiązywania połączenia z repozytorium usługi Azure DevOps:

      - W sekcji **dostawcy usług hostowanych** wybierz pozycję **Połącz...**.

        ![Sekcja dostawcy usług hostowanych okna Team Explorer w środowisku IDE programu Visual Studio](./media/open-proj-repo-azure-devops.png)

      - Z listy rozwijanej **Zarządzaj połączeniami** wybierz pozycję **Połącz z projektem...**.

        ![Sekcja zarządzanie połączeniami okna Team Explorer w środowisku IDE programu Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. W oknie dialogowym **Połącz z projektem** wybierz repozytorium, z którym chcesz nawiązać połączenie, a następnie wybierz **klon**.

      ![Okno dialogowe "łączenie z projektem", które zostało wygenerowane z programu Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Elementy wyświetlane w polu listy zależą od repozytoriów usługi Azure DevOps, do których masz dostęp.

1. Po sklonowaniu repozytorium przez program Visual Studio Team Explorer zamyka się i Eksplorator rozwiązań otwiera. Zostanie wyświetlony komunikat z informacją, że *kliknij pozycję rozwiązania i foldery powyżej, aby wyświetlić listę rozwiązań*. Wybierz **rozwiązania i foldery**.

      ![Powiadomienie "rozwiązania i foldery" z Team Explorer w programie Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Plik rozwiązania (w specjalnym pliku. sln) pojawi się w menu rozwijanym "rozwiązania i foldery". Wybierz go, a program Visual Studio otwiera Twoje rozwiązanie.

   Jeśli w repozytorium nie ma pliku rozwiązania, w menu rozwijanym zostanie wyświetlona informacja "nie znaleziono rozwiązań". Można jednak kliknąć dwukrotnie dowolny plik z menu folder, aby otworzyć go w edytorze kodu programu Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz **klonowanie lub wyewidencjonowywanie kodu**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. W sekcji **Przeglądaj repozytorium** wybierz pozycję **Azure DevOps**.

   ![Wyświetl okno "klonowanie lub wyewidencjonowywanie kodu"](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Jeśli zobaczysz okno logowania, zaloguj się do swojego konta.

1. W oknie dialogowym **Połącz z projektem** wybierz repozytorium, z którym chcesz nawiązać połączenie, a następnie wybierz **klon**.

      ![Okno dialogowe "łączenie z projektem", które zostało wygenerowane z programu Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Elementy wyświetlane w polu listy zależą od repozytoriów usługi Azure DevOps, do których masz dostęp.

   Program Visual Studio otwiera **Team Explorer** i zostanie wyświetlone powiadomienie po zakończeniu klonowania.

     ![Okno Team Explorer w programie Visual Studio po ukończeniu klonowania](./media/vs-2019/clone-complete-azure-devops.png)

1. Aby wyświetlić foldery i pliki, wybierz łącze **Pokaż widok folderu** .

     ![Sekcja Solutions okna Team Explorer w programie Visual Studio po ukończeniu klonowania](./media/vs-2019/show-folder-view-azure-devops.png)

     Program Visual Studio otwiera **Eksplorator rozwiązań**.

1. Wybierz łącze **rozwiązania i foldery** , aby wyszukać plik rozwiązania (w odniesieniu do pliku. sln), aby go otworzyć.

      ![Powiadomienie "rozwiązania i foldery" z Team Explorer w programie Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Jeśli w repozytorium nie ma pliku rozwiązania, zostanie wyświetlony komunikat "nie znaleziono rozwiązań". Można jednak kliknąć dwukrotnie dowolny plik z menu folder, aby otworzyć go w edytorze kodu programu Visual Studio.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Jeśli wszystko jest gotowe do kodu w programie Visual Studio, szczegółowe do dowolnego z następujących samouczków dotyczących języka:

- [Samouczki programu Visual Studio | Język **C#**](./csharp/index.yml)
- [Samouczki programu Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Samouczki programu Visual Studio | Język **C++**](/cpp/get-started/tutorial-console-cpp)
- [Samouczki programu Visual Studio | Język **Python**](../python/index.yml)
- [Samouczki programu Visual Studio | **JavaScript** , **TypeScript** i **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Zobacz też

::: moniker range="vs-2017"

- [Azure DevOps Services: wprowadzenie do Azure Repos i programu Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Rozpoczynanie pracy z usługą Azure DevOps](/learn/modules/get-started-with-devops/)
- [Nowe środowisko Git w programie Visual Studio 2019](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true)

::: moniker-end

::: moniker range="vs-2019"

- [Nowe środowisko Git w programie Visual Studio](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: wprowadzenie do Azure Repos i programu Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Rozpoczynanie pracy z usługą Azure DevOps](/learn/modules/get-started-with-devops/)

::: moniker-end
