---
title: Kontrola wersji Team Foundation (TFVC)
description: Łączenie się z programu Visual Studio dla komputerów Mac do team foundation server/azure devops z team foundation kontroli wersji (TFVC).
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: b7b160d58cead031a0eece2a522501d8c2060bd2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985199"
---
# <a name="connecting-to-team-foundation-version-control"></a>Łączenie się z kontrolą wersji programu Team Foundation

> [!NOTE]
> Aby uzyskać najlepsze środowisko kontroli wersji w systemie macOS, zalecamy użycie git zamiast Team Foundation Version Control (TFVC). Git jest obsługiwany w programie Visual Studio dla komputerów Mac i jest domyślną opcją dla repozytoriów hostowanych w programie Team Foundation Server (TFS)/Azure DevOps. Aby dowiedzieć się więcej na temat korzystania z git z TFS/Azure DevOps, zobacz [konfigurowanie repozytorium Git](/visualstudio/mac/set-up-git-repository) artykułu.
>
> Jeśli wcześniej używano wersji w wersji zapoznawczej rozszerzenia TFVC dla programu Visual Studio dla komputerów Mac, nie jest już obsługiwana podczas uaktualniania do programu Visual Studio 2019 dla komputerów Mac.

Usługa Azure Repos udostępnia dwa modele kontroli wersji: [Git](/azure/devops/repos/git/?view=azure-devops), rozproszony system kontroli wersji i [Team Foundation Version Control](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC), scentralizowany system kontroli wersji.

Visual Studio dla komputerów Mac zapewnia pełną obsługę repozytoriów Git, ale wymaga pewnych obejść do pracy z TFVC. Jeśli używasz TFVC do kontroli wersji dzisiaj, oto kilka rozwiązań, których można użyć, aby uzyskać dostęp do kodu źródłowego hostowanego w TFVC:

