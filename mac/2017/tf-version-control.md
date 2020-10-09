---
title: Kontrola wersji serwera Team Foundation (TFVC)
description: Nawiązywanie połączenia z Visual Studio dla komputerów Mac Team Foundation Server/Azure DevOps z usługą Kontrola wersji serwera Team Foundation (TFVC).
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: d2ba7f5d044b82c44d719b251a7d803212cf7b07
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91860564"
---
# <a name="connecting-to-team-foundation-version-control"></a>Nawiązywanie połączenia z Kontrola wersji serwera Team Foundation

> [!NOTE]
> Aby zapewnić najlepszą kontrolę wersji w systemie macOS, zalecamy korzystanie z narzędzia Git zamiast Kontrola wersji serwera Team Foundation (TFVC). Narzędzie git jest obsługiwane w Visual Studio dla komputerów Mac i jest opcją domyślną dla repozytoriów hostowanych w Team Foundation Server (TFS)/Azure DevOps. Aby dowiedzieć się więcej o korzystaniu z narzędzia Git z programem TFS/Azure DevOps, zobacz artykuł [Konfigurowanie repozytorium git](./set-up-git-repository.md) .
>
> Jeśli wcześniej była używana wersja zapoznawcza rozszerzenia TFVC dla Visual Studio dla komputerów Mac, nie jest już obsługiwana w przypadku uaktualniania do programu Visual Studio 2019 for Mac.

Azure Repos oferuje dwa modele kontroli wersji: [git](/azure/devops/repos/git/?view=azure-devops), rozproszony system kontroli wersji i [Kontrola wersji serwera Team Foundation](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC), scentralizowany system kontroli wersji.

Visual Studio dla komputerów Mac zapewnia pełną obsługę repozytoriów Git, ale wymaga zastosowania niektórych rozwiązań do pracy z usługą TFVC. Jeśli obecnie używasz usługi TFVC na potrzeby kontroli wersji, Oto kilka rozwiązań, których można użyć w celu uzyskania dostępu do kodu źródłowego hostowanego w TFVC:

