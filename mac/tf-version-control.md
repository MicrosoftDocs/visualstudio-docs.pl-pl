---
title: Kontrola wersji serwera Team Foundation (TFVC)
description: Przewodnik rozwiązywania problemów dotyczący TFVC i macOS.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/02/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: 0808f86f8571210a9048faf2e825b483120e73ca
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584207"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Czy program Visual Studio dla komputerów Mac obsługuje kontrolę wersji programu Team Foundation?

> [!CAUTION]
> Rozszerzenie TFVC podglądu dla Visual Studio dla komputerów Mac nie jest już obsługiwane w programie Visual Studio 2019 for Mac.


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Alternatywne opcje kontroli wersji w Visual Studio dla komputerów Mac

Aby zapewnić najlepszą kontrolę wersji w systemie macOS, zalecamy korzystanie z **narzędzia Git** zamiast Kontrola wersji serwera Team Foundation (TFVC). 

Narzędzie git jest obsługiwane w Visual Studio dla komputerów Mac i jest opcją domyślną dla repozytoriów hostowanych w Team Foundation Server (TFS)/Azure DevOps. Aby dowiedzieć się więcej o korzystaniu z narzędzia Git z programem TFS/Azure DevOps, zobacz Podręcznik [konfigurowania repozytorium git](./set-up-git-repository.md) .

## <a name="unsupported-workarounds-for-tfvc"></a>Nieobsługiwane obejścia dla TFVC

Mimo że Visual Studio dla komputerów Mac nie obsługiwał oficjalnie TFVC, pozostała część tego przewodnika zawiera pewne obejścia do pracy z TFVC na macOS. Jeśli obecnie używasz usługi TFVC na potrzeby kontroli wersji, Oto kilka rozwiązań, których można użyć w celu uzyskania dostępu do kodu źródłowego hostowanego w TFVC:

* Sposób 1. [ Użyj Visual Studio Code i rozszerzenia Azure Repos, dla graficznego interfejsu użytkownika](#use-visual-studio-code-and-the-azure-repos-extension)
* Sposób 2. [Nawiązywanie połączenia z repozytorium przy użyciu Team Explorer Everywhere wiersza polecenia klienta (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)

### <a name="option-1--use-visual-studio-code-and-the-azure-repos-extension"></a>Sposób 1. <a id="use-visual-studio-code-and-the-azure-repos-extension"></a> Użyj Visual Studio Code i rozszerzenia Azure Repos

Jeśli chcesz współpracować z interfejsem graficznym w celu zarządzania plikami w kontroli wersji, rozszerzenie Azure Repos dla Visual Studio Code udostępnia rozwiązanie obsługiwane przez firmę Microsoft. Aby rozpocząć, Pobierz [Visual Studio Code](https://code.visualstudio.com) a następnie Dowiedz się, jak [skonfigurować rozszerzenie Azure Repos](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

### <a name="option-2--connecting-using-the-team-explorer-everywhere-command-line-client"></a>Sposób 2. <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a> Nawiązywanie połączenia przy użyciu Team Explorer Everywhere klienta wiersza polecenia

> [!IMPORTANT]
> Zgodnie z Team Explorer Everywherem Readme ten projekt [nie jest już obsługiwany](https://github.com/microsoft/team-explorer-everywhere).

Jeśli nie masz doświadczenia w korzystaniu z terminalu macOS, klient wiersza polecenia Team Explorer Everywhere (TEE-CLC) zapewnia obsługiwany sposób nawiązywania połączenia ze źródłem w programie TFVC.

Możesz wykonać poniższe kroki, aby skonfigurować połączenie do TFVC i zatwierdzić zmiany.

#### <a name="setting-up-the-tee-clc"></a>Konfigurowanie TEE-CLC

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

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Nawiązywanie połączenia z repozytorium przy użyciu TEE-CLC

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

#### <a name="committing-changes-using-the-tee-clc"></a>Zatwierdzanie zmian przy użyciu TEE-CLC

Po wprowadzeniu zmian w plikach w Visual Studio dla komputerów Mac można wrócić do terminalu, aby zaewidencjonować zmiany. `tf add`Polecenie służy do dodawania plików do listy oczekujących zmian do zaewidencjonowania, a `tf checkin` polecenie wykonuje rzeczywiste ewidencjonowanie na serwerze. `checkin`Polecenie zawiera parametry służące do dodawania komentarza lub kojarzenia powiązanego elementu pracy. W poniższym fragmencie kodu wszystkie pliki w `WebApp.Services` folderze są dodawane cyklicznie do zaewidencjonowania. Następnie kod jest sprawdzany z komentarzem i skojarzony z elementem roboczym o IDENTYFIKATORze "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Aby dowiedzieć się więcej na temat poleceń wymienionych tutaj lub innych, można użyć następującego polecenia z terminalu:

`tf help`

## <a name="see-also"></a>Zobacz też

- [Opracowywanie i udostępnianie kodu w programie TFVC przy użyciu programu Visual Studio (w systemie Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)