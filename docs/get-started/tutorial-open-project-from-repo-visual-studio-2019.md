---
title: 'Samouczek: otwieranie projektu z repo w programie Visual Studio 2019'
description: Dowiedz się, jak otworzyć projekt w repozytorium Git Azure DevOps przy użyciu programu Visual Studio 2019.
ms.custom: vs-acquisition, get-started
ms.date: 03/18/2021
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
monikerRange: vs-2019
ms.openlocfilehash: b6f7cd57a1753ca5926ac73a9bb4c8c918d1bd10
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389946"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Samouczek: otwieranie projektu z repo

W tym samouczku po raz pierwszy Visual Studio z repozytorium, a następnie otworzysz z niego projekt.

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

## <a name="open-a-project-from-a-github-repo"></a>Otwieranie projektu z repozytorium GitHub

Sposób otwierania projektu z repozytorium GitHub przy użyciu programu Visual Studio 2019 zależy od posiadanej wersji. W szczególności, jeśli zainstalowano wersję [**16.8**](/visualstudio/releases/2019/release-notes/) lub nowszą, dostępne jest nowe, bardziej zintegrowane środowisko [Git](../ide/git-with-visual-studio.md) w Visual Studio dla Ciebie.

Niezależnie od zainstalowanej wersji zawsze możesz otworzyć projekt z repozytorium GitHub za pomocą Visual Studio.

#### <a name="168-and-later"></a>[16.8 i nowsze](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Klonowanie repozytorium GitHub, a następnie otwieranie projektu

1. Otwórz Visual Studio 2019 r.

1. W oknie uruchamiania wybierz pozycję **Clone a repository (Sklonuj repozytorium).**

   ![Zrzut ekranu przedstawiający okno dialogowe Klonowanie repozytorium Visual Studio 2019 w wersji 16.8 lub nowszej](../ide/media/vs-2019/clone-repository.png)

1. Wprowadź lub wpisz lokalizację repozytorium, a następnie wybierz pozycję **Klonuj**.

   ![Zrzut ekranu przedstawiający okno dialogowe Klonowanie repozytorium, w którym wprowadzasz adres URL repozytorium Git Visual Studio 2019 w wersji 16.8 lub nowszej](../ide/media/vs-2019/clone-repository-enter-location.png)

1. W oknie dialogowym Informacje o użytkowniku **usługi Git** może zostać wyświetlone pytanie o informacje dotyczące logowania użytkownika. Możesz dodać informacje lub edytować podane informacje domyślne.

   ![Zrzut ekranu przedstawiający okno dialogowe Informacje o użytkowniku usługi Git, w którym wprowadzasz lub edytujesz informacje o koncie w programie Visual Studio 2019 w wersji 16.8 lub nowszej](../ide/media/vs-2019/git-user-information-dialog.png)

    Wybierz **pozycję Zapisz,** aby dodać informacje do globalnego pliku gitconfig. (Możesz też wybrać tę opcję później, wybierając pozycję **Anuluj).**

    > [!TIP]
    > Aby uzyskać więcej informacji na temat logowania Visual Studio, zobacz stronę Logowanie [do Visual Studio](../ide/signing-in-to-visual-studio.md) aplikacji. Aby uzyskać szczegółowe informacje na temat logowania się przy użyciu konta usługi GitHub, zobacz stronę Praca z kontami [usługi GitHub Visual Studio](../ide/work-with-github-accounts.md) witrynie.

    Następnie Visual Studio automatycznie ładuje i otwiera rozwiązanie z repozytorium.

   ![Zrzut ekranu przedstawiający projekt w usłudze Git, który jest otwarty w programie Eksplorator rozwiązań w wersji Visual Studio 2019 16.8 lub nowszej](../ide/media/vs-2019/git-solution-explorer.png )

