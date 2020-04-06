---
title: Tworzenie wtyczki kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e0d9dc54a61cabe7bdd5c21c10abf0def34ff6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709171"
---
# <a name="create-a-source-control-plug-in"></a>Tworzenie wtyczki formantu źródła
Visual Studio SDK udostępnia zasoby, które umożliwiają dodawanie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] możliwości kontroli źródła do zintegrowanego środowiska programistycznego (IDE). Umożliwia użycie dowolnej biblioteki DLL wtyczek, która jest zgodna z interfejsem API wtyczki kontroli źródła opisanym w tej dokumentacji.

## <a name="in-this-section"></a>W tej sekcji
- [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 W tym artykule opisano sposób instalowania wtyczki formantu źródła i wyróżniono aktualnie dostępne wersje interfejsu API dodatku Source Control Plug-in.

- [Architektura](../../extensibility/internals/source-control-plug-in-architecture.md)

 Używa diagramu architektury, aby wyjaśnić integrację wtyczki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kontroli źródła z IDE.

- [Przewodnik po testach](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Zawiera wskazówki dotyczące testowania instalacji i działania wtyczki kontroli źródła.

## <a name="related-sections"></a>Powiązane sekcje
- [Tworzenie formantu źródła VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 W tym artykule omówiono sposób tworzenia formantu źródła VSPackage, który nie tylko dostarcza funkcje kontroli źródła, ale zastępuje interfejs użytkownika kontroli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] źródła.

- [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)

 Zawiera pełną listę wszystkich elementów w interfejsie API wtyczki kontroli źródła.

- [Kontrola źródła](../../extensibility/internals/source-control.md)

 W tym artykule omówiono opcje implementowania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kontroli źródła jako zintegrowanej funkcji programu .
