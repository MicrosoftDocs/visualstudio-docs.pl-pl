---
title: Rozwiązywanie problemów z błędami klienta platformy Docker w systemie Windows | Microsoft Docs
description: Rozwiązywanie problemów występujących podczas korzystania z programu Visual Studio do tworzenia i wdrażania aplikacji sieci Web w systemie Windows przy użyciu programu Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 1f4ca9d53900d0dc0c2392296303a94121103158
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283115"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Rozwiązywanie problemów związanych z opracowywaniem zwartości w programie Visual Studio przy użyciu platformy Docker

Podczas pracy z narzędziami kontenera programu Visual Studio mogą wystąpić problemy podczas kompilowania lub debugowania aplikacji. Poniżej przedstawiono kilka typowych kroków rozwiązywania problemów.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Udostępnianie woluminów nie jest włączone. Włącz udostępnianie woluminów w ustawieniach Docker CE for Windows (tylko kontenery systemu Linux)

Aby rozwiązać ten problem:

1. Kliknij prawym przyciskiem myszy **Docker for Windows** w obszarze powiadomień, a następnie wybierz pozycję **Ustawienia**.
1. Wybierz pozycję **dyski udostępnione** i Udostępnij dysk systemowy wraz z dyskiem, na którym znajduje się projekt.

> [!NOTE]
> Jeśli pliki są udostępnione, nadal może być konieczne kliknięcie przycisku "Resetuj poświadczenia..." link w dolnej części okna dialogowego, aby ponownie włączyć udostępnianie woluminu. Aby kontynuować po zresetowaniu poświadczeń, może być konieczne ponowne uruchomienie programu Visual Studio.

![udostępnione dyski](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Program Visual Studio w wersji nowszej niż Visual Studio 2017 w wersji 15,6 wyświetla monit, gdy **dyski udostępnione** nie są skonfigurowane.

### <a name="container-type"></a>Typ kontenera

Podczas dodawania obsługi platformy Docker do projektu należy wybrać kontener systemu Windows lub Linux. Na hoście platformy Docker musi być uruchomiony ten sam typ kontenera. Aby zmienić typ kontenera w uruchomionym wystąpieniu platformy Docker, kliknij prawym przyciskiem myszy ikonę platformy Docker na pasku zadań i wybierz polecenie **Switch to Windows containers...** (Przełącz do kontenerów systemu Windows...) lub polecenie **Switch to Linux containers...** (Przełącz do kontenerów systemu Linux...).

## <a name="unable-to-start-debugging"></a>Nie można uruchomić debugowania

Jedną z przyczyn może być związek ze starymi składnikami debugowania w folderze profilu użytkownika. Wykonaj następujące polecenia, aby usunąć te foldery, aby najnowsze składniki debugowania były pobierane podczas następnej sesji debugowania.

- del%USERPROFILE%\vsdbg
- del%USERPROFILE%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Błędy specyficzne dla sieci podczas debugowania aplikacji

Spróbuj wykonać pobieranie skryptu z [sieci hostowania kontenerów oczyszczania](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), co spowoduje odświeżenie składników związanych z siecią na komputerze-hoście.

## <a name="mounts-denied"></a>Odmowa instalacji

W przypadku korzystania z platformy Docker for macOS może wystąpić błąd odwołujący się do folderu/usr/local/share/dotnet/sdk/NuGetFallbackFolder. Dodaj folder do karty Udostępnianie plików w programie Docker

## <a name="docker-users-group"></a>Grupa użytkowników platformy Docker

Podczas pracy z kontenerami w programie Visual Studio może wystąpić następujący błąd:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Aby mieć uprawnienia do pracy z kontenerami platformy Docker, musisz być członkiem grupy "Docker-users".  Aby dodać siebie do grupy w systemie Windows 10, wykonaj następujące kroki:

1. Z menu Start Otwórz pozycję **Zarządzanie komputerem**.
1. Rozwiń węzeł **lokalni użytkownicy i grupy**, a następnie wybierz pozycję **grupy**.
1. Znajdź grupę **Docker — użytkownicy** , kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj do grupy**.
1. Dodaj konto użytkownika lub konta.
1. Wyloguj się i zaloguj ponownie, aby te zmiany zaczęły obowiązywać.

Możesz również użyć `net localgroup` polecenia w wierszu polecenia administratora, aby dodać użytkowników do określonych grup.

```cmd
net localgroup docker-users DOMAIN\username /add
```

W programie PowerShell Użyj funkcji [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) .

## <a name="low-disk-space"></a>Mało miejsca na dysku

Domyślnie program Docker przechowuje obrazy w folderze *% ProgramData%/Docker/* , który zazwyczaj znajduje się na dysku systemowym * C:\ProgramData\Docker \* . Aby zapobiec wykorzystaniu przez obrazy cennego miejsca na dysku systemowym, można zmienić lokalizację folderu obrazu.  Z poziomu ikony platformy Docker na pasku zadań Otwórz ustawienia platformy Docker, wybierz **demon**i przejdź z warstwy **podstawowa** na **Zaawansowane**. W okienku Edycja Dodaj `graph` ustawienie właściwości z wartością żądanej lokalizacji obrazów platformy Docker:

```json
    "graph": "D:\\mypath\\images"
```

![Zrzut ekranu przedstawiający ustawienie lokalizacji obrazu platformy Docker](media/troubleshooting-docker-errors/docker-settings-image-location.png)

Kliknij przycisk **Zastosuj** , aby ponownie uruchomić platformę Docker. Te kroki modyfikują plik konfiguracyjny w lokalizacji *% ProgramData% \docker\config\daemon.jsna*. Poprzednio skompilowane obrazy nie są przenoszone.

## <a name="microsoftdockertools-github-repo"></a>Repozytorium GitHub firmy Microsoft/DockerTools

Aby poznać inne problemy, zobacz temat problemy z [programem Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) .