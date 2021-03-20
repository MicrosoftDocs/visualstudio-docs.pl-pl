---
title: 'Samouczek: Otwieranie projektu z repozytorium w programie Visual Studio 2019'
description: Dowiedz się, jak otworzyć projekt w repozytorium Git lub Azure DevOps za pomocą programu Visual Studio 2019.
ms.custom: get-started
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
ms.openlocfilehash: 76dcd5061e2e12688f5119598071c3235e620967
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671716"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Samouczek: Otwieranie projektu z repozytorium

W tym samouczku użyjesz programu Visual Studio, aby połączyć się z repozytorium po raz pierwszy, a następnie otworzyć projekt.

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

## <a name="open-a-project-from-a-github-repo"></a>Otwieranie projektu z repozytorium GitHub

Sposób otwierania projektu z repozytorium GitHub przy użyciu programu Visual Studio 2019 zależy od posiadanej wersji. Jeśli zainstalowano wersję [**16,8**](/visualstudio/releases/2019/release-notes/) lub nowszą, [w programie Visual Studio](../ide/git-with-visual-studio.md) jest dostępne nowe, bardziej zintegrowane środowisko git.

Niezależnie od tego, która wersja została zainstalowana, można zawsze otworzyć projekt z repozytorium GitHub w programie Visual Studio.

#### <a name="168-and-later"></a>[16,8 i nowsze](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Klonowanie repozytorium GitHub i otwieranie projektu

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz pozycję **Klonuj repozytorium**.

   ![Zrzut ekranu okna dialogowego klonowanie repozytorium w programie Visual Studio 2019 w wersji 16,8 lub nowszej](../ide/media/vs-2019/clone-repository.png)

1. Wprowadź lub wpisz lokalizację repozytorium, a następnie wybierz pozycję **Klonuj**.

   ![Zrzut ekranu okna dialogowego klonowanie repozytorium, w którym wprowadzasz adres URL repozytorium Git w programie Visual Studio 2019 w wersji 16,8 lub nowszej](../ide/media/vs-2019/clone-repository-enter-location.png)

1. Może pojawić się prośba o podanie informacji logowania użytkownika w oknie dialogowym **Informacje o użytkowniku git** . Możesz dodać informacje lub edytować informacje domyślne, które zapewnia.

   ![Zrzut ekranu przedstawiający okno dialogowe informacji o użytkowniku git, w którym można wprowadzać lub edytować informacje o koncie w programie Visual Studio 2019 w wersji 16,8 lub nowszej](../ide/media/vs-2019/git-user-information-dialog.png)

    Wybierz pozycję **Zapisz** , aby dodać informacje do pliku Global. gitconfig. (Możesz też wybrać tę opcję później, wybierając pozycję **Anuluj**).

    > [!TIP]
    > Aby uzyskać więcej informacji na temat logowania do programu Visual Studio, zobacz stronę [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md) . Aby uzyskać szczegółowe informacje na temat korzystania z konta usługi GitHub w celu zalogowania się, zobacz temat [współpraca z kontami GitHub na stronie programu Visual Studio](../ide/work-with-github-accounts.md) .

    Następnie program Visual Studio automatycznie ładuje i otworzy rozwiązanie z repozytorium.

   ![Zrzut ekranu przedstawiający projekt w usłudze git, który jest otwarty w Eksplorator rozwiązań w programie Visual Studio 2019 w wersji 16,8 lub nowszej](../ide/media/vs-2019/git-solution-explorer.png )