* [Używanie kodu programu Visual Studio i rozszerzenia repozytorium platformy Azure dla graficznego interfejsu użytkownika](#use-visual-studio-code-and-the-azure-repos-extension)
* [Łączenie się z repozytorium przy użyciu klienta wiersza polecenia Eksploratora wszędzie (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Łączenie się z tfvc przy użyciu (nieobsługiwał) Team Foundation Version Control rozszerzenie programu Visual Studio dla komputerów Mac](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

Dalsza część artykułu prowadzi cię przez opcje wymienione powyżej.

## <a name="requirements"></a>Wymagania

* Visual Studio Community, Professional lub Enterprise for Mac w wersji 7.8 lub nowszej.
* Usługi Azure DevOps, Team Foundation Server 2013 i nowsze lub Azure DevOps Server 2018 i nowsze.
* Projekt w usługach Azure DevOps services lub Team Foundation Server/Azure DevOps Server, skonfigurowany do używania kontroli wersji programu Team Foundation.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Używanie kodu programu Visual Studio i rozszerzenia repozytorium platformy Azure

Jeśli chcesz pracować z interfejsem graficznym do zarządzania plikami w kontroli wersji, rozszerzenie Repozytorium platformy Azure dla programu Visual Studio Code zapewnia obsługiwane rozwiązanie firmy Microsoft. Aby rozpocząć, pobierz [program Visual Studio Code,](https://code.visualstudio.com) a następnie dowiedz się, jak [skonfigurować rozszerzenie Repozytorium platformy Azure](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Łączenie się przy użyciu klienta wiersza polecenia Eksploratora zespołu wszędzie

Jeśli korzystasz z terminala macOS, klient wiersza polecenia Team Explorer Everywhere (TEE-CLC) zapewnia obsługiwany sposób łączenia się ze źródłem w TFVC.

Możesz wykonać poniższe czynności, aby skonfigurować połączenie z TFVC i zatwierdzić zmiany.

### <a name="setting-up-the-tee-clc"></a>Konfigurowanie tee-CLC

Tee-CLC można skonfigurować na dwa sposoby.

* Użyj Homebrew, aby zainstalować klienta, lub
* Pobieranie i ręczne instalowanie klienta

Najprostszym rozwiązaniem jest **użycie HomeBrew**, który jest menedżerem pakietów dla systemu macOS. Aby zainstalować przy użyciu tej metody:

1. Uruchom aplikację terminala macOS.
1. Zainstaluj Homebrew za pomocą terminala i instrukcji na [stronie głównej Homebrew](https://brew.sh/).
1. Po zainstalowaniu homebrew uruchom następujące polecenie z terminala:`brew install tee-clc`

Aby **ręcznie skonfigurować TEE-CLC:**

1. [Pobierz najnowszą wersję tee-clc](https://github.com/Microsoft/team-explorer-everywhere/releases) ze strony wydań repozytorium GitHub w eksploratorze Team Explorer Everywhere (np.
1. Wyodrębnij zawartość pliku zip do folderu na dysku.
1. Otwórz aplikację terminala macOS `cd` i użyj polecenia, aby przełączyć się do folderu użytego w poprzednim kroku.
1. Z poziomu folderu uruchom `./tf` polecenie, aby sprawdzić, czy klient wiersza polecenia może być uruchomiony, może zostać wyświetlony monit o zainstalowanie oprogramowania Java lub innych zależności.

Po zainstalowaniu tee-CLC można uruchomić `tf eula` polecenie, aby wyświetlić i zaakceptować umowę licencyjną dla klienta.

Na koniec, aby uwierzytelnić się w środowisku TFS/Azure DevOps, musisz utworzyć token dostępu osobistego na serwerze. Dowiedz się więcej o [uwierzytelnieniu za pomocą tokenów dostępu osobistego](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops). Podczas tworzenia tokenu dostępu osobistego do użycia z TFVC, należy podać pełny dostęp podczas konfigurowania tokenu.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Łączenie się z repozytorium za pomocą tee-CLC

Aby połączyć się z kodem źródłowym, należy `tf workspace` najpierw utworzyć obszar roboczy za pomocą polecenia. Na przykład następujące polecenia łączą się z organizacją w usługach Azure DevOps o nazwie "MyOrganization": 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

Ustawienie `TF_AUTO_SAVE_CREDENTIALS` środowiska służy do zapisywania poświadczeń, więc nie jest wyświetlany monit o ich wielokrotne wprowadzanie. Po wyświetleniu monitu o podanie nazwy użytkownika użyj tokenu dostępu osobistego utworzonego w poprzedniej sekcji i użyj pustego hasła.

Aby utworzyć mapowanie plików źródłowych do folderu lokalnego, użyjesz tego `tf workfold` polecenia. Poniższy przykład będzie mapować folder o nazwie "WebApp.Services" z projektu TFVC "MyRepository" i skonfigurować go do kopiowania do lokalnego folderu ~/Projects/ (tj. folderu "Projekty" w folderze domowym bieżących użytkowników).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Na koniec należy użyć następującego polecenia, aby uzyskać pliki źródłowe z serwera i skopiować je lokalnie:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>Zatwierdzanie zmian przy użyciu TEE-CLC

Po włączeniu zmian w plikach w programie Visual Studio dla komputerów Mac można przełączyć się z powrotem do terminalu, aby zaewidencjonować zmiany. Polecenie `tf add` służy do dodawania plików do listy oczekujących zmian, `tf checkin` które mają zostać zaewidencjonowane, a polecenie wykonuje rzeczywiste zaewidencjonowanie na serwerze. Polecenie `checkin` zawiera parametry, aby dodać komentarz lub skojarzyć powiązany element pracy. We wpisie kodu poniżej wszystkie pliki `WebApp.Services` w folderze są dodawane, cyklicznie, do ewidencjonowania. Następnie kod jest zaewidencjonowany z komentarzem i skojarzony z elementem pracy o identyfikatorze "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Aby dowiedzieć się więcej o poleceniach wymienionych tutaj lub innych, można użyć następującego polecenia z terminala:

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Łączenie się z tfvc przy użyciu rozszerzenia Team Foundation Version Control

> [!NOTE]
> Aby uzyskać najlepsze środowisko kontroli wersji w systemie macOS, zalecamy użycie git zamiast Team Foundation Version Control (TFVC). Git jest obsługiwany w programie Visual Studio dla komputerów Mac i jest domyślną opcją dla repozytoriów hostowanych w programie Team Foundation Server (TFS)/Azure DevOps. Aby dowiedzieć się więcej na temat korzystania z git z TFS/Azure DevOps, zobacz [konfigurowanie repozytorium Git](/visualstudio/mac/set-up-git-repository) artykułu.
>
> Jeśli wcześniej używano wersji w wersji zapoznawczej rozszerzenia TFVC dla programu Visual Studio dla komputerów Mac, nie jest już obsługiwana podczas uaktualniania do programu Visual Studio 2019 dla komputerów Mac.

W galerii rozszerzenia programu Visual Studio dla komputerów Mac istnieje rozszerzenie kontroli wersji programu Team Foundation, które oferuje ograniczoną obsługę, aby połączyć się z TFVC. Rozszerzenie nie jest obsługiwane i ma kilka znanych problemów, więc doświadczenie może się różnić podczas korzystania z niego.

Aby zainstalować rozszerzenie, uruchom program Visual Studio dla komputerów Mac i wybierz menu **Rozszerzenia > programu Visual Studio.** Na karcie **Galeria** wybierz pozycję **Kontrola wersji > kontrola wersji programu Team Foundation dla usług TFS i azure DevOps** i kliknij pozycję **Zainstaluj...**:

![Menedżer rozszerzeń](media/tfvc-install.png)

Postępuj zgodnie z instrukcjami, aby zainstalować rozszerzenie. Po zainstalowaniu uruchom ponownie IDE.

### <a name="updating-the-extension"></a>Aktualizowanie rozszerzenia

Aktualizacje rozszerzenia TFVC są okresowo. Aby uzyskać dostęp do aktualizacji, wybierz z menu **polecenie Visual Studio > Rozszerzenia...** i wybierz **Update** kartę **Aktualizacje.**

Naciśnij **przycisk Zainstaluj** w następnym oknie dialogowym, aby odinstalować stary pakiet i zainstalować nowy.

### <a name="using-the-extension"></a>Korzystanie z rozszerzenia

Po zainstalowaniu rozszerzenia wybierz pozycję menu **Kontrola wersji > TFS/Azure DevOps > Open z repozytorium zdalnego...** element menu.

![Element menu, aby otworzyć rozszerzenie](media/tfvc-source-control-explorer-devops.png)

Wybierz program VSTS lub Team Foundation Server, aby rozpocząć pracę, a następnie naciśnij przycisk **Kontynuuj:**

![Łączenie się z serwerem](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Uwierzytelnianie repozytorium platformy Azure

Po wybraniu projektu, który jest hostowany w repo platformy Azure, zostanie wyświetlony monit o wprowadzenie szczegółów konta Microsoft:

![Połącz się z repozytorium platformy Azure](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>Uwierzytelnianie TFS

Aby połączyć się z usługą TFS, wprowadź szczegóły serwera i poświadczenia konta. Wprowadź domenę, aby użyć uwierzytelniania NTLM, w przeciwnym razie pozostaw puste miejsce, aby użyć uwierzytelniania podstawowego. Wybierz **pozycję Dodaj serwer:**

![Logowanie się do serwera TFS](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Wybieranie projektu

Po pomyślnym uwierzytelnieniu w oknie dialogowym **Kontrola źródła** zostanie wyświetlona lista repozytoriów skojarzonych z kontem:

![Otwórz z okna dialogowego Kontrola źródła z wyświetlonymi projektami](media/tfvc-vsts-projects.png)

To okno dialogowe jest zorganizowane z następującymi węzłami:

- Organizacja lub kolekcja programu Azure DevOps — wyświetla wszystkie organizacje połączone z kontem Microsoft, za pomocą którego użytkownik się zalogował.
- Projekty — w każdej organizacji lub kolekcji można mieć wiele projektów. Projekt jest, gdzie kod źródłowy, elementy robocze i zautomatyzowane kompilacje są hostowane.

W tym momencie można wyszukiwać i filtrować według nazwy projektu lub organizacji.

#### <a name="adding-a-new-server"></a>Dodawanie nowego serwera

Aby dodać nowy serwer do listy, naciśnij przycisk **Dodaj hosta** w oknie dialogowym **Otwórz z kontrolki źródła:**

![Wyróżniony przycisk dodaj, aby dodać nowy serwer do listy](media/tfvc-add-new-server.png)

Wybierz dostawcę z listy i wprowadź poświadczenia:

![Okno dialogowe z opcją dla dostawcy kontroli źródła](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Tworzenie nowego obszaru roboczego

Aby rozpocząć pracę z projektem, musisz mieć _obszar roboczy_. Jeśli nie masz jeszcze obszaru roboczego, możesz go utworzyć z pola kombi **Obszaru roboczego** w oknie dialogowym **Kontrola źródła Otwórz z źródła:**

![Tworzenie nowej opcji pola kombi obszaru roboczego](media/tfvc-create-new-workspace.png)

Ustaw nazwę i ścieżkę lokalną dla nowego obszaru roboczego i wybierz pozycję **Utwórz obszar roboczy:**

![Wprowadzanie nazwy i ścieżki lokalnej dla nowego obszaru roboczego](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Korzystanie z Eksploratora kodu źródłowego

Po utworzeniu obszaru roboczego i zamapowania projektu można rozpocząć pracę z _Eksploratorem kodu źródłowego_.

Aby otworzyć Eksploratora kodu źródłowego, wybierz pozycję menu **Kontrola wersji > TFS/Azure DevOps > Eksplorator kontroli źródła.**

Eksplorator kodu źródłowego umożliwia poruszanie się po wszystkich mapowanych projektach, ich plikach i folderach. Umożliwia również wykonywanie wszystkich podstawowych akcji kontroli źródła, takich jak:

- Pobierz najnowszą wersję
- Uzyskaj określoną wersję
- Ewidencjonowanie i wyewidencjonowywanie plików
- Blokowanie i odblokowywanie plików
- Dodawanie, usuwanie i zmienianie nazw plików
- Wyświetlanie historii
- Porównaj zmiany.

Wiele z tych działań jest dostępnych za pośrednictwem działań kontekstowych projektu:

![Akcje menu kontekstowego dla projektu](media/tfvc-sourcecode-actions.png)

### <a name="managing-workspaces"></a>Zarządzanie obszarami roboczymi

Jeśli nie utworzono jeszcze obszaru roboczego, zgodnie z opisem w sekcji [Tworzenie obszaru roboczego,](#creating-a-new-workspace) można zauważyć, że Eksplorator kodu źródłowego jest pusty:

![pusty eksplorator kodu źródłowego](media/tfvc-setup-empty-sce.png)

Aby skonfigurować projekt zdalny w lokalnym obszarze roboczym, należy wykonać następujące czynności:

1. Wybierz **serwer** z pola kombi.
1. Należy zauważyć, że istnieją "brak obszarów roboczych" i że ścieżka lokalna jest "Nie mapowane". Wybierz **łącze Nie mapowane,** aby wyświetlić okno dialogowe **Utwórz nowy obszar roboczy.**
1. Podaj nazwę obszaru roboczego, a następnie kliknij przycisk **Dodaj folder roboczy,** aby zamapować projekt na folder lokalny na komputerze:

    ![Tworzenie nowego okna dialogowego obszaru roboczego z opcjami domyślnymi](media/tfvc-workspace1.png)

1. Wybierz folder "$", aby zamapować wszystkie projekty na serwerze do tego samego obszaru roboczego, lub wybierz pojedynczy projekt, a następnie kliknij przycisk **OK:**

    ![Okno dialogowe Przeglądania folderu przedstawiające wszystkie projekty](media/tfvc-workspace2.png)

1. Wybierz lokalizację na komputerze lokalnym, na którą chcesz zamapować projekt, i kliknij przycisk **Wybierz folder**.
1. Potwierdź szczegóły nowego obszaru roboczego, naciskając przycisk **OK**

    ![Tworzenie nowego okna dialogowego obszaru roboczego z dodanym folderem roboczym](media/tfvc-workspace3.png)

Po skonfigurowaniu obszaru roboczego można go zmienić lub usunąć, klikając przycisk **Zarządzaj obszarami roboczymi** w Eksploratorze kodu źródłowego.

![Zarządzanie obszarami roboczymi](media/tfvc-workspace4.png)

## <a name="troubleshooting-and-known-issues"></a>Rozwiązywanie problemów i znane problemy

#### <a name="problems-using-basic-authentication"></a>Problemy z wykorzystaniem uwierzytelniania podstawowego

Do uwierzytelniania na serwerze można użyć następujących opcji:

- Oauth
- Podstawowa (Basic)
- Ntlm

Aby użyć uwierzytelniania podstawowego, konieczne jest włączenie **alternatywnych poświadczeń uwierzytelniania** w usługach Azure DevOps, wykonując poniższe kroki:

1. Zaloguj się do organizacji Programu Azure DevOps\/jako właściciel (https: /dev.azure.com/{organization}/{project}).

2. Na pasku narzędzi organizacji wybierz ikonę koła zębatego i wybierz pozycję **Zasady:**

    ![Wybrano opcję ustawień zasad](media/tfvc-auth2.png)

3. Przejrzyj ustawienia połączenia aplikacji. Zmień te ustawienia na podstawie zasad zabezpieczeń:

    ![Wybrano opcję ustawień zasad](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>Nie widzę nic w TFVC

Aby skonfigurować system Team Foundation Version Control (TFVC) na komputerze deweloperskim, **należy** utworzyć obszar roboczy, zgodnie z opisem w sekcji [Zarządzanie obszarami roboczymi.](#managing-workspaces)

W Eksploratorze kontroli źródła naciśnij przycisk **Zarządzaj obszarami roboczymi.** Wykonaj kroki, aby zamapować projekt do folderu na komputerze deweloperskim.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>Nie widzę żadnych / wszystkich moich projektów

Po uwierzytelnieniu powinna zostać wyświetlona lista projektów. Domyślnie wyświetlane są tylko projekty TFS. Aby wyświetlić inne typy projektów, zaznacz pole "Zobacz wszystkie projekty".

Należy pamiętać, że projekty, które znajdują się na serwerze nie pojawi się, jeśli nie masz odpowiednich uprawnień.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Pojawia się błąd "Nie można utworzyć obszaru roboczego. Spróbuj ponownie"

Podczas próby [utworzenia nowego obszaru roboczego](#creating-a-new-workspace)należy upewnić się, że spełnione są następujące warunki:

- Brak użycia nieprawidłowych znaków w nazwie obszaru roboczego.
- Nazwa musi być mniejsza niż 64 znaki.
- Ścieżka lokalna nie może być używana przez inne obszary robocze.

### <a name="see-also"></a>Zobacz też

- [Tworzenie i udostępnianie kodu w TFVC przy użyciu programu Visual Studio (w systemie Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)