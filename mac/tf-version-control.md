---
title: Kontrola wersji Team Foundation (TFVC)
description: Przewodnik rozwiązywania problemów dotyczący TFVC i macOS.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/02/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: e56aec03aabe818731c65acb30eafcc18f170ac3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714510"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Czy program Visual Studio dla komputerów Mac obsługuje kontrolę wersji programu Team Foundation?

> [!CAUTION]
> Rozszerzenie TFVC w wersji zapoznawczej dla programu Visual Studio dla komputerów Mac nie jest już obsługiwane w programie Visual Studio 2019 dla komputerów Mac.


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Opcje alternatywnej kontroli wersji w programie Visual Studio dla komputerów Mac

Aby uzyskać najlepsze środowisko kontroli wersji w systemie macOS, zalecamy użycie **git** zamiast Team Foundation Version Control (TFVC). 

Git jest obsługiwany w programie Visual Studio dla komputerów Mac i jest domyślną opcją dla repozytoriów hostowanych w programie Team Foundation Server (TFS)/Azure DevOps. Aby dowiedzieć się więcej na temat korzystania z git z TFS/Azure DevOps, zobacz [Konfigurowanie repozytorium Git](/visualstudio/mac/set-up-git-repository) przewodnik.

## <a name="unsupported-workarounds-for-tfvc"></a>Nieobsługiwały obejścia tfvc

Program Visual Studio dla komputerów Mac oficjalnie nie obsługuje usługi TFVC, ale pozostała część tego przewodnika zawiera pewne obejścia dotyczące pracy z TFVC w systemie macOS. Jeśli używasz TFVC do kontroli wersji dzisiaj, oto kilka rozwiązań, których można użyć, aby uzyskać dostęp do kodu źródłowego hostowanego w TFVC:

* Sposób 1. [Używanie kodu programu Visual Studio i rozszerzenia repozytorium platformy Azure dla graficznego interfejsu użytkownika](#use-visual-studio-code-and-the-azure-repos-extension)
* Sposób 2. [Łączenie się z repozytorium przy użyciu klienta wiersza polecenia Eksploratora wszędzie (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)

### <a name="option-1--use-visual-studio-code-and-the-azure-repos-extension"></a>Sposób 1. <a id="use-visual-studio-code-and-the-azure-repos-extension"></a>Używanie kodu programu Visual Studio i rozszerzenia repozytorium platformy Azure

Jeśli chcesz pracować z interfejsem graficznym do zarządzania plikami w kontroli wersji, rozszerzenie Repozytorium platformy Azure dla programu Visual Studio Code zapewnia obsługiwane rozwiązanie firmy Microsoft. Aby rozpocząć, pobierz [program Visual Studio Code,](https://code.visualstudio.com) a następnie dowiedz się, jak [skonfigurować rozszerzenie Repozytorium platformy Azure](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

### <a name="option-2--connecting-using-the-team-explorer-everywhere-command-line-client"></a>Sposób 2. <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Łączenie się przy użyciu klienta wiersza polecenia Eksploratora zespołu wszędzie

> [!IMPORTANT]
> Zgodnie z programem ReadME Team Explorer Everywhere, ten projekt nie jest [już utrzymywany.](https://github.com/microsoft/team-explorer-everywhere)

Jeśli korzystasz z terminala macOS, klient wiersza polecenia Team Explorer Everywhere (TEE-CLC) zapewnia obsługiwany sposób łączenia się ze źródłem w TFVC.

Możesz wykonać poniższe czynności, aby skonfigurować połączenie z TFVC i zatwierdzić zmiany.

#### <a name="setting-up-the-tee-clc"></a>Konfigurowanie tee-CLC

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

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Łączenie się z repozytorium za pomocą tee-CLC

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

#### <a name="committing-changes-using-the-tee-clc"></a>Zatwierdzanie zmian przy użyciu TEE-CLC

Po włączeniu zmian w plikach w programie Visual Studio dla komputerów Mac można przełączyć się z powrotem do terminalu, aby zaewidencjonować zmiany. Polecenie `tf add` służy do dodawania plików do listy oczekujących zmian, `tf checkin` które mają zostać zaewidencjonowane, a polecenie wykonuje rzeczywiste zaewidencjonowanie na serwerze. Polecenie `checkin` zawiera parametry, aby dodać komentarz lub skojarzyć powiązany element pracy. We wpisie kodu poniżej wszystkie pliki `WebApp.Services` w folderze są dodawane, cyklicznie, do ewidencjonowania. Następnie kod jest zaewidencjonowany z komentarzem i skojarzony z elementem pracy o identyfikatorze "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Aby dowiedzieć się więcej o poleceniach wymienionych tutaj lub innych, można użyć następującego polecenia z terminala:

`tf help`

## <a name="see-also"></a>Zobacz też

- [Tworzenie i udostępnianie kodu w TFVC przy użyciu programu Visual Studio (w systemie Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)