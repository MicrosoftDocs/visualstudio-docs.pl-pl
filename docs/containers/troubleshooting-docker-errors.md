---
title: Rozwiązywanie problemów z błędami klienta platformy Docker na Windows | Dokumentacja firmy Microsoft
description: Rozwiązywanie problemów napotykanych podczas korzystania z programu Visual Studio do tworzenia i wdrażania aplikacji sieci web do platformy Docker na Windows za pomocą programu Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 10/13/2017
ms.author: ghogen
ms.openlocfilehash: ca43098740a1e8e940f27eae8d2c4d405c23230b
ms.sourcegitcommit: 16d8ffc624adb716753412a22d586eae68a29ba2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412275"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Rozwiązywanie problemów związanych z opracowywaniem zwartości w programie Visual Studio przy użyciu platformy Docker

Podczas pracy z narzędzia kontenerów programu Visual Studio, mogą wystąpić problemy podczas kompilowania lub debugowania aplikacji. Poniżej są niektóre typowe kroki rozwiązywania problemów.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Udostępnianie woluminów nie jest włączona. Włącz udostępnianie woluminów w ustawieniach platformy Docker CE dla Windows (tylko w przypadku kontenerów systemu Linux)

Aby rozwiązać ten problem:

1. Kliknij prawym przyciskiem myszy **Docker for Windows** w obszarze powiadomień, a następnie wybierz **ustawienia**.
1. Wybierz **udostępnione dyski** i Udostępnij dysk systemowy, wraz z dysku, na którym znajduje się projekt.

> [!NOTE]
> Jeśli pliki są wyświetlane udostępniony, nadal może być konieczne kliknij link "Resetuj poświadczenia..." w dolnej części okna dialogowego, aby ponownie włączyć udostępnianie woluminów. Aby kontynuować po zresetowaniu poświadczeń, może być ponowne uruchomienie programu Visual Studio.

![dyski udostępnione](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Wersje serwera Visual Studio później niż Visual Studio 2017 w wersji 15.6 monitowanie, gdy **udostępnione dyski** nie są skonfigurowane.

### <a name="container-type"></a>Typ kontenera

Podczas dodawania obsługi programu Docker do projektu, możesz wybrać kontener systemu Linux lub Windows. Hosta platformy Docker musi działać ten sam typ kontenera. Aby zmienić typ kontenera, na uruchomione wystąpienie platformy Docker, kliknij prawym przyciskiem myszy ikonę platformy Docker w zasobniku systemowym, a następnie wybierz **przełączyć się do kontenerów Windows...**  lub **przełączyć się do kontenerów systemu Linux...** .

## <a name="unable-to-start-debugging"></a>Nie można uruchomić debugowania

Jedną z przyczyn może być związany z mających nieaktualne składniki debugowania w folderze profilu użytkownika. Wykonaj następujące polecenia, aby usunąć te foldery, aby składniki najnowsza wersja debugowania są pobierane w następnej sesji debugowania.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Błędy specyficzne dla sieci podczas debugowania aplikacji

Spróbuj wykonywanie skryptu do pobrania z [oczyszczania kontenera hosta sieci](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), która będzie odświeżać składników związanych z siecią na maszynie hosta.

## <a name="mounts-denied"></a>Instaluje odmowa

Korzystając z platformy Docker dla systemu macOS, może wystąpić błąd odwołujące się do /usr/local/share/dotnet/sdk/NuGetFallbackFolder folderu. Dodaj folder do karty Udostępnianie plików na platformie Docker

## <a name="docker-users-group"></a>Grupa użytkowników platformy docker

Może wystąpić następujący błąd w programie Visual Studio, podczas pracy z kontenerami:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Musi być członkiem grupy "docker użytkownicy", aby mogła mieć uprawnienia do pracy z kontenerami aparatu Docker.  Aby dodać użytkownika do grupy w systemie Windows 10, wykonaj następujące kroki:

1. Z Start menu, otwórz **Zarządzanie komputerem**.
1. Rozwiń **lokalnych użytkowników i grup**i wybierz polecenie **grup**.
1. Znajdź **użytkowników platformy docker** grupy, kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj do grupy**.
1. Dodaj swoje konto użytkownika lub konta.
1. Wyloguj się i zalogować ponownie te zmiany zaczęły obowiązywać.

Można również użyć `net localgroup` polecenie w wierszu polecenia administratora, aby dodać użytkowników do określonych grup.

```cmd
net localgroup docker-users DOMAIN\username /add
```

W programie PowerShell użyj [LocalGroupMember Dodaj](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) funkcji.

## <a name="microsoftdockertools-github-repo"></a>Repozytorium GitHub Microsoft/DockerTools

Aby uzyskać inne problemy wystąpią, zobacz [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) problemów.