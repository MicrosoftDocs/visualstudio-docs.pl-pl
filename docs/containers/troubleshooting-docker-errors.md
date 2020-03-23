---
title: Rozwiązywanie problemów z błędami klienta platformy Docker w systemie Windows | Dokumenty firmy Microsoft
description: Rozwiązywanie problemów napotkanych podczas tworzenia i wdrażania aplikacji sieci Web w programie Docker w systemie Windows przy użyciu programu Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: d8aa3028a12bcfb49f2663b2bea688baf14fd7f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027280"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Rozwiązywanie problemów związanych z opracowywaniem zwartości w programie Visual Studio przy użyciu platformy Docker

Podczas pracy z narzędziami kontenerów programu Visual Studio mogą wystąpić problemy podczas tworzenia lub debugowania aplikacji. Poniżej znajduje się kilka typowych kroków rozwiązywania problemów.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Udostępnianie woluminów nie jest włączone. Włączanie udostępniania woluminów w ustawieniach platformy Docker CE dla systemu Windows (tylko kontenery systemu Linux)

Aby rozwiązać ten problem:

1. Kliknij prawym przyciskiem myszy pozycję **Docker for Windows** w obszarze powiadomień, a następnie wybierz polecenie **Ustawienia**.
1. Wybierz **pozycję Dyski udostępnione** i udostępnij dysk systemowy wraz z dyskiem, na którym znajduje się projekt.

> [!NOTE]
> Jeśli pliki są udostępniane, może być konieczne kliknięcie przycisku "Resetuj poświadczenia..." w dolnej części okna dialogowego w celu ponownego włączenia udostępniania woluminów. Aby kontynuować po zresetowaniu poświadczeń, może być konieczne ponowne uruchomienie programu Visual Studio.

![dyski współdzielone](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Wersje programu Visual Studio później niż visual studio 2017 w wersji 15.6 monit, gdy **dyski udostępnione** nie są skonfigurowane.

### <a name="container-type"></a>Typ kontenera

Podczas dodawania do projektu docker, należy wybrać kontener systemu Windows lub linux. Na hoście platformy Docker musi być uruchomiony ten sam typ kontenera. Aby zmienić typ kontenera w uruchomionym wystąpieniu platformy Docker, kliknij prawym przyciskiem myszy ikonę platformy Docker na pasku zadań i wybierz polecenie **Switch to Windows containers...** (Przełącz do kontenerów systemu Windows...) lub polecenie **Switch to Linux containers...** (Przełącz do kontenerów systemu Linux...).

## <a name="unable-to-start-debugging"></a>Nie można uruchomić debugowania

Jednym z powodów może być związane z konieczności starych składników debugowania w folderze profilu użytkownika. Wykonaj następujące polecenia, aby usunąć te foldery, tak aby najnowsze składniki debugowania były pobierane w następnej sesji debugowania.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Błędy specyficzne dla sieci podczas debugowania aplikacji

Spróbuj wykonać skrypt do pobrania z [usługi Cleanup Container Host Networking,](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking)który odświeży składniki związane z siecią na komputerze-hoście.

## <a name="mounts-denied"></a>Wierzchowce odrzucone

Podczas korzystania z platformy Docker dla systemu macOS może wystąpić błąd odwołujący się do folderu /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Dodawanie folderu do karty Udostępnianie plików w aplikacji Docker

## <a name="docker-users-group"></a>Grupa Użytkownicy platformy Docker

Podczas pracy z kontenerami może wystąpić następujący błąd:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Aby mieć uprawnienia do pracy z kontenerami platformy Docker, musisz być członkiem grupy "docker-users".  Aby dodać się do grupy w systemie Windows 10, wykonaj następujące kroki:

1. W menu Start otwórz **pozycję Zarządzanie komputerem**.
1. Rozwiń **pozycję Użytkownicy i grupy lokalne**i wybierz pozycję **Grupy**.
1. Znajdź grupę **docker-users,** kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj do grupy**.
1. Dodaj swoje konto użytkownika lub konta.
1. Wyloguj się i zaloguj ponownie, aby te zmiany weszły w życie.

Można również użyć `net localgroup` polecenia w wierszu polecenia Administrator, aby dodać użytkowników do określonych grup.

```cmd
net localgroup docker-users DOMAIN\username /add
```

W programie PowerShell należy użyć funkcji [Add-LocalGroupMember.](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember)

## <a name="low-disk-space"></a>Mało miejsca na dysku

Domyślnie program Docker przechowuje obrazy w folderze *%ProgramData%/Docker/,* który zazwyczaj znajduje się na\*dysku systemowym, *C:\ProgramData\Docker . Aby zapobiec zajmowaniu cennego miejsca na dysku systemowym przez obrazy, można zmienić lokalizację folderu obrazów.  Z ikony Platformy Docker na pasku zadań otwórz ustawienia platformy Docker, wybierz polecenie **Demon**i przełącz się z **podstawowego** na **zaawansowany**. W okienku edycji dodaj `graph` ustawienie właściwości z wartością żądanej lokalizacji obrazów platformy Docker:

```json
    "graph": "D:\\mypath\\images"
```

![Zrzut ekranu przedstawiający ustawienie lokalizacji obrazu platformy Docker](media/troubleshooting-docker-errors/docker-settings-image-location.png)

Kliknij **przycisk Zastosuj,** aby ponownie uruchomić program Docker. W tych krokach zmodyfikowano plik konfiguracyjny w *pliku %ProgramData%\docker\config\daemon.json*. Wcześniej utworzone obrazy nie są przenoszone.

## <a name="microsoftdockertools-github-repo"></a>Repozytorium GitHub firmy Microsoft/DockerTools

Aby uzyskać inne problemy, które napotkasz, zobacz [Problemy z microsoft/dockerTools.](https://github.com/microsoft/dockertools/issues)