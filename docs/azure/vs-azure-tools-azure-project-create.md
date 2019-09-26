---
title: Tworzenie projektu usługi w chmurze platformy Azure
description: Dowiedz się teraz, jak utworzyć projekt usługi w chmurze platformy Azure z programem Visual Studio
author: ghogen
manager: jillfra
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: 722c816329c70bb2efad03f9554e201bcc9fde16
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253473"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>Tworzenie projektu usługi w chmurze platformy Azure za pomocą programu Visual Studio

Azure Tools dla programu Visual Studio zawiera szablon projektu umożliwiający tworzenie [usłudze w chmurze Azure](/azure/cloud-services/cloud-services-choose-me), który jest prostą usługę Azure ogólnego przeznaczenia. Po utworzeniu projektu programu Visual Studio pozwala konfigurować, debugować i wdrożyć usługę w chmurze na platformie Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Kroki, aby utworzyć projekt usługi w chmurze platformy Azure w programie Visual Studio
Ta sekcja przeprowadzi Cię przez tworzenie projektu usługi w chmurze platformy Azure w programie Visual Studio za pomocą co najmniej jedną rolę sieci web.

::: moniker range="vs-2017"
1. Otwórz program Visual Studio jako administrator.

1. W menu głównym wybierz pozycję **plik** > **Nowy** > **projekt**.

1. Wybierz **chmury** z Visual C# lub Visual Basic projektu węzłów szablonu, a następnie wybierz **usługa w chmurze** z listy szablonów.

    ![Nowa usługa w chmurze platformy Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Określenie, która wersja programu .NET Framework, którego chcesz użyć do tworzenia projektu.

1. Wprowadź nazwę i lokalizację projektu i nazwę rozwiązania.

1. Kliknij przycisk **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

1. W polu wyszukiwania wpisz ciąg w *chmurze*, a następnie wybierz pozycję **Usługa w chmurze platformy Azure**.

   ![Nowa usługa w chmurze platformy Azure](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. Nadaj projektowi nazwę i wybierz pozycję **Utwórz**.

   ![Nadaj nazwę projektowi](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. W **nową usługę w chmurze Azure Microsoft** okno dialogowe, wybierz role, które chcesz dodać, a następnie wybierz przycisk strzałki w prawo, aby dodać je do swojego rozwiązania.

    ![Wybierz nowy ról usługi w chmurze platformy Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Aby zmienić nazwę roli, które zostały dodane, umieść kursor na rolę w **nową usługę w chmurze Azure Microsoft** okno dialogowe i z menu kontekstowego wybierz **Zmień nazwę**. Można również zmienić nazwę roli w ramach rozwiązania usługi (w **Eksploratora rozwiązań**) po został dodany.

    ![Zmień nazwę roli usługi w chmurze platformy Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Projekt programu Visual Studio na platformie Azure ma skojarzenia z projektów ról w rozwiązaniu. Zawiera także projekt *pliku definicji usługi* i *pliku konfiguracji usługi*:

- **Plik definicji usługi** — definiuje ustawienia czasu wykonywania dla aplikacji, w tym informacje o wymaganych rolach, punktach końcowych i rozmiarze maszyny wirtualnej.
- **Plik konfiguracji usługi** -Określa, ile wystąpień roli są wykonywania i wartości ustawienia zdefiniowane dla roli.

Aby uzyskać więcej informacji o tych plikach, zobacz [konfigurowania ról usługi w chmurze platformy Azure z programem Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Następne kroki
- [Zarządzanie rolami w projekty usługi w chmurze platformy Azure z programem Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
