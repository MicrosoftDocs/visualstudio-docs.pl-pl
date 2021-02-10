---
title: 'Samouczek: Otwieranie projektu z repozytorium w programie Visual Studio 2017'
description: Dowiedz się, jak otworzyć projekt w repozytorium Git lub Azure DevOps za pomocą programu Visual Studio 2017.
ms.custom: get-started
ms.date: 01/25/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2017
ms.openlocfilehash: 97bfe7178d3bd744d1e441f8428cd38e8241b721
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951930"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Samouczek: Otwieranie projektu z repozytorium w programie Visual Studio 2017

W tym samouczku użyjesz programu Visual Studio 2017, aby nawiązać połączenie z repozytorium po raz pierwszy, a następnie otworzyć projekt z tego projektu.

> [!TIP]
> Istnieje nowy, bardziej w pełni zintegrowany sposób łączenia się z repozytorium GitHub w programie [Visual Studio 2019](https://visualstudio.microsoft.com/downloads). Aby uzyskać więcej informacji, zobacz [**nowe środowisko Git na stronie programu Visual Studio 2019**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true) .

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Otwieranie projektu z repozytorium GitHub przy użyciu programu Visual Studio 2017

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **plik**  >  **Otwórz**  >  **Otwórz z kontroli źródła**.

   Zostanie otwarte okienko **Team Explorer-Connect** .

    ![Okno Team Explorer w środowisku IDE programu Visual Studio](./media/open-proj-repo-team-explorer.png)

1. W sekcji **lokalne repozytoria Git** wybierz pozycję **Klonuj**.

    ![Wybierz klon z lokalnej sekcji repozytoria Git](./media/open-proj-repo-local-git-repo-clone.png)

1. W polu mówiącym ***wprowadź adres URL repozytorium git, aby sklonować**, wpisz lub wklej adres URL repozytorium, a następnie naciśnij klawisze _ * ENTER * *. (Może pojawić się monit o zalogowanie się do usługi GitHub; Jeśli tak, zrób to).

   Po sklonowaniu repozytorium przez program Visual Studio Team Explorer zamyka się i Eksplorator rozwiązań otwiera. Zostanie wyświetlony komunikat z informacją, że *kliknij pozycję rozwiązania i foldery powyżej, aby wyświetlić listę rozwiązań*. Wybierz **rozwiązania i foldery**.

   ![Wybierz pozycję "rozwiązania i foldery" z Eksplorator rozwiązań](./media/open-proj-repo-github-solutions-folders.png)

1. Jeśli masz dostępny plik rozwiązania, zostanie on wyświetlony w menu "roztwory i foldery". Wybierz go, a program Visual Studio otwiera Twoje rozwiązanie.

   ![Wybierz, co chcesz otworzyć z listy rozwijanej Eksplorator rozwiązań](./media/open-proj-repo-github-solutions-folders-picker.png)

   Jeśli w repozytorium nie ma pliku rozwiązania (w odniesieniu do pliku. sln), w menu rozwijanym zostanie wyświetlona informacja "nie znaleziono rozwiązań". Można jednak kliknąć dwukrotnie dowolny plik z menu folder, aby otworzyć go w edytorze kodu programu Visual Studio.

### <a name="review-your-work"></a>Przejrzyj swoją służbę

Wyświetl poniższą animację, aby sprawdzić pracę zakończono w poprzedniej sekcji.

   ![Animacja otwierania projektu w repozytorium GitHub przy użyciu programu Visual Studio](./media/open-project-from-github.gif)

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Otwieranie projektu z repozytorium DevOps platformy Azure przy użyciu programu Visual Studio 2017

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **plik**  >  **Otwórz**  >  **Otwórz z kontroli źródła**.

   Zostanie otwarte okienko **Team Explorer-Connect** .

    ![Okno Team Explorer w środowisku IDE programu Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Poniżej przedstawiono dwa sposoby nawiązywania połączenia z repozytorium usługi Azure DevOps:

      - W sekcji **dostawcy usług hostowanych** wybierz pozycję **Połącz...**.

        ![Sekcja dostawcy usług hostowanych okna Team Explorer w środowisku IDE programu Visual Studio](./media/open-proj-repo-azure-devops.png)

      - Z listy rozwijanej **Zarządzaj połączeniami** wybierz pozycję **Połącz z projektem...**.

        ![Sekcja zarządzanie połączeniami okna Team Explorer w środowisku IDE programu Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. W oknie dialogowym **Połącz z projektem** wybierz repozytorium, z którym chcesz się połączyć, a następnie wybierz pozycję **Klonuj**.

      ![Okno dialogowe "łączenie z projektem", które zostało wygenerowane z programu Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Elementy wyświetlane w polu listy zależą od repozytoriów usługi Azure DevOps, do których masz dostęp.

1. Po sklonowaniu repozytorium przez program Visual Studio Team Explorer zamyka się i Eksplorator rozwiązań otwiera. Zostanie wyświetlony komunikat z informacją, że *kliknij pozycję rozwiązania i foldery powyżej, aby wyświetlić listę rozwiązań*. Wybierz **rozwiązania i foldery**.

      ![Powiadomienie "rozwiązania i foldery" z Team Explorer w programie Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Plik rozwiązania (w specjalnym pliku. sln) pojawi się w menu rozwijanym "rozwiązania i foldery". Wybierz go, a program Visual Studio otwiera Twoje rozwiązanie.

   Jeśli w repozytorium nie ma pliku rozwiązania, w menu rozwijanym zostanie wyświetlona informacja "nie znaleziono rozwiązań". Można jednak kliknąć dwukrotnie dowolny plik z menu folder, aby otworzyć go w edytorze kodu programu Visual Studio.

## <a name="next-steps"></a>Następne kroki

Jeśli wszystko jest gotowe do kodu w programie Visual Studio 2017, szczegółowe do dowolnego z następujących samouczków dotyczących języka:

- [Samouczki programu Visual Studio | Język **C#**](./csharp/index.yml)
- [Samouczki programu Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Samouczki programu Visual Studio | Język **C++**](/cpp/get-started/tutorial-console-cpp)
- [Samouczki programu Visual Studio | Język **Python**](../python/index.yml)
- [Samouczki programu Visual Studio | **JavaScript**, **TypeScript** i **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Zobacz też

- [Azure DevOps Services: wprowadzenie do Azure Repos i programu Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Rozpoczynanie pracy z usługą Azure DevOps](/learn/modules/get-started-with-devops/)
- [Nowe środowisko Git w programie Visual Studio 2019](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true)
