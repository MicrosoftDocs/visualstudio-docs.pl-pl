---
title: Rozwiązywanie problemów z błędami klienta platformy Docker na Windows | Dokumentacja firmy Microsoft
description: Rozwiązywanie problemów napotykanych podczas korzystania z programu Visual Studio do tworzenia i wdrażania aplikacji sieci web do platformy Docker na Windows za pomocą programu Visual Studio 2017.
ms.technology: vs-azure
author: devinb
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 10/13/2017
ms.author: devinb
ms.openlocfilehash: 396ad65835375c9c85bc3d67ca685f6270bbb7d3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58160425"
---
# <a name="troubleshoot-visual-studio-2017-development-with-docker"></a>Rozwiązywanie problemów związanych z opracowywaniem zwartości w programie Visual Studio 2017 przy użyciu platformy Docker

Podczas pracy z Visual Studio Tools for Docker, mogą wystąpić problemy podczas kompilowania lub debugowania aplikacji. Poniżej są niektóre typowe kroki rozwiązywania problemów.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Udostępnianie woluminów nie jest włączona. Włącz udostępnianie woluminów w ustawieniach platformy Docker CE dla Windows (tylko w przypadku kontenerów systemu Linux)

Aby rozwiązać ten problem:

1. Kliknij prawym przyciskiem myszy **Docker for Windows** w obszarze powiadomień, a następnie wybierz **ustawienia**.
1. Wybierz **udostępnione dyski** i Udostępnij dysk systemowy, wraz z dysku, na którym znajduje się projekt.

> [!NOTE]
> Jeśli pliki są wyświetlane udostępniony, nadal może być konieczne kliknij link "Resetuj poświadczenia..." w dolnej części okna dialogowego, aby ponownie włączyć udostępnianie woluminów. Aby kontynuować po zresetowaniu poświadczeń, może być ponowne uruchomienie programu Visual Studio.

![dyski udostępnione](media/vs-azure-tools-docker-troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Visual Studio 2017 w wersji 15.6 lub nowszej monitowanie, gdy **udostępnione dyski** nie są skonfigurowane.

### <a name="container-type"></a>Typ kontenera

Podczas dodawania obsługi programu Docker do projektu, możesz wybrać kontener systemu Linux lub Windows. Hosta platformy Docker musi działać ten sam typ kontenera. Aby zmienić typ kontenera, na uruchomione wystąpienie platformy Docker, kliknij prawym przyciskiem myszy ikonę platformy Docker w zasobniku systemowym, a następnie wybierz **przełączyć się do kontenerów Windows...**  lub **przełączyć się do kontenerów systemu Linux...** .

## <a name="unable-to-start-debugging"></a>Nie można rozpocząć debugowania

Jedną z przyczyn może być związany z mających nieaktualne składniki debugowania w folderze profilu użytkownika. Wykonaj następujące polecenia, aby usunąć te foldery, aby składniki najnowsza wersja debugowania są pobierane w następnej sesji debugowania.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Błędy specyficzne dla sieci podczas debugowania aplikacji

Spróbuj wykonywanie skryptu do pobrania z [oczyszczania kontenera hosta sieci](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), która będzie odświeżać składników związanych z siecią na maszynie hosta.

## <a name="mounts-denied"></a>Instaluje odmowa

Korzystając z platformy Docker dla systemu macOS, może wystąpić błąd odwołujące się do /usr/local/share/dotnet/sdk/NuGetFallbackFolder folderu. Dodaj folder do karty Udostępnianie plików na platformie Docker

## <a name="microsoftdockertools-github-repo"></a>Repozytorium GitHub Microsoft/DockerTools

Aby uzyskać inne problemy wystąpią, zobacz [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) problemów.