---
title: Konfigurowanie projektu usługi w chmurze platformy Azure
description: Dowiedz się, jak skonfigurować projekt usługi w chmurze platformy Azure w programie Visual Studio, w zależności od wymagań dla tego projektu.
author: ghogen
manager: jillfra
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 8f26d862562f7741b4e76d61d052387871771fd7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929118"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Konfigurowanie projektu usługi w chmurze platformy Azure przy użyciu programu Visual Studio
Projekt usługi w chmurze platformy Azure, można skonfigurować w zależności od wymagań dla tego projektu. Można ustawić właściwości dla projektów w ramach następujących kategorii:

- **Opublikuj usługę w chmurze na platformie Azure** — możesz ustawić właściwość, aby upewnić się, że istniejącej usługi w chmurze wdrożona na platformie Azure nie zostanie przypadkowo usunięta.
- **Uruchamianie i debugowanie usługi w chmurze na komputerze lokalnym** — można wybrać konfigurację usługi, i wskazuje, czy można uruchomić emulatora usługi Azure storage.
- **Sprawdzanie poprawności pakietu usługi w chmurze, po utworzeniu** — możesz zdecydować się na traktuje wszystkie ostrzeżenia jako błędy, tak aby zagwarantować, że pakiet usługi w chmurze wdraża się bez żadnych problemów.

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Kroki, aby skonfigurować projekt usługi w chmurze platformy Azure
1. Otwórz lub Utwórz projekt usługi w chmurze w programie Visual Studio

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz z menu kontekstowego **właściwości**.

1. Na stronie właściwości projektu, wybierz **rozwoju** kartę.

    ![Menu Właściwości projektu](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Ustaw **Monituj przed usunięciem istniejącego wdrożenia** do **True**. To ustawienie pozwala, aby upewnić się, że nie można przypadkowo usunąć istniejące wdrożenie na platformie Azure

1. Wybierz żądany **konfiguracji usługi** aby wskazać, która Konfiguracja usługi ma używać podczas uruchamiania lub debugowania usługi w chmurze lokalnie. Aby uzyskać więcej informacji na temat sposobu modyfikowania konfiguracji usługi dla roli, zobacz [sposób konfigurowania ról dla usługi w chmurze platformy Azure przy użyciu programu Visual Studio](./vs-azure-tools-configure-roles-for-cloud-service.md).

1. Ustaw **emulatora magazynu Start Azure** do **True** można uruchomić emulatora usługi Azure storage, podczas uruchamiania lub debugowania usługi w chmurze lokalnie.

1. Ustaw **Traktuj ostrzeżenia jako błędy** do **True** się upewnić, że nie można opublikować, jeśli występują błędy sprawdzania poprawności pakietu.

1. Ustaw **korzystania z portów projektu sieci web** do **True** aby upewnić się, że rola usługi sieci web używa tego samego portu każdym uruchomieniu go lokalnie, w usługach IIS Express.

1. Na pasku narzędzi programu Visual Studio wybierz **Zapisz**.

## <a name="next-steps"></a>Następne kroki
- [Skonfiguruj projekt platformy Azure przy użyciu wielu konfiguracji usługi](vs-azure-tools-multiple-services-project-configurations.md)
