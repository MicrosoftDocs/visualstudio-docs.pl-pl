---
title: Tworzenie wtyczki kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8489e991a54df5b905289a64fccb0df65c3cec8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341928"
---
# <a name="create-a-source-control-plug-in"></a>Tworzenie wtyczki kontroli źródła
Visual Studio SDK zawiera zasoby, które umożliwiają dodawanie możliwości kontroli źródła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE). Dzięki temu można użyć biblioteki DLL w dodatku plug-in, który jest zgodny z interfejsu API wtyczki kontroli źródła opisane w tej dokumentacji.

## <a name="in-this-section"></a>W tej sekcji
- [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 W tym artykule opisano sposób instalowania wtyczki kontroli źródła i wyróżnienie obecnie dostępnych wersji interfejsu API wtyczki kontroli źródła.

- [Architektura](../../extensibility/internals/source-control-plug-in-architecture.md)

 Używa diagram architektury, aby wyjaśnić integracji wtyczka do kontroli źródła przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Przewodnik po testowym](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Zawiera wskazówki dotyczące sposobu testowania instalacji i działania wtyczki kontroli źródła.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie pakietu VSPackage kontroli źródła](../../extensibility/internals/creating-a-source-control-vspackage.md)

 W tym artykule omówiono sposób tworzenia kontroli źródła pakietu VSPackage, który nie tylko zapewnia funkcji kontroli źródła, lecz zastępuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] źródłowej kontrolki interfejsu użytkownika.

- [Wtyczek kontroli kodu źródłowego](../../extensibility/source-control-plug-ins.md)

 Zawiera pełną listę wszystkich elementów w interfejsie API wtyczki kontroli źródła.

- [Kontrola źródła](../../extensibility/internals/source-control.md)

 W tym artykule omówiono opcje implementowania kontroli źródła jako zintegrowaną funkcją [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
