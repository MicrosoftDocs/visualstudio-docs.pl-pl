---
title: Zarządzanie opcjami konfiguracji | Microsoft Docs
description: Dowiedz się, jak zarządzać ustawieniami konfiguracji projektów i rozwiązań w programie Visual Studio, aby kontrolować sposób kompilowania, pakowania, wdrażania i uruchamiania projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a34f772b780cda825861e11e6816d1d88405f74e
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204534"
---
# <a name="managing-configuration-options"></a>Zarządzanie opcjami konfiguracji
Podczas tworzenia nowego typu projektu należy zarządzać ustawieniami konfiguracji projektu i rozwiązania, które określają sposób kompilowania, pakowania, wdrażania i uruchamiania projektu. W poniższych tematach omówiono konfigurację projektu i rozwiązania.

## <a name="in-this-section"></a>W tej sekcji
- [Omówienie](../../extensibility/internals/configuration-options-overview.md)

 Opisuje, w jaki sposób projekty w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mogą obsługiwać wiele konfiguracji.

- [Strony właściwości](../../extensibility/internals/property-pages.md)

 Wyjaśniono, że użytkownicy mogą wyświetlać i zmieniać właściwości zależne konfiguracji projektu i niezależne właściwości przy użyciu stron właściwości.

- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)

 Zawiera informacje o tym, co jest przechowywane w konfiguracjach rozwiązań i jak konfiguracje rozwiązań kierują zachowanie poleceń **Start** i **Build** .

- [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)

 Wyjaśnia, jak obiekt konfiguracji projektu zarządza wyświetlaniem informacji o konfiguracji w interfejsie użytkownika.

- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)

 Wyjaśnia, w jaki sposób lista konfiguracji rozwiązań dla danego rozwiązania jest zarządzana przez okno dialogowe **konfiguracje rozwiązań** .

- [Konfigurowanie projektu do zarządzania wdrożeniem](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 Definiuje czynność wdrożenia, a dwa sposoby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługują projekty obsługujące wdrożenie.

- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)

 Wyjaśnia procesy kompilacji, które każda konfiguracja może obsłużyć, oraz interfejsy i metody, za pomocą których można udostępnić elementy wyjściowe.

## <a name="related-sections"></a>Sekcje pokrewne
- [Typy projektów](../../extensibility/internals/project-types.md)

 Zawiera omówienie projektów jako podstawowych bloków konstrukcyjnych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE). Linki są dostarczane do dodatkowych tematów, które wyjaśniają, jak projekty kontrolują Kompilowanie i kompilowanie kodu.
