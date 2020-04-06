---
title: Wdrażanie typów projektów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708791"
---
# <a name="deploy-project-types"></a>Wdrażanie typów projektów
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]instaluje nowy agregator typu projektu (*ProjectAggregator2.dll*), a także pakiet Instalatora Windows do redystrybucji (*ProjectAggregator2.msi*). Należy użyć nowego agregatora dla typów projektów kodu zarządzanego. ProjectAggregator2 działa wokół [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ograniczeń w agregatorze projektów, który uniemożliwia poprawnie działać typy projektów kodu zarządzanego. W poniższych krokach opisano, jak zmienić vspackage używać nowego agregatora.

1. Usuń projekt NativeHierarchyWrapper z rozwiązania.

2. Usuń wszystkie pliki binarne NativeHierarchyWrapper z konfiguracji.

3. Dodaj *plik ProjectAggregator2.msi* do konfiguracji.
