---
title: Team Foundation Version Control (TFVC)
description: Nawiązywanie połączenia z programu Visual Studio dla komputerów Mac w Team Foundation Server/DevOps platformy Azure za pomocą Team Foundation Version Control (TFVC).
author: conceptdev
ms.author: crdun
ms.date: 04/04/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: d98ffc8c9d864afaf0b42d029a4d65850f64d806
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59366162"
---
# <a name="connecting-to-team-foundation-version-control"></a>Nawiązywanie połączenia z Team Foundation Version Control

> [!NOTE]
> Aby uzyskać najlepsze wyniki kontroli wersji w systemie macOS zaleca się przy użyciu narzędzia Git zamiast Team Foundation Version Control (TFVC). Git jest obsługiwana w programie Visual Studio dla komputerów Mac i jest to opcja domyślna, w przypadku repozytoriów hostowanych w Team Foundation Server (TFS) / DevOps platformy Azure. Aby dowiedzieć się więcej o korzystaniu z usługi Git przy użyciu infrastruktury DevOps programu TFS/Azure, zobacz [Konfigurowanie repozytorium Git](/visualstudio/mac/set-up-git-repository) artykułu.

Repozytoriów platformy Azure oferuje dwa modele kontroli wersji: [Git](/azure/devops/repos/git/?view=azure-devops), rozproszony system kontroli wersji, a [Team Foundation Version Control](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC), wersjami w sposób scentralizowany system kontroli.

Program Visual Studio for Mac zapewnia pełną obsługę dla repozytoriów Git, ale wymaga obejścia do pracy z użyciem systemu TFVC. Jeśli obecnie używasz TFVC do kontroli wersji, poniżej przedstawiono niektóre rozwiązania, które umożliwia dostęp do kodu źródłowego hostowanych w TFVC.

