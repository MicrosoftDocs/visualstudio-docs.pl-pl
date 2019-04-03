---
title: 'Samouczek: Otwieranie projektu z repozytorium'
description: Dowiedz się, jak otworzyć projekt w repozytorium Git lub DevOps platformy Azure przy użyciu programu Visual Studio.
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
ms.openlocfilehash: 928e77c5c28b76570525b8ea9037cd0d0cef7f99
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857570"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Samouczek: Otwieranie projektu z repozytorium

W tym samouczku użyjesz programu Visual Studio do łączenia się z repozytorium po raz pierwszy, a następnie otwórz projekt z niego.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) strony, aby zainstalować go za darmo.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Otwórz projekt z repozytorium GitHub

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na pasku menu u góry wybierz **pliku** > **Otwórz** > **Otwórz z kontroli źródła**.

   **Team Explorer — łączenie** zostanie otwarte okienko.

    ![Okna programu Team Explorer w środowisku IDE programu Visual Studio](./media/open-proj-repo-team-explorer.png)

1. W **lokalne repozytoria Git** wybierz pozycję **klonowania**.

    ![Wybierz przycisk Klonuj, w sekcji lokalne repozytoria Git](./media/open-proj-repo-local-git-repo-clone.png)

1. W polu informującym ***wprowadź adres URL repozytorium Git, sklonować***wpisz lub wklej adres URL repozytorium, a następnie naciśnij klawisz **Enter**. (Może zostać wyświetlony monit, zaloguj się w witrynie GitHub; Jeśli tak, to zrobić).

   Po programu Visual Studio klonuje repozytorium, zamyka program Team Explorer i Eksplorator rozwiązań otwiera. Pojawi się komunikat informujący, że *kliknij rozwiązania i foldery powyżej, aby wyświetlić listę rozwiązań*. Wybierz **rozwiązania i foldery**.

   ![Wybierz pozycję "Rozwiązania i foldery" z poziomu Eksploratora rozwiązań](./media/open-proj-repo-github-solutions-folders.png)

1. Jeśli masz pliku rozwiązania, które jest dostępne, pojawi się w menu wysuwanego "Rozwiązania i foldery". Wybierz go, a program Visual Studio otwiera rozwiązania.

   ![Wybierz, co chcesz otworzyć z listy rozwijanej w Eksploratorze rozwiązań](./media/open-proj-repo-github-solutions-folders-picker.png)

   Jeśli nie masz plik rozwiązania (w szczególności pliku .sln) w repozytorium, menu wysuwanego będzie wyświetlany tekst "Nie znaleziono rozwiązania." Jednak można kliknąć dwukrotnie dowolny plik z menu folderu, aby otworzyć go w edytorze kodu programu Visual Studio.

### <a name="review-your-work"></a>Przejrzyj swoją pracę

