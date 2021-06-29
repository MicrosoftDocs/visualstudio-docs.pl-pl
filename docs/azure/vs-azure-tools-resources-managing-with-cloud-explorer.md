---
title: Zarządzanie zasobami platformy Azure za pomocą programu Cloud Explorer | Microsoft Docs
description: Dowiedz się, jak używać eksploratora chmury do przeglądania zasobów platformy Azure i zarządzania nimi w Visual Studio.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: 08ccab99df40247390894aa53d5073a3aff0c561
ms.sourcegitcommit: b770b99034e65c91b29bea87bc6f5fa02348515b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2021
ms.locfileid: "112997660"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Zarządzanie zasobami skojarzonymi z kontami platformy Azure w narzędziu Visual Studio Cloud Explorer

::: moniker range=">=vs-2022"
> [!Important]
> Usługa Cloud Explorer została wycofana Visual Studio 2022 r. Zamiast tego można użyć następujących alternatyw:
> - Użyj [Eksplorator usługi Microsoft Azure Storage](/azure/vs-azure-tools-storage-manage-with-storage-explorer) to bezpłatna, autonomiczna aplikacja firmy Microsoft. Można jej używać do wizualnej pracy z danymi usługi Azure Storage w systemach Windows, macOS i Linux.
> - Konsola [Kudu zapewnia](https://github.com/projectkudu/kudu/wiki/Kudu-console) bezpośredni, podwyższony poziom uprawnień dostępu do serwera App Service i jego systemu plików. Jest to cenne narzędzie do debugowania i umożliwia operacje interfejsu wiersza polecenia, takie jak instalowanie pakietów.
>
> W razie potrzeby możesz użyć witryny Azure Portal lub nadal korzystać z węzła platformy Azure Eksplorator serwera poprzednich wersjach Visual Studio.
>
> Aby uzyskać więcej informacji na Visual Studio 2022, zobacz nasze informacje [o wersji](/visualstudio/releases/2022/release-notes-preview/).

::: moniker-end

::: moniker range="<=vs-2017"

Eksplorator chmury umożliwia wyświetlanie zasobów i grup zasobów platformy Azure, sprawdzanie ich właściwości oraz wykonywanie kluczowych akcji diagnostycznych dla deweloperów z poziomu Visual Studio.

Podobnie jak [Azure Portal](https://portal.azure.com), eksplorator chmury jest zbudowany na Azure Resource Manager stosie. W związku z tym eksplorator chmury rozumie zasoby, takie jak grupy zasobów platformy Azure i usługi platformy Azure, takie jak aplikacje logiki i aplikacje interfejsu API, i obsługuje kontrolę dostępu opartą na [rolach](/azure/role-based-access-control/role-assignments-portal) (RBAC).

## <a name="prerequisites"></a>Wymagania wstępne

* Visual Studio 2017 lub nowszy (zobacz [Visual Studio pobrania](https://visualstudio.microsoft.com/downloads)) z wybranym **obciążeniem platformy Azure.** Można również użyć starszej wersji programu Visual Studio z Zestaw Microsoft Azure SDK dla platformy .NET [2.9.](https://www.microsoft.com/download/details.aspx?id=51657)
* Microsoft Azure — jeśli nie masz konta, możesz zarejestrować [](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) się w celu korzystania z bezpłatnej wersji próbnej lub aktywować korzyści [Visual Studio subskrybenta.](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)

> [!NOTE]
> Aby wyświetlić eksplorator chmury, naciśnij **klawisze Ctrl** + **Q,** aby aktywować pole wyszukiwania, a następnie wprowadź wartość **Cloud Explorer**.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Dodawanie konta platformy Azure do eksploratora chmury

Aby wyświetlić zasoby skojarzone z kontem platformy Azure, należy najpierw dodać konto do **eksploratora chmury.**

1. W **eksploratorze chmury** wybierz przycisk **Zarządzanie kontami.**

   ![Ikona ustawień konta platformy Azure w usłudze Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Wybierz **pozycję Zarządzaj kontami.**

   ![Link do dodawania konta w programie Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Zaloguj się do konta platformy Azure, którego zasoby chcesz przeglądać.

1. Po zalogowaniu się do konta platformy Azure zostaną wyświetlone subskrypcje skojarzone z tym kontem. Zaznacz pola wyboru dla subskrypcji kont, które chcesz przeglądać, a następnie wybierz pozycję **Zastosuj.**

   ![Cloud Explorer: wybierz subskrypcje platformy Azure do wyświetlenia](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Po wybraniu subskrypcji, których zasoby chcesz przeglądać, te subskrypcje i zasoby są wyświetlane w **Eksploratorze chmury.**

   ![Lista zasobów programu Cloud Explorer dla konta platformy Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Usuwanie konta platformy Azure z eksploratora chmury

1. W **eksploratorze chmury** wybierz **pozycję Zarządzanie kontami.**

   ![Ustawienia konta platformy Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Obok konta, które chcesz usunąć, wybierz pozycję **Zarządzaj kontami.**

   ![Usuwanie konta](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Wybierz **pozycję Usuń,** aby usunąć konto.

    ![Okno dialogowe Zarządzanie kontami w programie Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Wyświetlanie typów zasobów lub grup zasobów

Aby wyświetlić zasoby platformy Azure, możesz wybrać widok **Typy zasobów** lub **Grupy** zasobów.

1. W **eksploratorze chmury** wybierz menu rozwijane widok zasobów.

   ![Lista rozwijana eksploratora chmury w celu wybrania widoku żądanych zasobów](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. Z menu kontekstowego wybierz żądany widok:

   * **Widok Typy** zasobów — wspólny widok używany w usłudze [Azure Portal](https://portal.azure.com)zawiera zasoby platformy Azure podzielone na kategorie według ich typu, takie jak aplikacje internetowe, konta magazynu i maszyny wirtualne.
   * **Widok Grupy** zasobów — kategoryzuje zasoby platformy Azure według grupy zasobów platformy Azure, z którą są skojarzone. Grupa zasobów to pakiet zasobów platformy Azure, zwykle używany przez określoną aplikację. Aby dowiedzieć się więcej na temat grup zasobów platformy Azure, [zobacz Azure Resource Manager Omówienie](/azure/azure-resource-manager/resource-group-overview).

   Na poniższej ilustracji przedstawiono porównanie dwóch widoków zasobów:

   ![Porównanie widoków zasobów usługi Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Wyświetlanie zasobów i nawigowanie po nich w eksploratorze chmury

Aby przejść do zasobu platformy Azure i wyświetlić jego informacje w Eksploratorze chmury, rozwiń typ elementu lub skojarzoną grupę zasobów, a następnie wybierz zasób. Po wybraniu zasobu informacje są wyświetlane na dwóch kartach — **Akcje** i **Właściwości** — w dolnej części eksploratora chmury.

* **Karta** Akcje — zawiera listę akcji, które można podjąć w Eksploratorze chmury dla wybranego zasobu. Możesz również wyświetlić te opcje, klikając prawym przyciskiem myszy zasób, aby wyświetlić jego menu kontekstowe.

* **Karta** Właściwości — zawiera właściwości zasobu, takie jak typ, ustawienia lokalne i grupa zasobów, z którą jest skojarzony.

Na poniższej ilustracji przedstawiono przykładowe porównanie tego, co widzisz na każdej karcie dla App Service:

  ![Zrzut ekranu przedstawiający eksploratora chmury](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Każdy zasób ma akcję **Otwórz w portalu**. Po wybraniu tej akcji eksplorator chmury wyświetli wybrany zasób w Azure Portal [.](https://portal.azure.com) Funkcja **Otwórz w portalu** jest przydatna do przechodzenia do głęboko zagnieżdżonych zasobów.

Dodatkowe akcje i wartości właściwości mogą być również wyświetlane na podstawie zasobu platformy Azure. Na przykład aplikacje internetowe i aplikacje logiki oprócz polecenia Otwórz w portalu mają również akcje **Otwórz** w przeglądarce i **Dołącz debuger.**  Akcje otwierania edytorów są wyświetlane po wybraniu obiektu blob, kolejki lub tabeli konta magazynu. Aplikacje platformy Azure mają **właściwości Adres URL** i **Stan,** a zasoby magazynu mają właściwości klucza i parametrów połączenia.

## <a name="find-resources-in-cloud-explorer"></a>Znajdowanie zasobów w Eksploratorze chmury

Aby zlokalizować zasoby o określonej nazwie w subskrypcjach konta platformy Azure, wprowadź nazwę w polu **Wyszukiwania** w **Eksploratorze chmury.**

  ![Znajdowanie zasobów w eksploratorze chmury](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

Po wprowadzeniu znaków w **polu Wyszukiwania** w drzewie zasobów są wyświetlane tylko te zasoby, które pasują do tych znaków.

::: moniker-end
