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
ms.openlocfilehash: b42e4f879352a6edaf9171296b282accd9b1ae3f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009911"
---
# <a name="deploy-project-types"></a>Wdrażanie typów projektów
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instaluje nowy agregator typu projektu (*ProjectAggregator2.dll*) i również pakiet Instalatora Windows do ponownej dystrybucji (*ProjectAggregator2.msi*). Dla typów projektów kodu zarządzanego, należy użyć nowego agregatora. ProjectAggregator2 pozwala ominąć ograniczeń [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu agregator, który uniemożliwia poprawne działanie w typach projektów kodu zarządzanego. Poniżej opisano sposób zmiany Twojego pakietu VSPackage, aby użyć nowego agregatora.  
  
1.  Usunięcie projektu NativeHierarchyWrapper z rozwiązania.  
  
2.  Usuń wszystkie pliki binarne NativeHierarchyWrapper z konfiguracji.  
  
3.  Dodaj *ProjectAggregator2.msi* do konfiguracji.