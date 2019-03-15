---
title: 'Samouczek: Otwórz projekt z repozytorium'
description: Dowiedz się, jak otworzyć projekt w repozytorium Git lub DevOps platformy Azure przy użyciu programu Visual Studio.
ms.custom: get-started
ms.date: 03/13/2019
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
ms.openlocfilehash: f017e0ef3d7b76ba4d5de18ecab614f030b07501
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070077"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Samouczek: Otwórz projekt z repozytorium

W tym samouczku użyjesz programu Visual Studio do łączenia się z repozytorium po raz pierwszy, a następnie otwórz projekt z niego.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+rc) strony, aby zainstalować go za darmo.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Otwórz projekt z repozytorium GitHub

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

## <a name="open-a-project-from-an-azure-devops-repo"></a>Otwórz projekt z repozytorium DevOps platformy Azure

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
  
## <a name="next-steps"></a>Następne kroki

Gdy wszystko będzie gotowe do kodu za pomocą programu Visual Studio, od razu rozpocząć korzystanie w każdym z następujących samouczków specyficzny dla języka:

- [Visual Studio tutorials | **C#**](./csharp/index.yml)
- [Visual Studio tutorials | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio tutorials | **C++**](/cpp/get-started/)
- [Visual Studio tutorials | **Python**](/visualstudio/python/)
- [Samouczki usługi Visual Studio | **JavaScript**, **TypeScript**, i **środowiska Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>Zobacz także

- [Azure DevOps Services: Rozpoczynanie pracy z repozytoriami na platformie Azure i programu Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Dowiedz się, firmy Microsoft: Rozpoczynanie pracy z usługą DevOps platformy Azure](/learn/modules/get-started-with-devops/)