* [Użyj Visual Studio Code i rozszerzenia Azure Repos, dla graficznego interfejsu użytkownika](#use-visual-studio-code-and-the-azure-repos-extension)
* [Nawiązywanie połączenia z repozytorium przy użyciu Team Explorer Everywhere wiersza polecenia klienta (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Połącz się z usługą TFVC przy użyciu rozszerzenia (nieobsługiwane) Kontrola wersji serwera Team Foundation dla Visual Studio dla komputerów Mac](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

Pozostała część tego artykułu przeprowadzi Cię przez wymienione powyżej opcje.

## <a name="requirements"></a>Wymagania

* Visual Studio Community, Professional lub Enterprise dla komputerów Mac w wersji 7,8 lub nowszej.
* Azure DevOps Services, Team Foundation Server 2013 i nowsze, lub Azure DevOps Server 2018 i nowsze.
* Projekt w Azure DevOps Services lub Team Foundation Server/Azure DevOps Server skonfigurowany do korzystania z Kontrola wersji serwera Team Foundation.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Użyj Visual Studio Code i rozszerzenia Azure Repos

Jeśli chcesz współpracować z interfejsem graficznym w celu zarządzania plikami w kontroli wersji, rozszerzenie Azure Repos dla Visual Studio Code udostępnia rozwiązanie obsługiwane przez firmę Microsoft. Aby rozpocząć, Pobierz [Visual Studio Code](https://code.visualstudio.com) a następnie Dowiedz się, jak [skonfigurować rozszerzenie Azure Repos](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Nawiązywanie połączenia przy użyciu Team Explorer Everywhere klienta wiersza polecenia

Jeśli nie masz doświadczenia w korzystaniu z terminalu macOS, klient wiersza polecenia Team Explorer Everywhere (TEE-CLC) zapewnia obsługiwany sposób nawiązywania połączenia ze źródłem w programie TFVC.

Możesz wykonać poniższe kroki, aby skonfigurować połączenie do TFVC i zatwierdzić zmiany.

### <a name="setting-up-the-tee-clc"></a>Konfigurowanie TEE-CLC

Istnieją dwa sposoby uzyskania Instalatora za pomocą TEE-CLC.

* Użyj oprogramowania homebrew, aby zainstalować klienta programu lub
* Pobierz i ręcznie zainstaluj klienta

Najprostszym rozwiązaniem jest **Korzystanie**z programu oprogramowania homebrew, który jest menedżerem pakietów dla macOS. Aby zainstalować za pomocą tej metody:

1. Uruchom aplikację terminala macOS.
1. Zainstaluj program oprogramowania Homebrew przy użyciu terminalu i instrukcje na [stronie głównej oprogramowania Homebrew](https://brew.sh/).
1. Po zainstalowaniu oprogramowania Homebrew Uruchom następujące polecenie z terminalu: `brew install tee-clc`

Aby **ręcznie skonfigurować tee-CLC**:

1. [Pobierz najnowszą wersję tee-CLC](https://github.com/Microsoft/team-explorer-everywhere/releases) ze strony wydań w repozytorium GitHub Team Explorer Everywhere (np. tee-clc-14.134.0.zip w momencie tego zapisu).
1. Wyodrębnij zawartość pliku zip do folderu na dysku.
1. Otwórz aplikację terminala macOS i Użyj `cd` polecenia, aby przełączyć się do folderu, który został użyty w poprzednim kroku.
1. Z poziomu folderu Uruchom polecenie, `./tf` Aby sprawdzić, czy można uruchomić klienta wiersza polecenia. może zostać wyświetlony monit o zainstalowanie języka Java lub innych zależności.

Po zainstalowaniu TEE-CLC można uruchomić polecenie, `tf eula` Aby wyświetlić i zaakceptować umowę licencyjną dla klienta.

Na koniec, aby uwierzytelnić się w środowisku DevOps TFS/Azure, musisz utworzyć osobisty token dostępu na serwerze. Dowiedz się więcej o [uwierzytelnianiu z osobistymi tokenami dostępu](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops). Podczas tworzenia osobistego tokenu dostępu do używania z usługą TFVC należy zapewnić pełen dostęp podczas konfigurowania tokenu.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Nawiązywanie połączenia z repozytorium przy użyciu TEE-CLC

Aby nawiązać połączenie z kodem źródłowym, musisz najpierw utworzyć obszar roboczy przy użyciu `tf workspace` polecenia. Na przykład następujące polecenia nawiązują połączenie z organizacją w Azure DevOps Services o nazwie "Moja organizacja": 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

`TF_AUTO_SAVE_CREDENTIALS`Ustawienie środowisko służy do zapisywania poświadczeń, dlatego nie zostanie wyświetlony monit o wprowadzenie ich wiele razy. Po wyświetleniu monitu o podanie nazwy użytkownika Użyj osobistego tokenu dostępu utworzonego w poprzedniej sekcji i użyj pustego hasła.

Aby utworzyć mapowanie plików źródłowych do folderu lokalnego, użyj `tf workfold` polecenia. Poniższy przykład mapuje folder o nazwie "WebApp. Services" z projektu TFVC "moje repozytorium" i skonfiguruje go do kopiowania do lokalnego folderu ~/Projects/(tj. folder "projects" w folderze głównym bieżącego użytkownika).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Na koniec użyj następującego polecenia, aby pobrać pliki źródłowe z serwera i skopiować je lokalnie:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>Zatwierdzanie zmian przy użyciu TEE-CLC

Po wprowadzeniu zmian w plikach w Visual Studio dla komputerów Mac można wrócić do terminalu, aby zaewidencjonować zmiany. `tf add`Polecenie służy do dodawania plików do listy oczekujących zmian do zaewidencjonowania, a `tf checkin` polecenie wykonuje rzeczywiste ewidencjonowanie na serwerze. `checkin`Polecenie zawiera parametry służące do dodawania komentarza lub kojarzenia powiązanego elementu pracy. W poniższym fragmencie kodu wszystkie pliki w `WebApp.Services` folderze są dodawane cyklicznie do zaewidencjonowania. Następnie kod jest sprawdzany z komentarzem i skojarzony z elementem roboczym o IDENTYFIKATORze "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Aby dowiedzieć się więcej na temat poleceń wymienionych tutaj lub innych, można użyć następującego polecenia z terminalu:

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Nawiązywanie połączenia z usługą TFVC przy użyciu rozszerzenia Kontrola wersji serwera Team Foundation

> [!NOTE]
> Aby zapewnić najlepszą kontrolę wersji w systemie macOS, zalecamy korzystanie z narzędzia Git zamiast Kontrola wersji serwera Team Foundation (TFVC). Narzędzie git jest obsługiwane w Visual Studio dla komputerów Mac i jest opcją domyślną dla repozytoriów hostowanych w Team Foundation Server (TFS)/Azure DevOps. Aby dowiedzieć się więcej o korzystaniu z narzędzia Git z programem TFS/Azure DevOps, zobacz artykuł [Konfigurowanie repozytorium git](./set-up-git-repository.md) .
>
> Jeśli wcześniej była używana wersja zapoznawcza rozszerzenia TFVC dla Visual Studio dla komputerów Mac, nie jest już obsługiwana w przypadku uaktualniania do programu Visual Studio 2019 for Mac.

W galerii rozszerzeń Visual Studio dla komputerów Mac istnieje rozszerzenie kontroli wersji programu Team Foundation, które oferuje ograniczoną obsługę połączenia z usługą TFVC. Rozszerzenie nie jest obsługiwane i zawiera kilka znanych problemów, dlatego środowisko może się różnić w przypadku korzystania z niego.

Aby zainstalować rozszerzenie, uruchom Visual Studio dla komputerów Mac i wybierz menu **rozszerzenia Visual Studio >** . Na karcie **Galeria** wybierz pozycję **kontrola wersji > Kontrola wersji serwera Team Foundation dla TFS i Azure DevOps** , a następnie kliknij przycisk **Zainstaluj...**:

![Menedżer rozszerzeń](media/tfvc-install.png)

Postępuj zgodnie z monitami, aby zainstalować rozszerzenie. Po zainstalowaniu programu ponownie uruchom środowisko IDE.

### <a name="updating-the-extension"></a>Aktualizowanie rozszerzenia

Aktualizacje rozszerzenia TFVC są wykonywane okresowo. Aby uzyskać dostęp do aktualizacji, wybierz **> rozszerzenia programu Visual Studio...** z menu, a następnie wybierz kartę **aktualizacje** . Wybierz rozszerzenie na liście i naciśnij przycisk **Aktualizuj** :

Naciśnij przycisk **Instaluj** w następnym oknie dialogowym, aby odinstalować stary pakiet i zainstalować nowy.

### <a name="using-the-extension"></a>Przy użyciu rozszerzenia

Po zainstalowaniu rozszerzenia wybierz **kontrolę wersji > TFS/Azure DevOps > Otwórz z repozytorium zdalnego...** .

![Element menu, aby otworzyć rozszerzenie](media/tfvc-source-control-explorer-devops.png)

Wybierz opcję VSTS lub Team Foundation Server, aby rozpocząć pracę, i naciśnij przycisk **Kontynuuj**:

![Nawiązywanie połączenia z serwerem](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Uwierzytelnianie Azure Repos

Po wybraniu projektu hostowanego na Azure Repos zostanie wyświetlony monit o wprowadzenie szczegółów konto Microsoft:

![Połącz z Azure Repos](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>Uwierzytelnianie TFS

Aby nawiązać połączenie z programem TFS, wprowadź szczegóły serwera i poświadczenia konta. Wprowadź domenę, aby korzystać z uwierzytelniania NTLM, w przeciwnym razie pozostaw puste, aby użyć uwierzytelniania podstawowego. Wybierz pozycję **Dodaj serwer**:

![Zaloguj się do serwera TFS](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Wybieranie projektu

Po pomyślnym uwierzytelnieniu można zobaczyć listę repozytoriów skojarzonych z kontem w oknie dialogowym **Otwórz z kontroli źródła** :

![Otwórz z okna dialogowego kontroli źródła z wyświetlanymi projektami](media/tfvc-vsts-projects.png)

To okno dialogowe jest zorganizowane z następującymi węzłami:

- Azure DevOps — organizacja lub kolekcja — wyświetla wszystkie organizacje połączone z konto Microsoft, które zostały zalogowane.
- Projekty — w każdej organizacji lub kolekcji można mieć wiele projektów. Projekt jest miejscem, w którym są hostowane kod źródłowy, elementy robocze i kompilacje automatyczne.

W tym momencie można wyszukiwać i filtrować według nazwy projektu lub organizacji.

#### <a name="adding-a-new-server"></a>Dodawanie nowego serwera

Aby dodać nowy serwer do listy, naciśnij przycisk **Dodaj hosta** w oknie dialogowym **Otwórz z kontroli źródła** :

![Wyróżniono przycisk Dodaj, aby dodać nowy serwer do listy](media/tfvc-add-new-server.png)

Wybierz dostawcę z listy, a następnie wprowadź swoje poświadczenia:

![Okno dialogowe pokazujące opcję dla dostawcy kontroli źródła](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Tworzenie nowego obszaru roboczego

Aby rozpocząć pracę z projektem, musisz mieć _obszar roboczy_. Jeśli nie masz jeszcze obszaru roboczego, możesz utworzyć go z poziomu pola kombi **obszaru roboczego** w oknie dialogowym **Otwórz z kontroli źródła** :

![Utwórz nowy obszar roboczy — opcja ComboBox](media/tfvc-create-new-workspace.png)

Ustaw nazwę i ścieżkę lokalną dla nowego obszaru roboczego i wybierz pozycję **Utwórz obszar roboczy**:

![Wprowadzanie nazwy i ścieżki lokalnej dla nowego obszaru roboczego](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Korzystanie z Eksploratora kodu źródłowego

Po utworzeniu obszaru roboczego i zmapowaniu projektu możesz rozpocząć pracę z _Eksploratorem kodu źródłowego_.

Aby otworzyć Eksploratora kodu źródłowego, zaznacz element menu **Kontrola wersji > TFS/Azure DevOps > Eksploator kontroli źródła** .

Eksplorator kodu źródłowego umożliwia nawigowanie przez wszystkie zmapowane projekty, ich pliki i foldery. Umożliwia również wykonywanie wszystkich podstawowych akcji kontroli źródła, takich jak:

- Pobierz najnowszą wersję
- Pobierz określoną wersję
- Ewidencjonowanie i wyewidencjonowywanie plików
- Zablokuj i Odblokuj pliki
- Dodawanie, usuwanie i zmiana nazw plików
- Wyświetlanie historii
- Porównaj zmiany.

Wiele z tych akcji jest dostępnych za pomocą akcji kontekstu w projekcie:

![Akcje menu kontekstowego dla projektu](media/tfvc-sourcecode-actions.png)

### <a name="managing-workspaces"></a>Zarządzanie obszarami roboczymi

Jeśli obszar roboczy nie został jeszcze utworzony, zgodnie z opisem w sekcji [Tworzenie obszaru roboczego](#creating-a-new-workspace) można zauważyć, że Eksplorator kodu źródłowego jest pusty:

![pusty Eksplorator kodu źródłowego](media/tfvc-setup-empty-sce.png)

Aby skonfigurować zdalny projekt przy użyciu lokalnego obszaru roboczego, wykonaj następujące czynności:

1. Wybierz **serwer** z ComboBox.
1. Należy zauważyć, że nie ma żadnych obszarów roboczych, a ścieżka lokalna nie jest zamapowana. Wybierz łącze **niezamapowane** , aby wyświetlić okno dialogowe **Tworzenie nowego obszaru roboczego** .
1. Podaj nazwę obszaru roboczego, a następnie kliknij pozycję **Dodaj folder roboczy** , aby zmapować projekt do folderu lokalnego na komputerze:

    ![Utwórz nowe okno dialogowe obszaru roboczego z opcjami domyślnymi](media/tfvc-workspace1.png)

1. Wybierz folder "$", aby zmapować wszystkie projekty na serwerze do tego samego obszaru roboczego, lub Wybierz pojedynczy projekt, a następnie kliknij przycisk **OK**:

    ![Okno dialogowe Przeglądanie w poszukiwaniu folderu, w którym są wyświetlane wszystkie projekty](media/tfvc-workspace2.png)

1. Wybierz lokalizację na komputerze lokalnym, do której mają zostać zamapowane projekty, a następnie kliknij pozycję **Wybierz folder**.
1. Potwierdź szczegóły nowego obszaru roboczego, naciskając **przycisk OK** .

    ![Okno dialogowe Tworzenie nowego obszaru roboczego z dodanym folderem roboczym](media/tfvc-workspace3.png)

Po skonfigurowaniu obszaru roboczego można go zmienić lub usunąć, klikając przycisk **Zarządzaj obszarami roboczymi** w Eksploratorze kodu źródłowego.

![Zarządzanie obszarami roboczymi](media/tfvc-workspace4.png)

## <a name="troubleshooting-and-known-issues"></a>Rozwiązywanie problemów i znane problemy

#### <a name="problems-using-basic-authentication"></a>Problemy z uwierzytelnianiem podstawowym

Do uwierzytelniania za pomocą serwera można użyć następujących opcji:

- Oauth
- Podstawowy
- NTLM

Aby korzystać z uwierzytelniania podstawowego, należy włączyć **alternatywne poświadczenia uwierzytelniania** w Azure DevOps Services, wykonując poniższe kroki:

1. Zaloguj się do swojej organizacji usługi Azure DevOps jako właściciel (https: \/ /dev.Azure.com/{Organization}/{Project}).

2. Na pasku narzędzi organizacji wybierz ikonę koła zębatego i wybierz pozycję **zasady**:

    ![Wybrana opcja ustawień zasad](media/tfvc-auth2.png)

3. Sprawdź ustawienia połączenia aplikacji. Zmień te ustawienia na podstawie zasad zabezpieczeń:

    ![Wybrana opcja ustawień zasad](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>Nie widzę niczego w TFVC

Aby skonfigurować Kontrola wersji serwera Team Foundation (TFVC) na komputerze deweloperskim, **należy** utworzyć obszar roboczy, zgodnie z opisem w sekcji [Zarządzanie obszarami roboczymi](#managing-workspaces) .

W Eksploator kontroli źródła naciśnij przycisk **Zarządzaj obszarami roboczymi** . Postępuj zgodnie z instrukcjami, aby zmapować projekt do folderu na komputerze deweloperskim.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>Nie widzę żadnych/wszystkich moich projektów

Po uwierzytelnieniu powinna zostać wyświetlona lista projektów. Domyślnie są wyświetlane tylko projekty TFS. Aby wyświetlić inne typy projektów, zaznacz pole wyboru "Zobacz wszystkie projekty".

Należy pamiętać, że projekty, które znajdują się na serwerze, nie będą wyświetlane, jeśli nie masz odpowiednich uprawnień.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Otrzymuję komunikat o błędzie "nie można utworzyć obszaru roboczego. Spróbuj ponownie.

Podczas próby [utworzenia nowego obszaru roboczego](#creating-a-new-workspace)należy upewnić się, że są spełnione następujące warunki:

- Brak użycia nieprawidłowych znaków w nazwie obszaru roboczego.
- Nazwa musi być krótsza niż 64 znaków.
- Ścieżka lokalna nie może być używana przez żadne inne obszary robocze.

### <a name="see-also"></a>Zobacz też

- [Opracowywanie i udostępnianie kodu w programie TFVC przy użyciu programu Visual Studio (w systemie Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)