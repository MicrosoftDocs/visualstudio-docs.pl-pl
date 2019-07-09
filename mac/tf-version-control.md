---
title: Team Foundation Version Control (TFVC)
description: Nawiązywanie połączenia z programu Visual Studio dla komputerów Mac w Team Foundation Server/DevOps platformy Azure za pomocą Team Foundation Version Control (TFVC).
author: jmatthiesen
ms.author: jomatthi
ms.date: 06/25/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 378d1eaf1d57818a976f41a81c1098d75bb12e48
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691952"
---
# <a name="connecting-to-team-foundation-version-control"></a>Nawiązywanie połączenia z Team Foundation Version Control

> [!NOTE]
> Aby uzyskać najlepsze wyniki kontroli wersji w systemie macOS zaleca się przy użyciu narzędzia Git zamiast Team Foundation Version Control (TFVC). Git jest obsługiwana w programie Visual Studio dla komputerów Mac i jest to opcja domyślna, w przypadku repozytoriów hostowanych w Team Foundation Server (TFS) / DevOps platformy Azure. Aby dowiedzieć się więcej o korzystaniu z usługi Git przy użyciu infrastruktury DevOps programu TFS/Azure, zobacz [Konfigurowanie repozytorium Git](/visualstudio/mac/set-up-git-repository) artykułu.
> 
> Jeśli wcześniej używano rozszerzenia TFVC wersję zapoznawczą programu Visual Studio dla komputerów Mac, go nie jest już obsługiwana w programie Visual Studio 2019 dla komputerów Mac.

Repozytoriów platformy Azure oferuje dwa modele kontroli wersji: [Git](/azure/devops/repos/git/?view=azure-devops), rozproszony system kontroli wersji, a [Team Foundation Version Control](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC), wersjami w sposób scentralizowany system kontroli.

Program Visual Studio for Mac zapewnia pełną obsługę dla repozytoriów Git, ale wymaga obejścia do pracy z użyciem systemu TFVC. Jeśli obecnie używasz TFVC do kontroli wersji, poniżej przedstawiono niektóre rozwiązania, które umożliwia dostęp do kodu źródłowego hostowanych w TFVC:

* [Przy użyciu programu Visual Studio Code i rozszerzenia repozytoriów platformy Azure, graficznego interfejsu użytkownika](#use-visual-studio-code-and-the-azure-repos-extension)
* [Nawiązać połączenie z repozytorium, korzystając z Team Explorer Everywhere wiersza polecenia klienta (TEE CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)

W pozostałej części tego artykułu przeprowadzi Cię przez opcje wymienionych powyżej.

## <a name="requirements"></a>Wymagania

* Visual Studio Community, Professional lub Enterprise dla komputerów Mac w wersji 7,8 i nowszych.
* Usługom DevOps platformy Azure, Team Foundation Server 2013 i nowsze, lub na platformie Azure DevOps Server 2018 r. lub później.
* Projekt w usługom DevOps platformy Azure lub Team Foundation Server/Azure DevOps Server skonfigurowany do używania kontroli wersji serwera Team Foundation.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Przy użyciu programu Visual Studio Code i rozszerzenia repozytoriów platformy Azure

Jeśli wolisz pracować z interfejsem graficznym do zarządzania plikami w kontroli wersji, następnie rozszerzenie repozytoriów platformy Azure dla programu Visual Studio Code oferuje wspierane rozwiązanie firmy Microsoft. Aby rozpocząć pracę, Pobierz [programu Visual Studio Code](https://code.visualstudio.com) i Dowiedz się, jak [skonfiguruj rozszerzenie Azure repozytoriów](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Łączenie za pomocą Team Explorer Everywhere klienta wiersza polecenia

Jeśli wiesz, przy użyciu systemu macOS Terminal, a następnie z Team Explorer Everywhere klienta wiersza polecenia (TEE CLC) umożliwia obsługiwanych nawiązywania połączenia ze źródłem w TFVC.

Można wykonaj poniższe kroki, aby skonfigurować połączenie TFVC oraz zatwierdzić zmiany.

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

Aby utworzyć mapowanie plików źródłowych do folderu lokalnego, użyjesz `tf workfold` polecenia. Poniższy przykład zmapuje folder o nazwie "WebApp.Services" z "MyRepository" TFVC projektu i ustawić go tak, aby być skopiowany do folderu lokalnego ~/Projects/ (czyli folder "Projekty" w folderze głównym bieżących użytkowników).

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

### <a name="see-also"></a>Zobacz także

- [Tworzenie i udostępnianie kodu w TFVC przy użyciu programu Visual Studio (na Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)