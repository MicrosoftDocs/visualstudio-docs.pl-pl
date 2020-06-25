---
title: Tworzenie projektu usługi w chmurze platformy Azure
description: Dowiedz się teraz, jak utworzyć projekt usługi w chmurze platformy Azure za pomocą programu Visual Studio
author: ghogen
manager: jillfra
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: ef5acada89d48ed91dbf5b0f5fe7c9801337d47f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280378"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>Tworzenie projektu usługi w chmurze platformy Azure za pomocą programu Visual Studio

Program Visual Studio udostępnia szablon projektu, który umożliwia tworzenie [usługi w chmurze platformy Azure](/azure/cloud-services/cloud-services-choose-me), która jest prostą usługą platformy Azure ogólnego przeznaczenia. Po utworzeniu projektu program Visual Studio umożliwia skonfigurowanie, debugowanie i wdrożenie usługi w chmurze na platformie Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Procedura tworzenia projektu usługi w chmurze platformy Azure w programie Visual Studio
W tej sekcji omówiono tworzenie projektu usługi w chmurze platformy Azure w programie Visual Studio z co najmniej jedną rolą sieci Web.

::: moniker range="vs-2017"
1. Otwórz program Visual Studio jako administrator.

1. W menu głównym wybierz pozycję **plik** > **Nowy** > **projekt**.

1. Wybierz pozycję **chmura** z węzłów szablonu projektu Visual C# lub Visual Basic, a następnie wybierz pozycję **Usługa w chmurze platformy Azure** z listy szablonów.

    ![Nowa usługa w chmurze platformy Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Określ wersję .NET Framework, która ma zostać użyta do opracowania projektu.

1. Wprowadź nazwę i lokalizację projektu oraz nazwę rozwiązania.

1. Wybierz przycisk **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

1. W polu wyszukiwania wpisz ciąg w *chmurze*, a następnie wybierz pozycję **Usługa w chmurze platformy Azure**.

   ![Nowa usługa w chmurze platformy Azure](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. Nadaj projektowi nazwę i wybierz pozycję **Utwórz**.

   ![Nadaj nazwę projektowi](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. W oknie dialogowym **Nowa usługa w chmurze Microsoft Azure** wybierz role, które chcesz dodać, a następnie wybierz przycisk strzałki w prawo, aby dodać je do rozwiązania.

    ![Wybierz nowe role usługi w chmurze platformy Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Aby zmienić nazwę dodanej roli, umieść wskaźnik myszy na roli w oknie dialogowym **nowa Microsoft Azure usługa w chmurze** , a następnie z menu kontekstowego wybierz polecenie **Zmień nazwę**. Możesz również zmienić nazwę roli w rozwiązaniu (w **Eksplorator rozwiązań**) po dodaniu.

    ![Zmień nazwę roli usługi w chmurze platformy Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Projekt programu Visual Studio Azure ma skojarzenia z projektami ról w rozwiązaniu. Projekt zawiera również plik *definicji usługi* i *plik konfiguracji usługi*:

- **Plik definicji usługi** — definiuje ustawienia czasu wykonywania dla aplikacji, w tym informacje o wymaganych rolach, punktach końcowych i rozmiarze maszyny wirtualnej.
- **Plik konfiguracji usługi** — określa, ile wystąpień roli jest uruchomionych i wartości ustawień zdefiniowanych dla roli.

Aby uzyskać więcej informacji o tych plikach, zobacz [Konfigurowanie ról dla usługi w chmurze platformy Azure za pomocą programu Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Następne kroki
- [Zarządzanie rolami w projektach usług w chmurze platformy Azure za pomocą programu Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
