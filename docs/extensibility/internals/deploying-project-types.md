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
ms.openlocfilehash: 1e89f74d940182cd92fd15f726676f0979d21186
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861367"
---
# <a name="deploy-project-types"></a>Wdrażanie typów projektów
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instaluje nowy agregator typu projektu (*ProjectAggregator2.dll*) i również pakiet Instalatora Windows do ponownej dystrybucji (*ProjectAggregator2.msi*). Dla typów projektów kodu zarządzanego, należy użyć nowego agregatora. ProjectAggregator2 pozwala ominąć ograniczeń [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu agregator, który uniemożliwia poprawne działanie w typach projektów kodu zarządzanego. Poniżej opisano sposób zmiany Twojego pakietu VSPackage, aby użyć nowego agregatora.

1. Usunięcie projektu NativeHierarchyWrapper z rozwiązania.

2. Usuń wszystkie pliki binarne NativeHierarchyWrapper z konfiguracji.

3. Dodaj *ProjectAggregator2.msi* do konfiguracji.