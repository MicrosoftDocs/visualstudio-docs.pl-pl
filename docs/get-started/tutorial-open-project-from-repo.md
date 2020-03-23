---
title: 'Samouczek: Otwieranie projektu z repozytorium'
description: Dowiedz się, jak otworzyć projekt w repozytorium Git lub Azure DevOps przy użyciu programu Visual Studio.
ms.custom: get-started
ms.date: 03/30/2019
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
ms.openlocfilehash: 3af54d663cee1ad2b2dd4e8241678b88c635d376
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "70180437"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Samouczek: Otwieranie projektu z repozytorium

W tym samouczku użyjesz programu Visual Studio, aby połączyć się z repozytorium po raz pierwszy, a następnie otworzyć projekt z niego.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Otwieranie projektu z repozytorium GitHub

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **Otwórz plik** > **Open** > **z kontroli źródła**.

   Zostanie otwarte okienko **Eksplorator zespołu — połącz.**

    ![Okno Eksploratora zespołu w środowisku IDE programu Visual Studio](./media/open-proj-repo-team-explorer.png)

1. W sekcji **Lokalne repozytoria Git** wybierz pozycję **Klonuj**.

    ![Wybierz pozycję Klonuj z sekcji Lokalne repozytoria Git](./media/open-proj-repo-local-git-repo-clone.png)

1. W polu z ***podaniem Wprowadź adres URL repozytorium Git do klonowania***, wpisz lub wklej adres URL repozytorium, a następnie naciśnij **klawisz Enter**. (Może pojawić się monit o zalogowanie się do usługi GitHub; jeśli tak, zrób to).

   Po sklonowanie repozytorium w programie Visual Studio, Eksplorator zespołu zostanie zamknięty i zostanie otwarty Eksplorator rozwiązań. Pojawi się komunikat *Click on Solutions and Folders powyżej, aby wyświetlić listę rozwiązań*. Wybierz **rozwiązania i foldery**.

   ![Wybierz "Rozwiązania i foldery" w Eksploratorze rozwiązań](./media/open-proj-repo-github-solutions-folders.png)

1. Jeśli masz dostępny plik rozwiązania, pojawi się on w menu wysuwu "Rozwiązania i foldery". Wybierz go, a program Visual Studio otworzy rozwiązanie.

   ![Wybierz, co chcesz otworzyć z listy rozwijanej Eksploratora rozwiązań](./media/open-proj-repo-github-solutions-folders-picker.png)

   Jeśli nie masz pliku rozwiązania (w szczególności pliku .sln) w repozytorium, menu wysuń powie "Nie znaleziono rozwiązań". Można jednak dwukrotnie kliknąć dowolny plik z menu folderów, aby otworzyć go w edytorze kodu programu Visual Studio.

### <a name="review-your-work"></a>Przejrzyj swoją pracę

