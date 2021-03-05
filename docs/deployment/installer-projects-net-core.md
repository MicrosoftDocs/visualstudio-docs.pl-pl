---
description: Pakowanie aplikacji jako MSI jest często realizowane przy użyciu rozszerzenia projektów Instalator programu Visual Studio.
title: Projekty Instalator programu Visual Studio i .NET Core 3,1
titleSuffix: ''
ms.date: 08/18/2020
ms.topic: conceptual
helpviewer_keywords:
- installer projects
- installer projects, .NETCore
author: MSLukeWest
ms.author: lukewest
manager: MSLukeWest
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 5a78c1cf4f7b1562408e0a3fb598075f2c114fc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171243"
---
# <a name="visual-studio-installer-projects-extension-and-net-core-31"></a>Rozszerzenie projektów instalatora programu Visual Studio i platforma .NET Core 3.1

Pakowanie aplikacji jako MSI jest często realizowane przy użyciu rozszerzenia projektów Instalator programu Visual Studio.

Możesz pobrać rozszerzenie tutaj: [projekty Instalator programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects)

## <a name="update-for-net-core"></a>Aktualizacja dla platformy .NET Core
Platforma .NET Core ma dwa różne modele do opublikowania.

- Wdrożenia zależne od platformy

- Aplikacje samodzielne obejmują środowisko uruchomieniowe.

Aby dowiedzieć się więcej na temat tych strategii wdrażania, zobacz [Omówienie publikowania aplikacji .NET Core](/dotnet/core/deploying/).

### <a name="workflow-changes-for-net-core-31"></a>Zmiany przepływu pracy dla programu .NET Core 3,1

1. Wybierz pozycję **Publikuj elementy** zamiast **podstawowych danych wyjściowych** , aby uzyskać prawidłowe dane wyjściowe dla projektów platformy .NET Core 3,1.  Aby wyświetlić to okno dialogowe, wybierz pozycję **Dodaj**  >  **dane wyjściowe projektu...** z menu kontekstowego projektu.

    ![Grupa wyjściowa Publikuj elementy w oknie dialogowym Dodaj grupę wyjściową projektu](../deployment/media/installer-projects-net-core-publish-items-output.png "Wybierz elementy do opublikowania")

2. Aby utworzyć samodzielny Instalator, należy ustawić właściwość **PublishProfilePath** w węźle **Publish Items** w projekcie instalacyjnym, używając ścieżki względnej profilu publikacji z prawidłowym zestawem właściwości.

    ![Ustawianie profilu publikowania dla elementu wyjściowego projektu Opublikuj elementy](../deployment/media/installer-projects-net-core-publish-profile.png "Ustaw profil publikowania")

### <a name="prerequisites-for-net-core-31"></a>Wymagania wstępne dotyczące programu .NET Core 3,1

Jeśli chcesz, aby Instalator mógł zainstalować niezbędne środowisko uruchomieniowe dla aplikacji .NET Core 3,1 zależnej od platformy, możesz to zrobić przy użyciu [wymagań wstępnych](../deployment/application-deployment-prerequisites.md).  W oknie dialogowym właściwości projektu Instalatora Otwórz okno dialogowe **wymagania wstępne...** , a zobaczysz następujące pozycje:

![Elementy .NET Core w oknie dialogowym wymagania wstępne](../deployment/media/installer-projects-net-core-prerequisites.png "Wymagania wstępne dotyczące platformy .NET Core")

Należy wybrać opcję **środowiska uruchomieniowego .NET Core...** dla aplikacji konsolowych, **środowisko uruchomieniowe programu .NET Desktop...** powinno zostać wybrane dla aplikacji WPF/WinForms.

>[!NOTE]
>Te elementy są obecne od wersji programu Visual Studio 2019 Update 7.

## <a name="see-also"></a>Zobacz też

- [Wstępnie wymagane składniki — Okno dialogowe](../ide/reference/prerequisites-dialog-box.md)
- [Wymagania wstępne dotyczące wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)