* [Przy użyciu programu Visual Studio Code i rozszerzenia repozytoriów platformy Azure, graficznego interfejsu użytkownika](#use-visual-studio-code-and-the-azure-repos-extension)
* [Nawiązać połączenie z repozytorium, korzystając z Team Explorer Everywhere wiersza polecenia klienta (TEE CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Nawiązać połączenie z TFVC przy użyciu rozszerzenia Team Foundation Version Control (nieobsługiwane) dla programu Visual Studio dla komputerów Mac](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

W pozostałej części tego artykułu przeprowadzi Cię przez opcje wymienionych powyżej.

## <a name="requirements"></a>Wymagania

* Visual Studio Community, Professional lub Enterprise dla komputerów Mac w wersji 7,8 lub nowszej.
* Usługom DevOps platformy Azure, Team Foundation Server 2013 i nowsze, lub na platformie Azure DevOps Server 2018 r. lub później.
* Projekt w usługom DevOps platformy Azure lub Team Foundation Server/Azure DevOps Server skonfigurowany do używania kontroli wersji serwera Team Foundation.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Przy użyciu programu Visual Studio Code i rozszerzenia repozytoriów platformy Azure

Jeśli wolisz pracować z interfejsem graficznym do zarządzania plikami w kontroli wersji, następnie rozszerzenie repozytoriów platformy Azure dla programu Visual Studio Code oferuje wspierane rozwiązanie firmy Microsoft. Aby rozpocząć pracę, Pobierz [programu Visual Studio Code](https://code.visualstudio.com) i Dowiedz się, jak [skonfiguruj rozszerzenie Azure repozytoriów](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Łączenie za pomocą Team Explorer Everywhere klienta wiersza polecenia

Jeśli wiesz, przy użyciu systemu macOS Terminal, a następnie z Team Explorer Everywhere klienta wiersza polecenia (TEE CLC) umożliwia obsługiwanych nawiązywania połączenia ze źródłem w TFVC.

Można wykonaj poniższe kroki, aby skonfigurować połączenie TFVC oraz zatwierdzić zmiany.

Specjalne dzięki Chris Pilcher, Deweloper w naszej społeczności, którego [oryginalnego instrukcje dotyczące TEE CLC](https://gist.github.com/chris-pilcher/a3f14eb081d7ab983e5c) podstawą w tej sekcji.

### <a name="setting-up-the-tee-clc"></a>Konfigurowanie TEE CLC

Istnieją dwa sposoby pobrania konfiguracji TEE CLC.

* Użyj Homebrew, aby zainstalować klienta, lub
* Pobierz i zainstaluj ręcznie klienta

Najprostszym rozwiązaniem jest **przy użyciu programu HomeBrew**, czyli Menedżer pakietów dla systemu macOS. Aby zainstalować, za pomocą tej metody:

1. Uruchamianie aplikacji terminali z systemem macOS.
1. Zainstaluj Homebrew, za pomocą terminalu i instrukcje na [strony głównej Homebrew](https://brew.sh/).
1. Po zainstalowaniu Homebrew, uruchom następujące polecenie w terminalu: `brew install tee-clc`

Aby **ręcznie skonfigurować TEE CLC**:

1. [Pobierz najnowszą wersję tee clc](https://github.com/Microsoft/team-explorer-everywhere/releases) ze strony z wersjami programu Team Explorer Everywhere repozytorium GitHub (np. programu tee-clc-14.134.0.zip w momencie pisania tego dokumentu).
1. Wyodrębnij zawartość .zip do folderu na dysku.
1. Otwórz aplikację Terminal systemu macOS i użyj `cd` polecenie, aby przejść do folderu, który została użyta w poprzednim kroku.
1. Z wewnątrz folderu, uruchom polecenie `./tf` do przetestowania, czy można uruchomić klienta wiersza polecenia, może pojawić się prośba zainstalować język Java lub innych zależności.

Po zainstalowaniu TEE CLC polecenie można uruchomić `tf eula` do wyświetlania i zaakceptuj umowę licencyjną dla klienta.

Na koniec aby uwierzytelniać się przy użyciu środowiska DevOps programu TFS/platformy Azure, musisz utworzyć osobisty token dostępu na serwerze. Dowiedz się więcej o [uwierzytelniania za pomocą osobiste tokeny dostępu](https://docs.microsoft.com/azure/devops/integrate/get-started/authentication/pats?view=azure-devops). Podczas tworzenia osobistego tokenu dostępu do użycia z użyciem systemu TFVC, pamiętaj, że zapewnia pełny dostęp, podczas konfigurowania tokenu.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Za pomocą TEE CLC, aby nawiązać połączenie z repozytorium

Aby połączyć się z kodem źródłowym, należy najpierw utworzyć obszar roboczy za pomocą `tf workspace` polecenia. Na przykład poniższe polecenia Podłącz do organizacji w usłudze Azure DevOps Services o nazwie "MyOrganization": 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

`TF_AUTO_SAVE_CREDENTIALS` Ustawienie środowiska umożliwia zapisanie poświadczeń, więc zostanie wyświetlony monit o podanie ich wiele razy. Po wyświetleniu monitu o nazwę użytkownika, używać osobisty token dostępu utworzony w poprzedniej sekcji i pustego hasła.

Teraz, aby utworzyć mapowanie plików źródłowych do folderu lokalnego, użyjesz `tf workfold` polecenia. Poniższy przykład zmapuje folder o nazwie "WebApp.Services" z "MyRepository" TFVC projektu i ustawić go tak, aby być skopiowany do folderu lokalnego ~/Projects/ (czyli folder "Projekty" w folderze głównym bieżących użytkowników).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Na koniec użyj następującego polecenia, aby pobrać pliki źródłowe z serwera i skopiuj je lokalnie:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>Zatwierdzanie zmian za pomocą TEE CLC

Po wprowadzeniu zmian w plikach w programie Visual Studio dla komputerów Mac, przejście wracamy do terminalu, aby zaewidencjonować zmian. `tf add` Polecenie służy do dodawania plików do listy oczekujących zmian zaewidencjonowanych i `tf checkin` polecenie wykonuje rzeczywiste zaewidencjonowania do serwera. `checkin` Polecenie zawiera parametry, aby dodać komentarz lub skojarz powiązany element roboczy. W poniższym fragmencie kodu, wszystkie pliki w `WebApp.Services` folderu są dodawane, cyklicznie, do zaewidencjonowania. Następnie kod jest ewidencjonowane przy użyciu komentarz i skojarzony element roboczy o identyfikatorze "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Aby dowiedzieć się więcej na temat polecenia wymienione w tym miejscu lub inne osoby, służy następujące polecenie z poziomu terminalu:

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Nawiązać połączenie z TFVC przy użyciu rozszerzenia Team Foundation Version Control

> [!NOTE]
> Aby uzyskać najlepsze wyniki kontroli wersji w systemie macOS zaleca się przy użyciu narzędzia Git zamiast Team Foundation Version Control (TFVC). Git jest obsługiwana w programie Visual Studio dla komputerów Mac i jest to opcja domyślna, w przypadku repozytoriów hostowanych w Team Foundation Server (TFS) / DevOps platformy Azure. Aby dowiedzieć się więcej o korzystaniu z usługi Git przy użyciu infrastruktury DevOps programu TFS/Azure, zobacz [Konfigurowanie repozytorium Git](/visualstudio/mac/set-up-git-repository) artykułu.

W programie Visual Studio dla komputerów Mac rozszerzenia galerii ma rozszerzenie kontroli wersji Team Foundation, które udostępnia ograniczoną obsługę nawiązać połączenia z programem TFVC. Rozszerzenie nie jest obsługiwana i ma kilka znanych problemów, dzięki czemu Twoje doświadczenia mogą się różnić w przypadku korzystania z niego.

Aby zainstalować rozszerzenie, uruchom program Visual Studio dla komputerów Mac, a następnie wybierz **programu Visual Studio > rozszerzenia** menu. W **galerii** zaznacz **kontroli wersji > kontroli wersji Team Foundation dla TFS i usługi Azure DevOps** i kliknij przycisk **instalacji...** :

![Menedżer rozszerzeń](media/tfvc-install.png)

Postępuj zgodnie z monitami, aby zainstalować rozszerzenie. Po zainstalowaniu, należy ponownie uruchomić środowisko IDE.

### <a name="updating-the-extension"></a>Trwa aktualizowanie rozszerzenia

Okresowo są wprowadzone aktualizacje z rozszerzeniem TFVC. Dostęp do aktualizacji, wybierz **programu Visual Studio > rozszerzenia...**  z menu i wybierzesz **aktualizacje** kartę. Zaznacz rozszerzenie na liście i naciśnij klawisz **aktualizacji** przycisku:

Naciśnij klawisz **zainstalować** w następnym oknie dialogowym odinstalowanie starego pakietu i instalacja nowego.

### <a name="using-the-extension"></a>Przy użyciu rozszerzenia

Po zainstalowaniu rozszerzenia wybierz **kontroli wersji > DevOps programu TFS/platformy Azure > Otwórz ze zdalnego repozytorium...**  elementu menu.

![Element menu, aby otworzyć rozszerzenia](media/tfvc-source-control-explorer-devops.png)

Wybierz usługi VSTS lub serwera Team Foundation Server, aby rozpocząć pracę, a następnie naciśnij klawisz **Kontynuuj**:

![Łączenie z serwerem](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Uwierzytelnianie repozytoriów platformy Azure

Po wybraniu projektu, który znajduje się na repozytoriów platformy Azure, monit o podanie szczegółów konta Microsoft:

![Połącz się z repozytoriów platformy Azure](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>Uwierzytelnianie serwera TFS

Aby połączyć z TFS, wprowadź szczegóły serwera i poświadczenia konta. Wprowadź domenę do użycia uwierzytelniania NTLM, w przeciwnym razie pozostaw puste, aby użyć uwierzytelniania podstawowego. Wybierz **Dodaj serwer**:

![Zaloguj się do serwera TFS](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Wybieranie projektu

Po użytkownik został pomyślnie uwierzytelniony, można wyświetlić listę repozytoriów, które są skojarzone z kontem w **Otwórz z kontroli źródła** okno dialogowe:

![Otwórz z dialogowe kontroli źródła z projektami wyświetlane](media/tfvc-vsts-projects.png)

To okno dialogowe jest zorganizowana przy użyciu następujących węzłów:

- Usługa Azure DevOps organizacji lub kolekcji — zostaną wyświetlone wszystkie organizacje podłączone do konta Microsoft, którego zalogowano się przy użyciu.
- Projekty — w każdej organizacji lub kolekcji, może mieć wiele projektów. Projekt jest, gdzie hostowana kod źródłowy, elementy robocze i automatyczne kompilacje.

W tym momencie wyszukiwanie i filtrowanie według nazwy projektu lub organizacji.

#### <a name="adding-a-new-server"></a>Dodawanie nowego serwera

Aby dodać nowy serwer do listy, naciśnij klawisze **Dodaj hosta** znajdujący się na **Otwórz z kontroli źródła** okno dialogowe:

![Wyróżnione Dodaj przycisk, aby dodać nowy serwer do listy](media/tfvc-add-new-server.png)

Wybierz dostawcę z listy, a następnie wprowadź swoje poświadczenia:

![Okno dialogowe z wyświetloną opcją dostawcy kontroli źródła](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Tworzenie nowego obszaru roboczego

Aby rozpocząć pracę z projektem, musisz mieć _obszaru roboczego_. Jeśli nie masz jeszcze obszaru roboczego, możesz utworzyć je z **obszaru roboczego** combobox **Otwórz z kontroli źródła** okno dialogowe:

![Utwórz nową opcję combobox obszaru roboczego](media/tfvc-create-new-workspace.png)

Ustaw nazwę i ścieżkę lokalną dla nowego obszaru roboczego i wybierz **Utwórz obszar roboczy**:

![Wprowadź nazwę i ścieżkę lokalną dla nowego obszaru roboczego](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Za pomocą Eksploratora kodu źródłowego

Po utworzeniu obszaru roboczego i mapowany do projektu, możesz rozpocząć pracę z _Eksploratora kodu źródłowego_.

Aby otworzyć Eksploratora kodu źródłowego, zaznacz **kontroli wersji > DevOps programu TFS/platformy Azure > Eksploratorze kontroli źródła** elementu menu.

Eksplorator kodu źródłowego umożliwia nawigowanie po wszystkich zamapowanych projektów, pliki i foldery. W tym obszarze można również wykonywać wszystkie akcje kontroli podstawowego źródła takie jak:

- Pobierz najnowszą wersję
- Pobieranie określonej wersji
- Ewidencjonowanie i wyewidencjonowywanie plików
- Blokowanie i odblokowywanie plików
- Dodawanie, usuwanie i Zmień nazwy plików
- Wyświetlić historię
- Porównaj zmiany.

Wiele z tych działań są dostępne za pośrednictwem kontekst akcji dla projektu:

![Akcje menu kontekstowe dla projektu](media/tfvc-sourcecode-actions.png)

### <a name="managing-workspaces"></a>Zarządzanie obszarami roboczymi

Jeśli nie utworzono jeszcze obszaru roboczego, zgodnie z opisem w [tworzenia obszaru roboczego](#creating-a-new-workspace) sekcji, można zauważyć, że Eksplorator kodu źródłowego jest puste:

![Źródło pusty Eksplorator kodu](media/tfvc-setup-empty-sce.png)

Aby skonfigurować zdalne projektu za pomocą lokalnego obszaru roboczego, użyj następujących kroków:

1. Wybierz **serwera** z pola kombi.
1. Należy pamiętać, że nie ma "żadnych obszarów roboczych" i że ścieżka lokalna jest "Niezamapowany". Wybierz **niezamapowane** łącze, aby wyświetlić **Utwórz nowy obszar roboczy** okna dialogowego.
1. Podaj nazwę obszaru roboczego, a następnie kliknij przycisk **Dodaj Folder pracy** do mapowania projektu do folderu lokalnego na komputerze:

    ![Utwórz nowe okno dialogowe obszaru roboczego przedstawiający opcje domyślne](media/tfvc-workspace1.png)

1. Wybierz folder "$", aby mapować wszystkie projekty na serwerze do tego samego obszaru roboczego, lub wybierz pojedynczego projektu, a następnie kliknij przycisk **OK**:

    ![Przeglądaj w poszukiwaniu folderu okno dialogowe wyświetloną wszystkie projekty](media/tfvc-workspace2.png)

1. Wybierz lokalizację na lokalnym komputerze, którą chcesz zamapować te projekty do, a następnie kliknij przycisk **wybierz Folder**.
1. Potwierdź szczegóły nowego obszaru roboczego, naciskając klawisz **OK**

    ![Tworzenie okna dialogowego Nowy obszar roboczy za pomocą folderu roboczego dodano](media/tfvc-workspace3.png)

Po skonfigurowaniu obszaru roboczego może można zmienić ani usunąć, klikając **zarządzanie obszarami roboczymi** przycisku w Eksploratorze kodu źródłowego.

![Zarządzanie obszarami roboczymi](media/tfvc-workspace4.png)

## <a name="troubleshooting-and-known-issues"></a>Rozwiązywanie problemów i znane problemy

#### <a name="problems-using-basic-authentication"></a>Problemów przy użyciu uwierzytelniania podstawowego

Następujące opcje może służyć do uwierzytelniania z serwerem:

- OAuth
- Podstawowy
- Ntlm

Do korzystania z uwierzytelniania podstawowego jest niezbędne do włączenia **uwierzytelniania alternatywnych poświadczeń** w usługom DevOps platformy Azure, wykonując poniższe kroki:

1. Zaloguj się do Twojej organizacji DevOps platformy Azure jako właściciel (https://dev.azure.com/{organization}/{project}).

2. Z organizacji paska narzędzi, wybierz ikonę koła zębatego, a następnie wybierz pozycję **zasad**:

    ![Wybrana opcja ustawień zasad](media/tfvc-auth2.png)

3. Sprawdź ustawienia połączenia aplikacji. Zmień te ustawienia, w oparciu o zasady zabezpieczeń:

    ![Wybrana opcja ustawień zasad](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>Nie znajdziesz już niczego w TFVC

Aby ustawić się kontroli wersji Team Foundation (TFVC) na komputerze deweloperskim, możesz **musi** Utwórz obszar roboczy, zgodnie z opisem w [zarządzanie obszarami roboczymi](#managing-workspaces) sekcji.

W Eksploratorze kontroli źródła, naciśnij klawisz **zarządzanie obszarami roboczymi** przycisku. Wykonaj kroki do mapowania projektu do folderu na komputerze deweloperskim.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>Nie widzę żadnych / all moich projektów

Po uwierzytelnieniu powinien zostać wyświetlony listy projektów. Domyślnie są wyświetlane tylko w projektach programu TFS. Aby wyświetlić innych typów projektów, zaznacz pole "Zobacz wszystkich projektów".

Należy pamiętać, że projekty, które znajdują się na serwerze nie będą widoczne, jeśli nie masz poprawne uprawnienia.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Pojawia się błąd "nie można utworzyć obszaru roboczego. Spróbuj ponownie"

Podczas próby [Utwórz nowy obszar roboczy](#creating-a-new-workspace), należy się upewnić, są spełnione następujące warunki:

- Zakaz używania nieprawidłowe znaki w nazwie obszaru roboczego.
- Nazwa musi być krótsza niż 64 znaki.
- Nie można użyć ścieżki lokalnej przez innych obszarów roboczych.

### <a name="see-also"></a>Zobacz także

- [Tworzenie i udostępnianie kodu w TFVC przy użyciu programu Visual Studio (na Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)