Wyświetl następujące animacji, aby sprawdzić prac, które można wykonać w poprzedniej sekcji.

   ![Animacja otwierania projektu w repozytorium GitHub przy użyciu programu Visual Studio](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Open Visual Studio 2019.

1. W oknie rozpoczęcia wybierz **klonowania lub Sprawdź kod**.

   ![Wyświetlanie w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Wprowadź lub wpisz lokalizację repozytorium, a następnie wybierz **klonowania**.

   ![Wyświetl okno "kodu klonowania lub realizacji transakcji"](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio otwiera projektu z repozytorium.

1. Jeśli masz pliku rozwiązania, które jest dostępne, pojawi się w menu wysuwanego "Rozwiązania i foldery". Wybierz go, a program Visual Studio otwiera rozwiązania.

   ![Wybierz, co chcesz otworzyć z listy rozwijanej w Eksploratorze rozwiązań](./media/open-proj-repo-github-solutions-folders-picker.png)

   Jeśli nie masz plik rozwiązania (w szczególności pliku .sln) w repozytorium, menu wysuwanego będzie wyświetlany tekst "Nie znaleziono rozwiązania." Jednak można kliknąć dwukrotnie dowolny plik z menu folderu, aby otworzyć go w edytorze kodu programu Visual Studio.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Otwórz projekt z repozytorium DevOps platformy Azure

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

1. Na pasku menu u góry wybierz **pliku** > **Otwórz** > **Otwórz z kontroli źródła**.

   **Team Explorer — łączenie** zostanie otwarte okienko.

    ![Okna programu Team Explorer w środowisku IDE programu Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Poniżej przedstawiono dwa sposoby podłączenia do repozytorium DevOps platformy Azure:

      - W **dostawcy usług hostowanych** wybierz pozycję **Connect...** .

        ![Dostawcy usług hostowanych części okna programu Team Explorer w środowisku IDE programu Visual Studio](./media/open-proj-repo-azure-devops.png)

      - W **Zarządzaj połączeniami** listy rozwijanej wybierz **nawiązywanie połączenia z projektem...** .

        ![Zarządzanie połączeniami części okna programu Team Explorer w środowisku IDE programu Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. W **nawiązywanie połączenia z projektem** okna dialogowego Wybierz repozytorium, którą chcesz nawiązać połączenie, a następnie wybierz **klonowania**.

      ![Okno dialogowe "Łączenie do projektu", który jest generowany w programie Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Zostanie wyświetlony w polu listy, zależy od repozytoriów DevOps platformy Azure, które mają dostęp do.

1. Po programu Visual Studio klonuje repozytorium, zamyka program Team Explorer i Eksplorator rozwiązań otwiera. Pojawi się komunikat informujący, że *kliknij rozwiązania i foldery powyżej, aby wyświetlić listę rozwiązań*. Wybierz **rozwiązania i foldery**.

      ![Powiadomienia "Rozwiązania i foldery" w programie Team Explorer w programie Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Plik rozwiązania (w szczególności jest .sln plik), zostanie wyświetlona w menu wysuwanego "Rozwiązania i foldery". Wybierz go, a program Visual Studio otwiera rozwiązania.

   Jeśli nie masz plik rozwiązania w repozytorium, menu wysuwanego będzie wyświetlany tekst "Nie znaleziono rozwiązań". Jednak można kliknąć dwukrotnie dowolny plik z menu folderu, aby otworzyć go w edytorze kodu programu Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Open Visual Studio 2019.

1. W oknie rozpoczęcia wybierz **klonowania lub Sprawdź kod**.

   ![Wyświetlanie w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. W **Przeglądaj repozytorium** wybierz pozycję **DevOps platformy Azure**.

   ![Wyświetl okno "Klonowania lub zapoznaj się z kodem"](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Jeśli zobaczysz okno logowania, zaloguj się do swojego konta.

1. W **nawiązywanie połączenia z projektem** okna dialogowego Wybierz repozytorium, którą chcesz nawiązać połączenie, a następnie wybierz **klonowania**.

      ![Okno dialogowe "Łączenie do projektu", który jest generowany w programie Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Zostanie wyświetlony w polu listy, zależy od repozytoriów DevOps platformy Azure, które mają dostęp do.

   Zostanie otwarty program Visual Studio **Team Explorer** i pojawi się powiadomienie po zakończeniu klonowania.

     ![Okna programu Team Explorer w programie Visual Studio po ukończeniu klonowania](./media/vs-2019/clone-complete-azure-devops.png)

1. Aby wyświetlić pliki i foldery, wybierz **Pokaż widok folderu** łącza.

     ![Rozwiązania części okna programu Team Explorer w programie Visual Studio po ukończeniu klonowania](./media/vs-2019/show-folder-view-azure-devops.png)

     Zostanie otwarty program Visual Studio **Eksploratora rozwiązań**.

1. Wybierz **rozwiązania i foldery** łącze, aby wyszukać plik rozwiązania (w szczególności plik sln) otworzyć.

      ![Powiadomienia "Rozwiązania i foldery" w programie Team Explorer w programie Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Jeśli nie masz plik rozwiązania w repozytorium, zostanie wyświetlony komunikat "Nie znaleziono rozwiązań". Jednak można kliknąć dwukrotnie dowolny plik z menu folderu, aby otworzyć go w edytorze kodu programu Visual Studio.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Gdy wszystko będzie gotowe do kodu za pomocą programu Visual Studio, od razu rozpocząć korzystanie w każdym z następujących samouczków specyficzny dla języka:

- [Visual Studio tutorials | **C#**](./csharp/index.yml)
- [Samouczki usługi Visual Studio | **Języka Visual Basic**](./visual-basic/index.yml)
- [Visual Studio tutorials | **C++**](/cpp/get-started/)
- [Samouczki usługi Visual Studio | **Języka Python**](/visualstudio/python/)
- [Samouczki usługi Visual Studio | **JavaScript**, **TypeScript**, i **środowiska Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>Zobacz także

- [Azure DevOps Services: Rozpoczynanie pracy z repozytoriami na platformie Azure i programu Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Dowiedz się, firmy Microsoft: Rozpoczynanie pracy z usługą DevOps platformy Azure](/learn/modules/get-started-with-devops/)