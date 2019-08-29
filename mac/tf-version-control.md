---
title: Kontrola wersji serwera Team Foundation (TFVC)
description: Nawiązywanie połączenia z Visual Studio dla komputerów Mac Team Foundation Server/Azure DevOps z usługą Kontrola wersji serwera Team Foundation (TFVC).
author: jmatthiesen
ms.author: jomatthi
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 4d0de2b9d91458a4baa7d0ed6498fbc7f65b2fb1
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108087"
---
# <a name="connecting-to-team-foundation-version-control"></a>Nawiązywanie połączenia z Kontrola wersji serwera Team Foundation

> [!NOTE]
> Aby zapewnić najlepszą kontrolę wersji w systemie macOS, zalecamy korzystanie z narzędzia Git zamiast Kontrola wersji serwera Team Foundation (TFVC). Narzędzie git jest obsługiwane w Visual Studio dla komputerów Mac i jest opcją domyślną dla repozytoriów hostowanych w Team Foundation Server (TFS)/Azure DevOps. Aby dowiedzieć się więcej o korzystaniu z narzędzia Git z programem TFS/Azure DevOps, zobacz artykuł [Konfigurowanie repozytorium git](/visualstudio/mac/set-up-git-repository) .
> 
> Jeśli wcześniej była używana wersja zapoznawcza rozszerzenia TFVC dla Visual Studio dla komputerów Mac, nie jest już obsługiwana w programie Visual Studio 2019 for Mac.

Azure Repos oferuje dwa modele kontroli wersji: [Git](/azure/devops/repos/git/?view=azure-devops), rozproszony system kontroli wersji i [Kontrola wersji serwera Team Foundation](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC) — scentralizowany system kontroli wersji.

Visual Studio dla komputerów Mac zapewnia pełną obsługę repozytoriów Git, ale wymaga zastosowania niektórych rozwiązań do pracy z usługą TFVC. Jeśli obecnie używasz usługi TFVC na potrzeby kontroli wersji, Oto kilka rozwiązań, których można użyć w celu uzyskania dostępu do kodu źródłowego hostowanego w TFVC:

* [Użyj Visual Studio Code i rozszerzenia Azure Repos, dla graficznego interfejsu użytkownika](#use-visual-studio-code-and-the-azure-repos-extension)
* [Nawiązywanie połączenia z repozytorium przy użyciu Team Explorer Everywhere wiersza polecenia klienta (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)

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
1. Po zainstalowaniu oprogramowania Homebrew Uruchom następujące polecenie z terminalu:`brew install tee-clc`

Aby **ręcznie skonfigurować tee-CLC**:

1. [Pobierz najnowszą wersję tee-CLC](https://github.com/Microsoft/team-explorer-everywhere/releases) ze Team Explorer Everywhere strony wersji repozytorium GitHub (np. tee-CLC-14.134.0. zip w momencie pisania tego zapisu).
1. Wyodrębnij zawartość pliku zip do folderu na dysku.
1. Otwórz aplikację terminala macOS i Użyj `cd` polecenia, aby przełączyć się do folderu, który został użyty w poprzednim kroku.
1. Z poziomu folderu Uruchom polecenie `./tf` , aby sprawdzić, czy można uruchomić klienta wiersza polecenia. może zostać wyświetlony monit o zainstalowanie języka Java lub innych zależności.

Po zainstalowaniu tee-CLC można uruchomić polecenie `tf eula` , aby wyświetlić i zaakceptować umowę licencyjną dla klienta.

Na koniec, aby uwierzytelnić się w środowisku DevOps TFS/Azure, musisz utworzyć osobisty token dostępu na serwerze. Dowiedz się więcej o [uwierzytelnianiu z osobistymi tokenami dostępu](https://docs.microsoft.com/azure/devops/integrate/get-started/authentication/pats?view=azure-devops). Podczas tworzenia osobistego tokenu dostępu do używania z usługą TFVC należy zapewnić pełen dostęp podczas konfigurowania tokenu.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Nawiązywanie połączenia z repozytorium przy użyciu TEE-CLC

Aby nawiązać połączenie z kodem źródłowym, musisz najpierw utworzyć obszar roboczy przy użyciu `tf workspace` polecenia. Na przykład następujące polecenia nawiązują połączenie z organizacją w Azure DevOps Services o nazwie "Moja organizacja": 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

Ustawienie `TF_AUTO_SAVE_CREDENTIALS` środowisko służy do zapisywania poświadczeń, dlatego nie zostanie wyświetlony monit o wprowadzenie ich wiele razy. Po wyświetleniu monitu o podanie nazwy użytkownika Użyj osobistego tokenu dostępu utworzonego w poprzedniej sekcji i użyj pustego hasła.

Aby utworzyć mapowanie plików źródłowych do folderu lokalnego, użyj `tf workfold` polecenia. Poniższy przykład mapuje folder o nazwie "WebApp. Services" z projektu TFVC "moje repozytorium" i skonfiguruje go do kopiowania do lokalnego folderu ~/Projects/(tj. folder "projects" w folderze głównym bieżącego użytkownika).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Na koniec użyj następującego polecenia, aby pobrać pliki źródłowe z serwera i skopiować je lokalnie:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>Zatwierdzanie zmian przy użyciu TEE-CLC

Po wprowadzeniu zmian w plikach w Visual Studio dla komputerów Mac można wrócić do terminalu, aby zaewidencjonować zmiany. Polecenie służy do dodawania plików do listy oczekujących zmian do zaewidencjonowania `tf checkin` , a polecenie wykonuje rzeczywiste ewidencjonowanie na serwerze. `tf add` `checkin` Polecenie zawiera parametry służące do dodawania komentarza lub kojarzenia powiązanego elementu pracy. W poniższym fragmencie kodu wszystkie pliki w `WebApp.Services` folderze są dodawane cyklicznie do zaewidencjonowania. Następnie kod jest sprawdzany z komentarzem i skojarzony z elementem roboczym o IDENTYFIKATORze "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Aby dowiedzieć się więcej na temat poleceń wymienionych tutaj lub innych, można użyć następującego polecenia z terminalu:

`tf help`

### <a name="see-also"></a>Zobacz także

- [Opracowywanie i udostępnianie kodu w programie TFVC przy użyciu programu Visual Studio (w systemie Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)