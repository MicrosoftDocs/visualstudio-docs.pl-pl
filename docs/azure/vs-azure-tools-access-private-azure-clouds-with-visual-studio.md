---
title: Uzyskiwanie dostępu do prywatnych chmur platformy Azure
description: Dowiedz się, jak uzyskać dostęp do zasobów chmury prywatnej przy użyciu programu Visual Studio.
author: ghogen
manager: jillfra
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 57f92aa797e589bd48cc52296b710617cbe8d732
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544370"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Uzyskiwanie dostępu do prywatnych chmur platformy Azure za pomocą programu Visual Studio

Domyślnie visual studio obsługuje punkty końcowe REST w chmurze platformy Azure. W tym artykule dowiesz się, jak używać certyfikatu chmury prywatnej do uzyskiwania dostępu do chmury prywatnej i interakcji z nią z programu Visual Studio.

1. W witrynie Azure portal dla chmury prywatnej pobierz plik ustawień publikowania lub skontaktuj się z administratorem w celu uzyskania pliku ustawień publikowania. (Plik ma rozszerzenie `.publishsettings`.)

1. W **Eksploratorze programu**Visual Studio Server kliknij prawym przyciskiem myszy węzeł **platformy Azure** i wybierz pozycję **Zarządzaj subskrypcjami i filtruj**.

    ![Zarządzanie subskrypcjami, polecenie](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. W oknie **dialogowym Zarządzanie subskrypcjami platformy Microsoft Azure** wybierz kartę **Certyfikaty,** a następnie wybierz pozycję **Importuj**.

    ![Importowanie certyfikatów platformy Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. W oknie dialogowym **Importowanie subskrypcji platformy Microsoft Azure** wybierz pozycję **Przeglądaj**.

    ![Przycisk Przeglądaj w oknie dialogowym Importowanie subskrypcji platformy Microsoft Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. W oknie dialogowym **Otwórz** przejdź do katalogu, w którym zapisano plik ustawień publikowania, wybierz plik, a następnie wybierz pozycję **Otwórz**.

    ![Wybieranie pliku ustawień publikowania](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Po powrocie do okna dialogowego **Importowanie subskrypcji platformy Microsoft Azure** wybierz pozycję **Importuj**.

    ![Importowanie pliku ustawień publikowania](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Certyfikaty są importowane z pliku ustawień publikowania do programu Visual Studio, a teraz można wchodzić w interakcje z zasobami chmury prywatnej.
