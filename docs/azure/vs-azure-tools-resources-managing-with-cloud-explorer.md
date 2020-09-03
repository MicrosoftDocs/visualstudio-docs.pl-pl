---
title: Zarządzanie zasobami platformy Azure za pomocą programu Cloud Explorer | Microsoft Docs
description: Dowiedz się, jak przeglądać zasoby platformy Azure w programie Visual Studio i zarządzać nimi za pomocą programu Cloud Explorer.
author: ghogen
manager: jillfra
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: 175aa7111d77e92fb29a3983db7365e068abba2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800388"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Zarządzanie zasobami skojarzonymi z kontami platformy Azure w narzędziu Visual Studio Cloud Explorer

W programie Cloud Explorer można wyświetlać zasoby platformy Azure i grupy zasobów, sprawdzać ich właściwości oraz wykonywać kluczowe akcje diagnostyki deweloperów w programie Visual Studio.

Podobnie jak [Azure Portal](https://portal.azure.com), Eksplorator chmury jest oparty na stosie Azure Resource Manager. W związku z tym program Cloud Explorer rozumie zasoby, takie jak grupy zasobów platformy Azure i usługi platformy Azure, takie jak aplikacje logiki i aplikacje API Apps, a także obsługuje [kontrolę dostępu opartą na rolach](/azure/role-based-access-control/role-assignments-portal) (RBAC).

## <a name="prerequisites"></a>Wymagania wstępne

* Program Visual Studio 2017 lub nowszy (zobacz [pliki do pobrania w programie Visual Studio](https://visualstudio.microsoft.com/downloads)) z wybranym **obciążeniem platformy Azure** . Możesz również użyć wcześniejszej wersji programu Visual Studio z [Zestaw Microsoft Azure SDK dla platformy .NET 2,9](https://www.microsoft.com/download/details.aspx?id=51657).
* Konto Microsoft Azure — Jeśli nie masz konta, możesz [zarejestrować się w celu uzyskania bezpłatnej wersji próbnej](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) lub [aktywować korzyści dla subskrybentów programu Visual Studio](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).

> [!NOTE]
> Aby wyświetlić program Cloud Explorer, naciśnij **kombinację klawiszy CTRL** + **Q** , aby uaktywnić pole wyszukiwania, a następnie przejdź do **Eksploratora chmury**.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Dodawanie konta platformy Azure do programu Cloud Explorer

Aby wyświetlić zasoby skojarzone z kontem platformy Azure, musisz najpierw dodać to konto do programu **Cloud Explorer**.

1. W programie **Cloud Explorer**wybierz przycisk **Zarządzanie kontem** .

   ![Ikona ustawień konta platformy Azure w programie Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Wybierz pozycję **Zarządzaj kontami**.

   ![Link do dodawania konta w programie Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Zaloguj się do konta platformy Azure, którego zasoby chcesz przeglądać.

1. Po zalogowaniu się do konta platformy Azure są wyświetlane subskrypcje skojarzone z tym kontem. Zaznacz pola wyboru dla subskrypcji konta, które chcesz przeglądać, a następnie wybierz pozycję **Zastosuj**.

   ![Eksplorator chmury: wybierz subskrypcje platformy Azure do wyświetlenia](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Po wybraniu subskrypcji, których zasobów chcesz przeglądać, te subskrypcje i zasoby są wyświetlane w programie **Cloud Explorer**.

   ![Lista zasobów w programie Cloud Explorer dla konta platformy Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Usuwanie konta platformy Azure z poziomu programu Cloud Explorer

1. W programie **Cloud Explorer**wybierz pozycję **Zarządzanie kontem**.

   ![Ikona ustawień konta platformy Azure w programie Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Obok konta, które chcesz usunąć, wybierz pozycję **Zarządzaj kontami**.

   ![Ikona ustawień konta platformy Azure w programie Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Wybierz pozycję **Usuń** , aby usunąć konto.

    ![Okno dialogowe Zarządzanie kontami w programie Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Wyświetlanie typów zasobów lub grup zasobów

Aby wyświetlić zasoby platformy Azure, możesz wybrać opcję **typy zasobów** lub widok **grup zasobów** .

1. W programie **Cloud Explorer**wybierz listę rozwijaną widok zasobów.

   ![Lista rozwijana programu Cloud Explorer, aby wybrać widok żądanych zasobów](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. Z menu kontekstowego wybierz odpowiedni widok:

   * Widok **typów zasobów** — typowy widok używany na [Azure Portal](https://portal.azure.com), pokazuje zasoby platformy Azure pogrupowane według ich typu, takich jak aplikacje sieci Web, konta magazynu i maszyny wirtualne.
   * Widok **grup zasobów** — umożliwia kategoryzowanie zasobów platformy Azure według grupy zasobów platformy Azure, z którą są skojarzone. Grupa zasobów to pakiet zasobów platformy Azure, zwykle używany przez określoną aplikację. Aby dowiedzieć się więcej na temat grup zasobów platformy Azure, zobacz [Azure Resource Manager przegląd](/azure/azure-resource-manager/resource-group-overview).

   Na poniższej ilustracji przedstawiono porównanie dwóch widoków zasobów:

   ![Porównanie widoków zasobów w programie Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Wyświetlanie zasobów i nawigowanie w programie Cloud Explorer

Aby przejść do zasobu platformy Azure i wyświetlić jego informacje w programie Cloud Explorer, rozwiń typ elementu lub powiązanej grupy zasobów, a następnie wybierz zasób. Po wybraniu zasobu informacje są wyświetlane na karcie dwie karty — **Akcje** i **Właściwości** — w dolnej części Eksploratora chmury.

* Karta **Akcje** — zawiera listę akcji, które można wykonać w programie Cloud Explorer dla wybranego zasobu. Możesz również wyświetlić te opcje, klikając prawym przyciskiem myszy zasób, aby wyświetlić jego menu kontekstowe.

* Karta **Właściwości** — pokazuje właściwości zasobu, takie jak jego typ, ustawienia regionalne i Grupa zasobów, z którą jest skojarzona.

Na poniższej ilustracji przedstawiono przykładowe porównanie zawartości widocznej na każdej karcie dla App Service:

  ![Zrzut ekranu programu Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Każdy zasób ma **otwartą akcję w portalu**. Po wybraniu tej akcji w programie Cloud Explorer zostanie wyświetlony wybrany zasób z [Azure Portal](https://portal.azure.com). Funkcja **Otwórz w portalu** jest przydatna do przechodzenia do głęboko zagnieżdżonych zasobów.

Dodatkowe akcje i wartości właściwości mogą być również wyświetlane na podstawie zasobu platformy Azure. Na przykład aplikacje sieci Web i Aplikacje logiki również mają otwarte akcje **w przeglądarce** i **Dołącz debuger** oprócz **otwartych w portalu**. Akcje otwierania edytorów są wyświetlane po wybraniu obiektu BLOB, kolejki lub tabeli konta magazynu. Aplikacje platformy Azure mają właściwości **adresu URL** i **stanu** , natomiast zasoby magazynu mają właściwości klucza i parametrów połączenia.

## <a name="find-resources-in-cloud-explorer"></a>Znajdowanie zasobów w programie Cloud Explorer

Aby zlokalizować zasoby z określoną nazwą w ramach subskrypcji konta platformy Azure, wprowadź nazwę w polu **wyszukiwania** w programie **Cloud Explorer**.

  ![Znajdowanie zasobów w programie Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

Po wprowadzeniu znaków w polu **wyszukiwania** tylko zasoby, które pasują do tych znaków, są wyświetlane w drzewie zasobów.
