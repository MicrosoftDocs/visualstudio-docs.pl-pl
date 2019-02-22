---
title: Wdrażanie typów projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 958628194e4ea768de5a47dc66476345bff6c4f3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625338"
---
# <a name="deploy-project-types"></a>Wdrażanie typów projektów
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instaluje nowy agregator typu projektu (*ProjectAggregator2.dll*) i również pakiet Instalatora Windows do ponownej dystrybucji (*ProjectAggregator2.msi*). Dla typów projektów kodu zarządzanego, należy użyć nowego agregatora. ProjectAggregator2 pozwala ominąć ograniczeń [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu agregator, który uniemożliwia poprawne działanie w typach projektów kodu zarządzanego. Poniżej opisano sposób zmiany Twojego pakietu VSPackage, aby użyć nowego agregatora.

1.  Usunięcie projektu NativeHierarchyWrapper z rozwiązania.

2.  Usuń wszystkie pliki binarne NativeHierarchyWrapper z konfiguracji.

3.  Dodaj *ProjectAggregator2.msi* do konfiguracji.