1. Jeśli repozytorium zawiera wiele rozwiązań, zobaczysz je w Eksplorator rozwiązań. Listę rozwiązań można wyświetlić, wybierając przycisk **Przełącz widoki** w Eksplorator rozwiązań.

   ![Zrzut ekranu przedstawiający projekt w usłudze Git, który jest otwarty w usłudze Eksplorator rozwiązań, z przyciskiem Przełącz widoki wyróżniony w programie Visual Studio 2019 w wersji 16.8 lub nowszej](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Eksplorator rozwiązań następnie udostępnia opcję otwarcia folderu głównego w  widoku folderu lub wybrania pliku rozwiązania do otwarcia.

   ![Zrzut ekranu przedstawiający plik sln w usłudze Git otwarty w programie Eksplorator rozwiązań po wybraniu przycisku Przełącz widoki w programie Visual Studio 2019 w wersji 16.8 lub nowszej](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Aby przełączyć widok, ponownie wybierz **przycisk Przełącz widoki.**

    > [!TIP]
    > Możesz również użyć menu **Usługi Git** w Visual Studio IDE, aby sklonować repozytorium i otworzyć projekt.
    >
    > ![Zrzut ekranu przedstawiający menu usługi Git w Visual Studio 2019 w wersji 16.8 lub nowszej](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Otwieranie projektu lokalnie z wcześniej sklonowanego repozytorium GitHub

1. Otwórz Visual Studio 2019 r.

1. W oknie uruchamiania wybierz **pozycję Otwórz projekt lub rozwiązanie.**

    Visual Studio wystąpienie usługi Eksplorator plików, w którym możesz przejść do swojego rozwiązania lub projektu, a następnie wybrać je, aby je otworzyć.

   ![Zrzut ekranu przedstawiający okno "Otwieranie projektu lub rozwiązania" w programie Visual Studio 2019 w wersji 16.8 lub nowszej](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Jeśli niedawno otwarto projekt lub rozwiązanie, wybierz go w sekcji Otwórz **ostatnie,** aby szybko otworzyć go ponownie.

    > [!TIP]
    > Możesz również użyć menu **Git** w programie Visual Studio IDE, aby otworzyć foldery i pliki lokalne z wcześniej sklonowanego repozytorium.
    >
    > ![Zrzut ekranu przedstawiający menu Usługi Git w Visual Studio 2019 w wersji 16.8 lub nowszej z rozwiniętą opcją Repozytoria lokalne](../ide/media/vs-2019/git-menu-local-repositories.png)

    Rozpocznij kodowanie!

#### <a name="167-and-earlier"></a>[16.7 i starsze](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Klonowanie repozytorium GitHub, a następnie otwieranie projektu

1. Otwórz Visual Studio 2019 r.

1. W oknie uruchamiania wybierz pozycję **Klonuj lub wyewidencj go.**

   ![Zrzut ekranu przedstawiający okno "Tworzenie nowego projektu" w programie Visual Studio 2019 w wersji 16.7 lub starszej](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Wprowadź lub wpisz lokalizację repozytorium, a następnie wybierz pozycję **Klonuj**.

   ![Zrzut ekranu przedstawiający okno "Klonuj lub wyewidencjonaj kod" Visual Studio 2019 w wersji 16.7 i starszych](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio projekt zostanie otwarty z tego repo.

1. Jeśli masz dostępny plik rozwiązania, zostanie on wyświetlony w wysuwanych menu "Rozwiązania i foldery". Wybierz go, a Visual Studio spowoduje otwarcie rozwiązania.

   ![Zrzut ekranu przedstawiający Eksplorator rozwiązań rozwijanej w programie Visual Studio 2019 w wersji 16.7 lub starszej](./media/open-proj-repo-github-solutions-folders-picker.png)

   Jeśli w swoim repocie nie masz pliku rozwiązania (konkretnie pliku sln), w wysuwalnym menu będzie widać tekst "No Solutions Found" (Nie znaleziono żadnych rozwiązań). Można jednak kliknąć dwukrotnie dowolny plik z menu folderu, aby otworzyć go w Visual Studio kodu.

    Rozpocznij kodowanie!

---

> [!NOTE]
> Aby uzyskać informacje specyficzne dla programu Visual Studio 2017, zobacz stronę Open [a project from a repo in Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md) (Otwieranie projektu z Visual Studio 2017).

## <a name="connect-to-an-azure-devops-server"></a>Nawiązywanie połączenia z serwerem Azure DevOps serwera

To, co zobaczysz po nawiązać połączenie z serwerem Azure DevOps przy użyciu programu Visual Studio 2019, zależy od posiadanej wersji. W szczególności, jeśli zainstalowano wersję [**16.8**](/visualstudio/releases/2019/release-notes/) lub nowszą, interfejs użytkownika został zmieniony w celu uwzględnienia nowego, bardziej zintegrowanego interfejsu Git w programie [Visual Studio](../ide/git-with-visual-studio.md) w Visual Studio.

Niezależnie od zainstalowanej wersji zawsze możesz nawiązać połączenie z serwerem Azure DevOps pomocą Visual Studio.

#### <a name="168-and-later"></a>[16.8 i nowsze](#tab/vs168later)

1. Otwórz Visual Studio 2019 r.

1. W oknie uruchamiania wybierz pozycję **Clone a repository (Sklonuj repozytorium).**

   ![Zrzut ekranu przedstawiający okno dialogowe Klonowanie repozytorium w programie Visual Studio 2019 w wersji 16.8 lub nowszej dla Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. W **sekcji Przeglądanie repozytorium** wybierz pozycję **Azure DevOps**.

    ![Zrzut ekranu przedstawiający sekcję "Przeglądanie repozytorium" okna dialogowego "Łączenie z projektem" w programie Visual Studio 2019 w wersji 16.8 lub nowszej](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Jeśli zostanie otwarte okno logowania, zaloguj się do swojego konta.

1. W **oknie dialogowym Łączenie** z projektem wybierz repopo, z którym chcesz nawiązać połączenie, a następnie wybierz pozycję **Klonuj**.

      ![Zrzut ekranu przedstawiający okno dialogowe "Łączenie z projektem" wygenerowane na podstawie programu Visual Studio 2019 w wersji 16.8 lub nowszej](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Jeśli nie widzisz wstępnie wypełnionej listy repos, z którym chcesz nawiązać połączenie, wybierz pozycję **Dodaj** Azure DevOps Server, aby wprowadzić adres URL serwera. (Alternatywnie może zostać wyświetlony monit "Nie znaleziono serwerów" z linkami do dodawania istniejącego Azure DevOps Server lub tworzenia Azure DevOps konta).

   Następnie Visual Studio plik **Eksplorator rozwiązań** foldery i pliki.

1. Wybierz **kartę Team Explorer,** aby wyświetlić Azure DevOps akcje.

      ![Zrzut ekranu przedstawiający okno dialogowe Team Explorer "Visual Studio 2019 w wersji 16.8 lub nowszej"](../ide/media/vs-2019/team-explorer-azure-devops.png)

#### <a name="167-and-earlier"></a>[16.7 i starsze](#tab/vs167earlier)

1. Otwórz Visual Studio 2019 r.

1. W oknie uruchamiania wybierz pozycję **Klonuj lub wyewidencj go.**

   ![Zrzut ekranu przedstawiający okno "Tworzenie nowego projektu" w programie Visual Studio 2019 w wersji 16.7 lub starszej](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. W **sekcji Przeglądanie repozytorium** wybierz pozycję **Azure DevOps**.

   ![Zrzut ekranu przedstawiający okno "Klonowanie lub wyewidencjonaj kod" z sekcją "Przeglądanie repozytorium", która zawiera listę Azure DevOps w wersji 16.7 i starszych w programie Visual Studio 2019](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Jeśli zostanie otwarte okno logowania, zaloguj się do swojego konta.

1. W **oknie dialogowym Łączenie** z projektem wybierz repopo, z którym chcesz nawiązać połączenie, a następnie wybierz pozycję **Klonuj**.

      ![Zrzut ekranu przedstawiający okno dialogowe "Łączenie z projektem" wygenerowane na podstawie Visual Studio 2019 w wersji 16.7 lub starszej](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > To, co zostanie wyświetlona w polu listy, zależy Azure DevOps repozytoriów, do których masz dostęp.

   Visual Studio zostanie **Team Explorer,** a po zakończeniu klonowania zostanie wyświetlone powiadomienie.

     ![Zrzut ekranu przedstawiający okno Team Explorer w programie Visual Studio 2019 w wersji 16.7 i starszych po zakończeniu klonowania](./media/vs-2019/clone-complete-azure-devops.png)

1. Aby wyświetlić foldery i pliki, wybierz **link Pokaż widok** folderu.

     ![Zrzut ekranu przedstawiający sekcję Rozwiązania okna Team Explorer w programie Visual Studio 2019 w wersji 16.7 i starszych, po zakończeniu klonowania](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio zostanie otwarty **Eksplorator rozwiązań**.

1. Wybierz link **Rozwiązania i foldery,** aby wyszukać plik rozwiązania (w szczególności plik sln), który ma być otwarty.

      ![Zrzut ekranu przedstawiający powiadomienie "Rozwiązania i foldery" z Team Explorer wersji 2019 16.7 lub starszej Visual Studio 2019](./media/open-proj-repo-solutions-folders.png)

   Jeśli w swoim repocie nie masz pliku rozwiązania, zostanie wyświetlony komunikat "Nie znaleziono rozwiązań". Można jednak kliknąć dwukrotnie dowolny plik z menu folderu, aby otworzyć go w Visual Studio kodu.

---

## <a name="next-steps"></a>Następne kroki

Jeśli wszystko jest gotowe do programowania za pomocą Visual Studio, poznaj dowolny z następujących samouczków specyficznych dla języka:

- [Visual Studio samouczków | **C#**](./csharp/index.yml)
- [Visual Studio samouczków | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio samouczków | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio samouczków | **Język Python**](../python/index.yml)
- [Visual Studio samouczków | **JavaScript,** **TypeScript** i **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Zobacz też

- [Otwieranie projektu z repo w Visual Studio 2017 r.](tutorial-open-project-from-repo-visual-studio-2017.md)
- [Nowe środowisko usługi Git w Visual Studio 2019 r.](../ide/git-with-visual-studio.md)
- [Porównanie usługi Git i Team Explorer obok siebie](../ide/git-team-explorer-feature-comparison.md)
- [Azure DevOps Services: Wprowadzenie do Azure Repos i Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Wprowadzenie do Azure DevOps](/learn/modules/get-started-with-devops/)
