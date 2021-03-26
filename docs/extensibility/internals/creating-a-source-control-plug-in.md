---
title: Tworzenie wtyczki kontroli źródła | Microsoft Docs
description: Dowiedz się, jak utworzyć wtyczkę kontroli źródła, która dodaje możliwości kontroli źródła do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc302ee7327740380bb02e28c99e5117c926c7bc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056899"
---
# <a name="create-a-source-control-plug-in"></a>Tworzenie wtyczki kontroli źródła
Zestaw Visual Studio SDK udostępnia zasoby, które umożliwiają dodawanie funkcji kontroli źródła do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE). Umożliwia korzystanie z dowolnych bibliotek DLL, które są zgodne z interfejsem API kontroli źródła opisanymi w tej dokumentacji.

## <a name="in-this-section"></a>W tej sekcji
- [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Opisuje, jak zainstalować wtyczkę kontroli źródła i podświetlić obecnie dostępne wersje interfejsu API kontroli źródła.

- [Architektura](../../extensibility/internals/source-control-plug-in-architecture.md)

 Używa diagramu architektury, aby wyjaśnić integrację wtyczki kontroli źródła z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Przewodnik testowy](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Zawiera wskazówki dotyczące testowania instalacji i działania wtyczki kontroli źródła.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie pakietu VSPackage kontroli źródła](../../extensibility/internals/creating-a-source-control-vspackage.md)

 W tym artykule omówiono sposób tworzenia pakietu VSPackage kontroli źródła, które nie tylko dostarczają funkcji kontroli źródła, ale zastępują [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejs użytkownika kontroli źródła.

- [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)

 Zawiera kompletną listę wszystkich elementów w interfejsie API dodatku plug-in kontroli źródła.

- [Kontrola źródła](../../extensibility/internals/source-control.md)

 W tym artykule omówiono opcje implementowania kontroli źródła jako funkcji zintegrowanej programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
