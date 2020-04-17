---
title: Tworzenie projektu usługi w chmurze platformy Azure
description: Dowiedz się teraz, jak utworzyć projekt usługi w chmurze platformy Azure za pomocą programu Visual Studio
author: ghogen
manager: jillfra
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: 23e2db0b42fb12872feb5942d9f4eeaab96d3c2d
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489756"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>Tworzenie projektu usługi w chmurze platformy Azure za pomocą programu Visual Studio

Visual Studio udostępnia szablon projektu, który umożliwia utworzenie [usługi w chmurze platformy Azure](/azure/cloud-services/cloud-services-choose-me), która jest prostą usługą ogólnego przeznaczenia platformy Azure. Po utworzeniu projektu program Visual Studio umożliwia konfigurowanie, debugowanie i wdrażanie usługi w chmurze na platformie Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Kroki tworzenia projektu usługi w chmurze platformy Azure w programie Visual Studio
W tej sekcji można zapoznać cię z tworzeniem projektu usługi w chmurze platformy Azure w programie Visual Studio z co najmniej jedną rolą sieci Web.

::: moniker range="vs-2017"
1. Otwórz program Visual Studio jako administrator.

1. W menu głównym wybierz polecenie **Plik** > **nowego** > **projektu**.

1. Wybierz **opcję Chmura** z węzłów szablonów projektu Visual C# lub Visual Basic i wybierz usługę **Azure Cloud Service** z listy szablonów.

    ![Nowa usługa w chmurze platformy Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Określ, której wersji programu .NET Framework ma zostać użyta do opracowania projektu.

1. Wprowadź nazwę i lokalizację projektu oraz nazwę rozwiązania.

1. Kliknij przycisk **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

1. W polu wyszukiwania wpisz w *chmurze*, a następnie wybierz pozycję **Usługa Azure Cloud Service**.

   ![Nowa usługa w chmurze platformy Azure](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. Nadaj projektowi nazwę i wybierz pozycję **Utwórz**.

   ![Nadaj projektowi nazwę](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. W oknie dialogowym **Nowa usługa w chmurze platformy Microsoft Azure** wybierz role, które chcesz dodać, i wybierz przycisk strzałki w prawo, aby dodać je do rozwiązania.

    ![Wybieranie nowych ról usługi w chmurze platformy Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Aby zmienić nazwę dodanej roli, umieść wskaźnik myszy na roli w oknie dialogowym **Nowa usługa w chmurze platformy Microsoft Azure,** a z menu kontekstowego wybierz polecenie **Zmień nazwę**. Można również zmienić nazwę roli w rozwiązaniu (w **Eksploratorze rozwiązań)** po jego dodaniu.

    ![Zmienianie nazwy roli usługi w chmurze platformy Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Projekt platformy Visual Studio Azure ma skojarzenia z projektami ról w rozwiązaniu. Projekt zawiera również *plik definicji usługi* i plik *konfiguracyjny usługi:*

- **Plik definicji usługi** — definiuje ustawienia czasu wykonywania aplikacji, w tym jakie role są wymagane, punkty końcowe i rozmiar maszyny wirtualnej.
- **Plik konfiguracji usługi** — konfiguruje liczbę wystąpień roli są uruchamiane i wartości ustawień zdefiniowanych dla roli.

Aby uzyskać więcej informacji na temat tych plików, zobacz [Konfigurowanie ról dla usługi w chmurze platformy Azure za pomocą programu Visual Studio.](vs-azure-tools-configure-roles-for-cloud-service.md)

## <a name="next-steps"></a>Następne kroki
- [Zarządzanie rolami w projektach usług w chmurze platformy Azure za pomocą programu Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