Wyświetl następującą animację, aby sprawdzić pracę wykonany w poprzedniej sekcji.

   ![Animacja otwierania projektu w repozytorium Usługi GitHub przy użyciu programu Visual Studio](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

1. W oknie startowym wybierz pozycję **Klonuj lub wyewidencjonuj kod**.

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Wprowadź lub wpisz lokalizację repozytorium, a następnie wybierz pozycję **Klonuj**.

   ![Wyświetlanie okna "Klonuj lub kod realizacji transakcji"](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio otwiera projekt z repozytorium.

1. Jeśli masz dostępny plik rozwiązania, pojawi się on w menu wysuwu "Rozwiązania i foldery". Wybierz go, a program Visual Studio otworzy rozwiązanie.

   ![Wybierz, co chcesz otworzyć z listy rozwijanej Eksploratora rozwiązań](./media/open-proj-repo-github-solutions-folders-picker.png)

   Jeśli nie masz pliku rozwiązania (w szczególności pliku .sln) w repozytorium, menu wysuń powie "Nie znaleziono rozwiązań". Można jednak dwukrotnie kliknąć dowolny plik z menu folderów, aby otworzyć go w edytorze kodu programu Visual Studio.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Otwieranie projektu z repozytorium usługi Azure DevOps

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **Otwórz plik** > **Open** > **z kontroli źródła**.

   Zostanie otwarte okienko **Eksplorator zespołu — połącz.**

    ![Okno Eksploratora zespołu w środowisku IDE programu Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Oto dwa sposoby nawiązanie połączenia z repozytorium usługi Azure DevOps:

      - W sekcji **Hosted Service Providers (Hosted Service Providers)** wybierz pozycję **Połącz...**.

        ![Sekcja Hosted Service Providers okna Eksploratora zespołu w środowisku IDE programu Visual Studio](./media/open-proj-repo-azure-devops.png)

      - Z listy rozwijanej **Zarządzanie połączeniami** wybierz pozycję **Połącz z projektem...**.

        ![Sekcja Zarządzanie połączeniami okna Eksploratora zespołu w środowisku IDE programu Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. W oknie **dialogowym Łączenie z projektem** wybierz repozytorium, z którego chcesz się połączyć, a następnie wybierz pozycję **Klonuj**.

      ![Okno dialogowe "Łączenie się z projektem", które jest generowane z programu Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > To, co widzisz w polu listy, zależy od repozytoriów programu Azure DevOps, do których masz dostęp.

1. Po sklonowanie repozytorium w programie Visual Studio, Eksplorator zespołu zostanie zamknięty i zostanie otwarty Eksplorator rozwiązań. Pojawi się komunikat *Click on Solutions and Folders powyżej, aby wyświetlić listę rozwiązań*. Wybierz **rozwiązania i foldery**.

      ![Powiadomienie "Rozwiązania i foldery" z Eksploratora zespołu w programie Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Plik rozwiązania (w szczególności plik .sln), pojawi się w menu wysuwu "Rozwiązania i foldery". Wybierz go, a program Visual Studio otworzy rozwiązanie.

   Jeśli nie masz pliku rozwiązania w repozytorium, menu wysuń powie "Nie znaleziono rozwiązań". Można jednak dwukrotnie kliknąć dowolny plik z menu folderów, aby otworzyć go w edytorze kodu programu Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

1. W oknie startowym wybierz pozycję **Klonuj lub wyewidencjonuj kod**.

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. W sekcji **Przeglądaj repozytorium** wybierz pozycję **Azure DevOps**.

   ![Wyświetl okno "Klonuj lub wyewidencjonuj kod"](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Jeśli widzisz okno logowania, zaloguj się na swoje konto.

1. W oknie **dialogowym Łączenie z projektem** wybierz repozytorium, z którego chcesz się połączyć, a następnie wybierz pozycję **Klonuj**.

      ![Okno dialogowe "Łączenie się z projektem", które jest generowane z programu Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > To, co widzisz w polu listy, zależy od repozytoriów programu Azure DevOps, do których masz dostęp.

   Visual Studio otwiera **Eksploratora zespołu** i po zakończeniu klonowania zostanie wyświetlone powiadomienie.

     ![Okno Eksploratora zespołu w programie Visual Studio po zakończeniu klonowania](./media/vs-2019/clone-complete-azure-devops.png)

1. Aby wyświetlić foldery i pliki, wybierz łącze **Pokaż widok folderu.**

     ![Sekcja Rozwiązania okna Eksploratora zespołu w programie Visual Studio po zakończeniu klonowania](./media/vs-2019/show-folder-view-azure-devops.png)

     Program Visual Studio otwiera **Eksploratora rozwiązań**.

1. Wybierz **łącze Rozwiązania i foldery, aby wyszukać** plik rozwiązania (w szczególności plik .sln), który ma być otwarty.

      ![Powiadomienie "Rozwiązania i foldery" z Eksploratora zespołu w programie Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Jeśli nie masz pliku rozwiązania w repozytorium, zostanie wyświetlony komunikat "Nie znaleziono rozwiązań". Można jednak dwukrotnie kliknąć dowolny plik z menu folderów, aby otworzyć go w edytorze kodu programu Visual Studio.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Jeśli chcesz zakodować program Visual Studio, zapoznaj się z dowolnym z następujących samouczków specyficznych dla języka:

- [Samouczki programu Visual Studio | **C#**](./csharp/index.yml)
- [Samouczki programu Visual Studio | **Visual Basic (Visual Basic)**](./visual-basic/index.yml)
- [Samouczki programu Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Samouczki programu Visual Studio | **Python**](/visualstudio/python/)
- [Samouczki programu Visual Studio | **JavaScript**, **TypeScript**i **Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>Zobacz też

- [Usługi Azure DevOps: wprowadzenie do usługi Azure Repos i visual studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Wprowadzenie do usługi Azure DevOps](/learn/modules/get-started-with-devops/)