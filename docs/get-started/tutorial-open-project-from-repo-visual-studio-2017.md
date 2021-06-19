---
title: 'Samouczek: otwieranie projektu z repo w programie Visual Studio 2017'
description: Dowiedz się, jak otworzyć projekt w repozytorium Git lub Azure DevOps przy użyciu programu Visual Studio 2017.
ms.custom: vs-acquisition, get-started
ms.date: 02/15/2021
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
ms.openlocfilehash: 5543a568f7246d9600ba375d9a1cf19af4cbd2d4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389205"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Samouczek: otwieranie projektu z repo w programie Visual Studio 2017

W tym samouczku użyjesz programu Visual Studio 2017, aby po raz pierwszy nawiązać połączenie z repozytorium, a następnie otworzysz z niego projekt.

> [!TIP]
> Istnieje nowy, bardziej zintegrowany sposób nawiązywania połączenia z repozytorium GitHub w Visual Studio [2019 r.](https://visualstudio.microsoft.com/downloads) Aby uzyskać więcej informacji, zobacz stronę [**New Git experience in Visual Studio 2019 (Nowe środowisko Git w programie Visual Studio 2019).**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true)

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Otwieranie projektu z repozytorium GitHub przy użyciu programu Visual Studio 2017

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **Plik** Otwórz  >  **otwórz** z kontroli  >  **kodu źródłowego.**

   Zostanie **otwarte Team Explorer —** Połącz.

    ![Okno Team Explorer w Visual Studio IDE](./media/open-proj-repo-team-explorer.png)

1. W sekcji **Lokalne repozytoria Git** wybierz pozycję **Klonuj**.

    ![Wybierz pozycję Klonuj w sekcji Lokalne repozytoria Git](./media/open-proj-repo-local-git-repo-clone.png)

1. W polu * Wprowadź adres URL repozytorium Git do sklonowania _, wpisz lub wklej adres URL repozytorium,**a** następnie naciśnij klawisz _*Enter**. (Może zostać wyświetlony monit o zalogowanie się do usługi GitHub. Jeśli tak, zrób to).

   Po Visual Studio sklonowania twojego Team Explorer zostanie zamknięte i Eksplorator rozwiązań otwarte. Zostanie wyświetlony komunikat Kliknij *rozwiązania i foldery powyżej, aby wyświetlić listę rozwiązań*. Wybierz **pozycję Rozwiązania i foldery.**

   ![Wybierz pozycję "Rozwiązania i foldery" z Eksplorator rozwiązań](./media/open-proj-repo-github-solutions-folders.png)

1. Jeśli masz dostępny plik rozwiązania, będzie on wyświetlany w wysuwanych menu "Rozwiązania i foldery". Wybierz go, a Visual Studio otworzy twoje rozwiązanie.

   ![Wybierz, co chcesz otworzyć, z Eksplorator rozwiązań listy rozwijanej](./media/open-proj-repo-github-solutions-folders-picker.png)

   Jeśli w swoim repocie nie masz pliku rozwiązania (konkretnie pliku sln), w wysuwalnym menu pojawi się tekst "No Solutions Found" (Nie znaleziono żadnych rozwiązań). Można jednak kliknąć dwukrotnie dowolny plik z menu folderu, aby otworzyć go w Visual Studio kodu.

### <a name="review-your-work"></a>Przeglądanie pracy

Wyświetl następującą animację, aby sprawdzić pracę, która została ukończona w poprzedniej sekcji.

   ![Animacja otwierania projektu w repozytorium GitHub przy użyciu Visual Studio](./media/open-project-from-github.gif)

> [!NOTE]
> Aby uzyskać informacje specyficzne dla programu Visual Studio 2019, zobacz stronę Otwieranie projektu z Visual Studio [2019.](tutorial-open-project-from-repo-visual-studio-2019.md)

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Otwieranie projektu z Azure DevOps przy użyciu programu Visual Studio 2017

1. Otwórz program Visual Studio 2017.

1. Na górnym pasku menu wybierz pozycję **Plik** Otwórz  >  **otwórz** z kontroli  >  **kodu źródłowego.**

   Zostanie **otwarte Team Explorer —** Połącz.

    ![Okno Team Explorer w Visual Studio IDE](./media/open-proj-repo-team-explorer.png)

1. Oto dwa sposoby nawiązywania połączenia z Azure DevOps danych:

      - W sekcji **Dostawcy usług hostowanych** wybierz pozycję **Połącz...**.

        ![Sekcja Dostawcy usług hostowanych w oknie Team Explorer w Visual Studio IDE](./media/open-proj-repo-azure-devops.png)

      - Z listy **rozwijanej Zarządzaj** połączeniami wybierz pozycję **Połącz z projektem...**.

        ![Sekcja Zarządzanie połączeniami w oknie Team Explorer w Visual Studio IDE](./media/open-proj-repo-azuredevops-manage-connections.png)

1. W **oknie dialogowym Łączenie** z projektem wybierz repopo, z którym chcesz nawiązać połączenie, a następnie wybierz pozycję **Klonuj**.

      ![Okno dialogowe "Łączenie z projektem" wygenerowane na podstawie Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > To, co widzisz w polu listy, zależy od Azure DevOps repozytoriów, do których masz dostęp.

1. Po Visual Studio sklonowania twojego Team Explorer zostanie zamknięte i Eksplorator rozwiązań otwarte. Zostanie wyświetlony komunikat Kliknij *rozwiązania i foldery powyżej, aby wyświetlić listę rozwiązań*. Wybierz **pozycję Rozwiązania i foldery.**

      ![Powiadomienie "Rozwiązania i foldery" z Team Explorer w Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Plik rozwiązania (w szczególności plik sln) pojawi się w wysuwalnym menu "Rozwiązania i foldery". Wybierz go, a Visual Studio otworzy twoje rozwiązanie.

   Jeśli w swoim repocie nie masz pliku rozwiązania, w wysuwanych menu pojawi się tekst "No Solutions Found" (Nie znaleziono żadnych rozwiązań). Można jednak kliknąć dwukrotnie dowolny plik z menu folderu, aby otworzyć go w Visual Studio kodu.

## <a name="next-steps"></a>Następne kroki

Jeśli wszystko jest gotowe do programowania w programie Visual Studio 2017, poznaj dowolny z następujących samouczków specyficznych dla języka:

- [Visual Studio samouczków | **C#**](./csharp/index.yml)
- [Visual Studio samouczków | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio samouczków | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio samouczków | **Język Python**](../python/index.yml)
- [Visual Studio samouczków | **JavaScript,** **TypeScript** i **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Zobacz też

- [Otwieranie projektu z repo w Visual Studio 2019 r.](tutorial-open-project-from-repo-visual-studio-2019.md)
- [Nowe środowisko usługi Git w Visual Studio 2019 r.](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: Wprowadzenie do Azure Repos i Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Wprowadzenie do Azure DevOps](/learn/modules/get-started-with-devops/)
