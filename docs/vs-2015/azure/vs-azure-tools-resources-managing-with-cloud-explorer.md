---
title: Zarządzanie zasobami platformy Azure za pomocą Eksploratora chmury | Dokumentacja firmy Microsoft
description: Dowiedz się, jak za pomocą Eksploratora chmury do przeglądania i zarządzania zasobami platformy Azure w programie Visual Studio.
author: ghogen
manager: jillfra
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: 25995eacc961474fcb6486668c918d2e5be5ba76
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779703"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Zarządzanie zasobami skojarzonymi z kontami platformy Azure w narzędziu Visual Studio Cloud Explorer

Eksplorator chmury umożliwia wyświetlanie zasobów platformy Azure i grup zasobów, badania ich właściwości i akcje klucza dewelopera diagnostyki z poziomu programu Visual Studio.

Podobnie jak [witryny Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040), Cloud Explorer jest oparta na stosie usługi Azure Resource Manager. W związku z tym, rozumie Eksploratora chmury, zasoby, takie jak grupy zasobów platformy Azure i usług platformy Azure, takich jak Logic apps i API apps i obsługuje [kontroli dostępu opartej na rolach](/azure/role-based-access-control/role-assignments-portal) (RBAC).

## <a name="prerequisites"></a>Wymagania wstępne

* Visual Studio 2015 z [platformy Microsoft Azure SDK dla platformy .NET 2.9](https://www.microsoft.com/download/details.aspx?id=51657).
* Konto Microsoft Azure — Jeśli nie masz konta, możesz to zrobić [utworzyć konto bezpłatnej wersji próbnej](http://go.microsoft.com/fwlink/?LinkId=623901) lub [aktywować korzyści dla subskrybentów programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=623901).

> [!NOTE]
> Zaznacz, aby wyświetlić Eksplorator chmury **widoku** > **programu Cloud Explorer** na pasku menu.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Dodaj platformę Azure konta do Eksploratora chmury

Aby wyświetlić zasoby skojarzone z kontem platformy Azure, musisz dodać konto do programu Cloud Explorer.

1. W **programu Cloud Explorer**, wybierz opcję **ustawienia konta platformy Azure**.

   ![Ikona ustawień konta Azure Eksploratora chmury](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Wybierz **Zarządzanie kontami**.

   ![Łącze Dodaj konto Eksploratora chmury](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Zaloguj się do konta platformy Azure zasoby, których chcesz przeglądać.

1. Po zalogowaniu się do konta platformy Azure, Wyświetl subskrypcje skojarzone z tym kontem. Zaznacz pole wyboru dla subskrypcji konta, aby przejrzeć i wybrać pozycję **Zastosuj**.

   ![Eksplorator chmury: Wybierz subskrypcję platformy Azure do wyświetlenia](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Po wybraniu subskrypcji, którego zasoby, które chcesz przeglądać, te subskrypcje i zasoby są wyświetlane w programie Cloud Explorer.

   ![Eksplorator zasobów dla konta platformy Azure w chmurze](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Usuń konto platformy Azure z Eksploratora chmury

1. W **programu Cloud Explorer**, wybierz opcję **zarządzania kontami**.

   ![Ikona ustawień konta Azure Eksploratora chmury](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Obok konto, którego chcesz usunąć, wybierz **Zarządzanie kontami**.

   ![Ikona ustawień konta Azure Eksploratora chmury](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Wybierz **Usuń** w celu usunięcia konta.

    ![Okno dialogowe konta zarządzania Eksploratora chmury](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Wyświetlanie typów zasobów lub grupy zasobów

Aby wyświetlić zasoby platformy Azure, możesz wybrać dowolną **typów zasobów** lub **grup zasobów** widoku.

1. W **programu Cloud Explorer**, wybierz listę rozwijaną widoku zasobów.

   ![Listę rozwijaną Eksploratora chmury, aby wybrać widok żądanych zasobów](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. Z menu kontekstowego wybierz żądany widok:

   * **Typy zasobów** view - typowy widok na [witryny Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040), pokazuje Twoich zasobów platformy Azure, pogrupowane według ich typu, na przykład aplikacje sieci web, kont magazynu i maszyn wirtualnych.
   * **Grupy zasobów** view - kategoryzuje zasobów platformy Azure przez grupę zasobów platformy Azure, z którymi są powiązane. Grupa zasobów to zbiór zasobów platformy Azure, zwykle używane przez określoną aplikację. Aby dowiedzieć się więcej na temat grup zasobów platformy Azure, zobacz [Omówienie usługi Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview).

   Na poniższej ilustracji przedstawiono porównanie widoki dwóch zasobów:

   ![Eksplorator zasobów widoków porównanie w chmurze](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Wyświetlanie i nawigowanie po zasobach w programie Cloud Explorer

Aby przejść do zasobu platformy Azure i wyświetlić informacje o nim w programie Cloud Explorer, rozwiń węzeł typu elementu lub skojarzonej grupy zasobów, a następnie wybierz zasób. Po wybraniu zasobu, informacje są wyświetlane w dwóch kart - **akcje** i **właściwości** — w dolnej części Eksploratora chmury.

* **Akcje** karcie — zawiera listę akcji może zająć się w Eksploratorze chmury dla wybranego zasobu. Te opcje można również wyświetlić, klikając prawym przyciskiem myszy zasób, aby wyświetlić jego menu kontekstowe.

* **Właściwości** karcie - Wyświetla właściwości zasobu, takie jak jego typ, ustawienia regionalne i grupę zasobów za pomocą którego jest skojarzony.

Na poniższej ilustracji przedstawiono przykład porównanie wyświetlanych na każdej karcie dla usługi App Service:

  ![Zrzut ekranu przedstawiający Eksploratora chmury](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Każdy zasób ma akcji **Otwórz w portalu**. W przypadku wybrania tej akcji, Cloud Explorer wyświetla wybranego zasobu w [witryny Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040). **Otwórz w portalu** funkcja jest przydatna do nawigowania do głęboko zagnieżdżonych zasobów.

Dodatkowe akcje i wartości właściwości mogą również zostać wyświetlony zależnie od zasobu platformy Azure. Na przykład aplikacje web apps i logic apps również mieć akcje **Otwórz w przeglądarce** i **dołączyć debuger** oprócz **Otwórz w portalu**. Operacje, aby otworzyć edytory są wyświetlane po wybraniu obiekt blob konta magazynu, kolejki lub tabeli. Aplikacje platformy Azure mają **adresu URL** i **stan** właściwości, gdy zasoby magazynu ma właściwości parametrów połączenia i klucz.

## <a name="find-resources-in-cloud-explorer"></a>Znajdź zasoby w Eksploratorze chmury

Aby znaleźć zasoby o określonej nazwie w Twoich subskrypcjach konta platformy Azure, wprowadź nazwę w **wyszukiwania** pola w programie Cloud Explorer.

  ![Znajdowanie zasobów w programie Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

Gdy wprowadzasz znaków **wyszukiwania** pole, tylko zasoby, które odpowiadają te znaki, które są wyświetlane w drzewie zasobów.