1. Jeśli repozytorium zawiera wiele rozwiązań, zostaną one wyświetlone w Eksplorator rozwiązań. Listę rozwiązań można wyświetlić, wybierając przycisk **Przełącz widoki** w Eksplorator rozwiązań.

   ![Zrzut ekranu przedstawiający projekt w usłudze git, który jest otwarty w Eksplorator rozwiązań, z wyróżnionym przyciskiem przełączania widoków w programie Visual Studio 2019 w wersji 16,8 lub nowszej](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Eksplorator rozwiązań następnie oferuje opcję otwarcia folderu głównego w **widoku folderu** lub wybrania pliku rozwiązania do otwarcia.

   ![Zrzut ekranu przedstawiający plik. sln w narzędziu git, który jest otwarty w Eksplorator rozwiązań, po wybraniu przycisku Przełącz widoki w programie Visual Studio 2019 w wersji 16,8 lub nowszej](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Aby przełączać widok, ponownie wybierz przycisk **Przełącz widoki** .

    > [!TIP]
    > Możesz również użyć menu **git** w środowisku IDE programu Visual Studio, aby sklonować repozytorium i otworzyć projekt.
    >
    > ![Zrzut ekranu przedstawiający menu Git w programie Visual Studio 2019 w wersji 16,8 lub nowszej](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Otwieranie projektu lokalnie z wcześniej sklonowanego repozytorium GitHub

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz pozycję **Otwórz projekt lub rozwiązanie**.

    Program Visual Studio otwiera wystąpienie Eksploratora plików, w którym można przejść do rozwiązania lub projektu, a następnie wybrać go, aby go otworzyć.

   ![Zrzut ekranu przedstawiający okno "Otwieranie projektu lub rozwiązania" w programie Visual Studio 2019 w wersji 16,8 lub nowszej](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Jeśli ostatnio otwarto projekt lub rozwiązanie, wybierz je z sekcji **Otwórz ostatnio** , aby szybko ją otworzyć.

    > [!TIP]
    > Możesz również użyć menu **git** w środowisku IDE programu Visual Studio, aby otworzyć lokalne foldery i pliki z repozytorium, które zostało wcześniej sklonowane.
    >
    > ![Zrzut ekranu przedstawiający menu Git w programie Visual Studio 2019 w wersji 16,8 lub nowszej z rozwiniętą opcją lokalne repozytoria](../ide/media/vs-2019/git-menu-local-repositories.png)

    Rozpocznij kodowanie!

#### <a name="167-and-earlier"></a>[16,7 i starsze](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Klonowanie repozytorium GitHub i otwieranie projektu

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz opcję **klonowanie lub wyewidencjonowywanie kodu**.

   ![Zrzut ekranu przedstawiający okno "Tworzenie nowego projektu" w programie Visual Studio 2019 w wersji 16,7 i starszej](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Wprowadź lub wpisz lokalizację repozytorium, a następnie wybierz pozycję **Klonuj**.

   ![Zrzut ekranu przedstawiający okno "klonowanie lub Wyewidencjonuj kod" w programie Visual Studio 2019 w wersji 16,7 i starszej](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Program Visual Studio otwiera projekt z repozytorium.

1. Jeśli masz dostępny plik rozwiązania, zostanie on wyświetlony w menu "roztwory i foldery". Wybierz go, a program Visual Studio otwiera Twoje rozwiązanie.

   ![Zrzut ekranu przedstawiający listę rozwijaną Eksplorator rozwiązań w programie Visual Studio 2019 w wersji 16,7 i starszej](./media/open-proj-repo-github-solutions-folders-picker.png)

   Jeśli w repozytorium nie ma pliku rozwiązania (w oddzielnym pliku. sln), w menu rozwijanym zostanie wyświetlony komunikat "nie znaleziono żadnych rozwiązań". Można jednak kliknąć dwukrotnie dowolny plik z menu folder, aby otworzyć go w edytorze kodu programu Visual Studio.

    Rozpocznij kodowanie!

---

> [!NOTE]
> Aby uzyskać informacje specyficzne dla programu Visual Studio 2017, zobacz [Otwórz projekt z repozytorium na stronie Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md) .

## <a name="connect-to-an-azure-devops-server"></a>Nawiązywanie połączenia z serwerem usługi Azure DevOps

Co widzisz po nawiązaniu połączenia z serwerem usługi Azure DevOps za pomocą programu Visual Studio 2019 zależy od posiadanej wersji. Jeśli zainstalowano wersję [**16,8**](/visualstudio/releases/2019/release-notes/) lub nowszą, interfejs użytkownika został zmieniony tak, aby pomieścić nowe, w pełni zintegrowane [środowisko Git w](../ide/git-with-visual-studio.md) programie Visual Studio w programie Visual Studio.

Niezależnie od tego, która wersja została zainstalowana, zawsze możesz nawiązać połączenie z serwerem usługi Azure DevOps za pomocą programu Visual Studio.

#### <a name="168-and-later"></a>[16,8 i nowsze](#tab/vs168later)

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

#### <a name="167-and-earlier"></a>[16,7 i starsze](#tab/vs167earlier)

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz opcję **klonowanie lub wyewidencjonowywanie kodu**.

   ![Zrzut ekranu przedstawiający okno "Tworzenie nowego projektu" w programie Visual Studio 2019 w wersji 16,7 i starszej](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. W sekcji **Przeglądaj repozytorium** wybierz pozycję **Azure DevOps**.

   ![Zrzut ekranu przedstawiający okno "klonowanie lub wyewidencjonowywanie kodu" z sekcją "przeglądanie repozytorium" przedstawiającą usługę Azure DevOps w programie Visual Studio 2019 w wersji 16,7 i starszej](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Jeśli zobaczysz okno logowania, zaloguj się do swojego konta.

1. W oknie dialogowym **Połącz z projektem** wybierz repozytorium, z którym chcesz się połączyć, a następnie wybierz pozycję **Klonuj**.

      ![Zrzut ekranu przedstawiający okno dialogowe "łączenie z projektem", które zostało wygenerowane z programu Visual Studio 2019 w wersji 16,7 i starszej](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Elementy wyświetlane w polu listy zależą od repozytoriów usługi Azure DevOps, do których masz dostęp.

   Program Visual Studio otwiera **Team Explorer** i zostanie wyświetlone powiadomienie po zakończeniu klonowania.

     ![Zrzut ekranu okna Team Explorer w programie Visual Studio 2019 w wersji 16,7 i starszej po ukończeniu klonowania](./media/vs-2019/clone-complete-azure-devops.png)

1. Aby wyświetlić foldery i pliki, wybierz łącze **Pokaż widok folderu** .

     ![Zrzut ekranu przedstawiający sekcję Solutions okna Team Explorer w programie Visual Studio 2019 w wersji 16,7 i starszej po ukończeniu klonowania](./media/vs-2019/show-folder-view-azure-devops.png)

     Program Visual Studio otwiera **Eksplorator rozwiązań**.

1. Wybierz łącze **rozwiązania i foldery** , aby wyszukać plik rozwiązania (w odniesieniu do pliku. sln), aby go otworzyć.

      ![Zrzut ekranu przedstawiający powiadomienie "rozwiązania i foldery" z Team Explorer w programie Visual Studio 2019 w wersji 16,7 i starszej](./media/open-proj-repo-solutions-folders.png)

   Jeśli nie masz pliku rozwiązania w repozytorium, zostanie wyświetlony komunikat "nie znaleziono rozwiązań". Można jednak kliknąć dwukrotnie dowolny plik z menu folder, aby otworzyć go w edytorze kodu programu Visual Studio.

---

## <a name="next-steps"></a>Następne kroki

Jeśli wszystko jest gotowe do kodu w programie Visual Studio, szczegółowe do dowolnego z następujących samouczków dotyczących języka:

- [Samouczki programu Visual Studio | Język **C#**](./csharp/index.yml)
- [Samouczki programu Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Samouczki programu Visual Studio | Język **C++**](/cpp/get-started/tutorial-console-cpp)
- [Samouczki programu Visual Studio | Język **Python**](../python/index.yml)
- [Samouczki programu Visual Studio | **JavaScript**, **TypeScript** i **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Zobacz też

- [Otwieranie projektu z repozytorium w programie Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md)
- [Nowe środowisko Git w programie Visual Studio 2019](../ide/git-with-visual-studio.md)
- [Porównaj narzędzia Git i Team Explorer obok siebie](../ide/git-team-explorer-feature-comparison.md)
- [Azure DevOps Services: wprowadzenie do Azure Repos i programu Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Rozpoczynanie pracy z usługą Azure DevOps](/learn/modules/get-started-with-devops/)