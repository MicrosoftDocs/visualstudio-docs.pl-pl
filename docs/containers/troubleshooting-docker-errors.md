---
title: Rozwiązywanie problemów z błędami klienta platformy Docker w systemie Windows | Microsoft Docs
description: Rozwiązywanie problemów, które można napotkać podczas używania Visual Studio do tworzenia i wdrażania aplikacji internetowych na potrzeby platformy Docker w systemie Windows przy użyciu Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jmartens
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 5f48b5c06e91b9c05e6edc7e2a1738aeb677a7ba
ms.sourcegitcommit: 69456d802203d21dabc3ae8662547a3241c24f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2021
ms.locfileid: "110235914"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Rozwiązywanie problemów związanych z opracowywaniem zwartości w programie Visual Studio przy użyciu platformy Docker

Podczas pracy z narzędziami kontenerów Visual Studio mogą wystąpić problemy podczas budowania lub debugowania aplikacji. Poniżej przedstawiono kilka typowych kroków rozwiązywania problemów.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Udostępnianie woluminów nie jest włączone. Włączanie udostępniania woluminów w ustawieniach Docker CE for Windows (tylko kontenery systemu Linux)

Udostępnianiem plików należy zarządzać tylko w przypadku korzystania z funkcji Hyper-V z platformą Docker. Jeśli używasz programu WSL 2, poniższe kroki nie są konieczne, a opcja udostępniania plików nie będzie widoczna. Aby rozwiązać ten problem:

1. Kliknij prawym przyciskiem **myszy Docker for Windows** w obszarze powiadomień, a następnie wybierz pozycję **Ustawienia.**
1. Wybierz **pozycję Udostępnianie** plików  >  **zasobów** i udostępnij folder, do którego należy uzyskać dostęp. Udostępnianie całego dysku systemowego jest możliwe, ale nie jest zalecane.

    :::image type="content" source="media//troubleshooting-docker-errors/docker-settings-image.png" alt-text="Dyski udostępnione":::

> [!TIP]
> Visual Studio wersjach nowszych niż Visual Studio 2017 w wersji 15.6 będzie wyświetlany monit, gdy dyski udostępnione **nie** są skonfigurowane.

## <a name="unable-to-start-debugging"></a>Nie można uruchomić debugowania

Jedną z przyczyn może być nieaktualne składniki debugowania w folderze profilu użytkownika. Wykonaj następujące polecenia, aby usunąć te foldery, aby najnowsze składniki debugowania zostały pobrane podczas następnej sesji debugowania.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Błędy specyficzne dla sieci podczas debugowania aplikacji

Spróbuj wykonać skrypt do pobrania z usługi [Cleanup Container Host Networking](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), co spowoduje odświeżenie składników związanych z siecią na maszynie hosta.

## <a name="mounts-denied"></a>Odmowa instalacji

Podczas korzystania z platformy Docker dla systemu macOS może wystąpić błąd odwołujący się do folderu /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Dodaj folder do karty Udostępnianie plików na platformie Docker.

## <a name="docker-users-group"></a>Grupa użytkowników platformy Docker

Podczas pracy z kontenerami może wystąpić następujący błąd Visual Studio kontenerów:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Aby mieć uprawnienia do pracy z kontenerami platformy Docker, musisz być członkiem grupy "docker-users".  Aby dodać siebie do grupy w Windows 10, wykonaj następujące kroki:

1. Na stronie menu Start Zarządzanie **komputerem.**
1. Rozwiń **pozycję Użytkownicy i grupy lokalne,** a następnie wybierz pozycję **Grupy.**
1. Znajdź **grupę docker-users,** kliknij prawym przyciskiem myszy i wybierz **polecenie Dodaj do grupy.**
1. Dodaj swoje konto użytkownika lub konta.
1. Wyloguj się i zaloguj się ponownie, aby te zmiany weszły w życie.

Można również użyć polecenia `net localgroup` w wierszu polecenia administratora, aby dodać użytkowników do określonych grup.

```cmd
net localgroup docker-users DOMAIN\username /add
```

W programie PowerShell użyj [funkcji Add-LocalGroupMember.](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember)

## <a name="low-disk-space"></a>Mała ilość miejsca na dysku

Domyślnie docker przechowuje obrazy w *folderze %ProgramData%/Docker/,* który zazwyczaj znajduje się na dysku systemowym * C:\ProgramData\Docker \* . Aby uniemożliwić obrazom zajmuje cenne miejsce na dysku systemowym, można zmienić lokalizację folderu obrazu. W tym celu:

 1. Kliknij prawym przyciskiem myszy ikonę platformy Docker na pasku zadań i wybierz pozycję **Ustawienia.**
 1. Wybierz **pozycję Aparat platformy Docker.** 
 1. W okienku edycji dodaj ustawienie właściwości z wartością `graph` żądanej lokalizacji dla obrazów platformy Docker:

```json
    "graph": "D:\\mypath\\images"
```

:::image type="content" source="media/troubleshooting-docker-errors/docker-daemon-settings.png" alt-text="Zrzut ekranu przedstawiający udostępnianie plików platformy Docker":::

Kliknij **przycisk Zastosuj & uruchom ponownie.** Te kroki modyfikują plik konfiguracji w *%ProgramData%\docker\config\daemon.jsna*. Wcześniej sbudowaną obrazy nie są przenoszone.

## <a name="container-type-mismatch"></a>Niezgodność typów kontenerów

Podczas dodawania obsługi platformy Docker do projektu należy wybrać kontener systemu Windows lub Linux. Jeśli host serwera platformy Docker nie jest skonfigurowany do uruchamiania tego samego typu kontenera co obiekt docelowy projektu, prawdopodobnie zostanie wyświetlony błąd podobny do poniższego:

:::image type="content" source="media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png" alt-text="Zrzut ekranu przedstawiający niezgodność hosta platformy Docker i projektu":::

Aby rozwiązać ten problem:

- Kliknij prawym przyciskiem myszy ikonę Docker for Windows na pasku zadań i wybierz polecenie Przełącz do kontenerów systemu **Windows...** lub Przełącz **na kontenery systemu Linux...**.

## <a name="microsoftdockertools-github-repo"></a>Repozytorium GitHub Microsoft/DockerTools

W przypadku innych napotkanych problemów zobacz [Microsoft/DockerTools issues (Problemy z narzędziami Microsoft/DockerTools).](https://github.com/microsoft/dockertools/issues)

## <a name="see-also"></a>Zobacz też

- [Visual Studio rozwiązywania problemów](/troubleshoot/visualstudio/welcome-visual-studio/)
