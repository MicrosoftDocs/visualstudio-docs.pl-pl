---
title: Konfigurowanie projektu usługi w chmurze platformy Azure
description: Dowiedz się, jak skonfigurować projekt usługi w chmurze platformy Azure w programie Visual Studio, w zależności od wymagań dla tego projektu.
author: ghogen
manager: jillfra
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 609830b5182ef726a6d1933acecb1ddcbf4e25ef
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489704"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Konfigurowanie projektu usługi w chmurze platformy Azure przy użyciu programu Visual Studio
Można skonfigurować projekt usługi w chmurze platformy Azure, w zależności od wymagań dla tego projektu. Właściwości projektu można ustawić dla następujących kategorii:

- **Publikowanie usługi w chmurze na platformie Azure** — można ustawić właściwość, aby upewnić się, że istniejąca usługa w chmurze wdrożona na platformie Azure nie zostanie przypadkowo usunięta.
- **Uruchom lub debuguj usługę w chmurze na komputerze lokalnym** — można wybrać konfigurację usługi do użycia i wskazać, czy chcesz uruchomić emulator magazynu platformy Azure.
- **Sprawdź poprawność pakietu usługi w chmurze podczas jego tworzenia** — możesz zdecydować się na traktowanie wszystkich ostrzeżeń jako błędów, dzięki czemu można zapewnić wdrożenie pakietu usługi w chmurze bez żadnych problemów.

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Kroki konfigurowania projektu usługi w chmurze platformy Azure
1. Otwieranie lub tworzenie projektu usługi w chmurze w programie Visual Studio

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a z menu kontekstowego wybierz polecenie **Właściwości**.

1. Na stronie właściwości projektu wybierz kartę **Rozwój.**

    ![Menu właściwości projektu](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Ustaw **monit przed usunięciem istniejącego wdrożenia** na **True**. To ustawienie pomaga upewnić się, że nie przypadkowo usuniesz istniejące wdrożenie na platformie Azure

1. Wybierz żądaną **konfigurację usługi,** aby wskazać, której konfiguracji usługi chcesz użyć podczas uruchamiania lub debugowania usługi w chmurze lokalnie. Aby uzyskać więcej informacji na temat modyfikowania konfiguracji usługi dla roli, zobacz [Jak skonfigurować role usługi w chmurze platformy Azure za pomocą programu Visual Studio.](./vs-azure-tools-configure-roles-for-cloud-service.md)

1. Ustaw **polecenie Uruchom emulator magazynu platformy Azure** na **True,** aby uruchomić emulator magazynu platformy Azure po uruchomieniu lub debugowaniu usługi w chmurze lokalnie.

1. Ustaw **Traktuj ostrzeżenia jako błędy** **true,** aby upewnić się, że nie można opublikować, jeśli istnieją błędy sprawdzania poprawności pakietu.

1. Ustaw **użyj portów projektu sieci web** na **True,** aby upewnić się, że rola sieci web używa tego samego portu za każdym razem, gdy uruchamia się lokalnie w programie IIS Express.

1. Na pasku narzędzi Programu Visual Studio wybierz pozycję **Zapisz**.

## <a name="next-steps"></a>Następne kroki
- [Konfigurowanie projektu platformy Azure przy użyciu wielu konfiguracji usługi](vs-azure-tools-multiple-services-project-configurations.md)
