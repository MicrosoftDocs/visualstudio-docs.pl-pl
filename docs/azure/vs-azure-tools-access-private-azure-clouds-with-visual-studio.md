---
title: Uzyskiwanie dostępu do prywatnych chmur platformy Azure
description: Dowiedz się, jak uzyskać dostęp do zasobów chmury prywatnej za pomocą programu Visual Studio.
author: ghogen
manager: jillfra
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 136c7f4f497c21de24e34c4c426707de94151ddf
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398738"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Uzyskiwanie dostępu do prywatnych chmur platformy Azure za pomocą programu Visual Studio

Domyślnie program Visual Studio obsługuje punkty końcowe REST usługi Azure Cloud. W tym artykule dowiesz się, jak używać certyfikatu chmury prywatnej w celu uzyskania dostępu do chmury prywatnej z programu Visual Studio i korzystania z niej.

1. W Azure Portal chmury prywatnej Pobierz plik Publish-Settings lub skontaktuj się z administratorem w celu uzyskania pliku ustawień publikowania. (Plik ma rozszerzenie `.publishsettings` ).

1. W programie Visual Studio **Eksplorator serwera** kliknij prawym przyciskiem myszy węzeł **platformy Azure** , a następnie wybierz pozycję **Zarządzaj i Filtruj subskrypcje**.

    ![Polecenie zarządzania subskrypcjami](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. W oknie dialogowym **Zarządzanie subskrypcjami Microsoft Azure** wybierz kartę **Certyfikaty** , a następnie wybierz pozycję **Importuj**.

    ![Importowanie certyfikatów platformy Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. W oknie dialogowym **Importuj subskrypcje Microsoft Azure** wybierz pozycję **Przeglądaj**.

    ![Przycisk Przeglądaj w oknie dialogowym Importowanie subskrypcji Microsoft Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. W oknie dialogowym **Otwórz** przejdź do katalogu, w którym zapisano plik Publikuj-ustawienia, wybierz plik, a następnie wybierz pozycję **Otwórz**.

    ![Wybierz plik Publish-Settings](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Po powrocie do okna dialogowego **Importuj subskrypcje Microsoft Azure** wybierz pozycję **Importuj**.

    ![Importuj plik Publish-Settings](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Certyfikaty są importowane z pliku Publish-Settings do programu Visual Studio, a teraz można korzystać z zasobów w chmurze prywatnej.
