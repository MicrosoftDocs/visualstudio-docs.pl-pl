---
title: Zarządzanie opcjami konfiguracji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e093b3af6c0db75282d12f8766d36bc511d2cf4c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328652"
---
# <a name="managing-configuration-options"></a>Zarządzanie opcjami konfiguracji
Gdy tworzysz nowy typ projektu, muszą zarządzać projektu i rozwiązania ustawienia konfiguracji, które określają jak projekt zostanie skompilowany, spakowanych, wdrożone i wykonywania. W poniższych tematach omówiono konfiguracji projektu i rozwiązania.

## <a name="in-this-section"></a>W tej sekcji
- [Omówienie](../../extensibility/internals/configuration-options-overview.md)

 W tym artykule opisano sposób projekty w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] może obsługiwać wiele konfiguracji.

- [Strony właściwości](../../extensibility/internals/property-pages.md)

 Wyjaśniono, że użytkownicy mogą przeglądać i zmienić zależne właściwości konfiguracji projektu i niezależnie od właściwości za pomocą strony właściwości.

- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)

 Informacje na temat co to jest przechowywany w konfiguracje rozwiązania i jak konfiguracje rozwiązania bezpośrednie zachowanie **Start** i **kompilacji** poleceń.

- [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)

 W tym artykule wyjaśniono, jak obiekt konfiguracji projektu zarządza wyświetlanie informacji o konfiguracji w interfejsie użytkownika.

- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)

 Wyjaśnia, jak lista konfiguracje rozwiązania dla konkretnego rozwiązania jest zarządzana przez **konfiguracje rozwiązania** okno dialogowe.

- [Konfigurowanie projektu do zarządzania wdrożeniem](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 Określa czynność wdrożenia oraz dwa sposoby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje projekty, które obsługują wdrożenia.

- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)

 Wyjaśnia, procesów kompilacji, obsługujące dla każdej konfiguracji i interfejsów i metod, które wysyłają elementy mogą być udostępniane.

## <a name="related-sections"></a>Sekcje pokrewne
- [Typy projektów](../../extensibility/internals/project-types.md)

 Zawiera omówienie projektów jako podstawowe bloki konstrukcyjne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE). Podano linki do dodatkowych tematów, które wyjaśniają, jak kontrolować projektów, tworzenie i kompilowanie kodu.