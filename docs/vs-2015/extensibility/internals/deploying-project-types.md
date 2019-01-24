---
title: Wdrażanie typów projektów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f168656950c65ce133a8e808a0fa1232726e1b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761293"
---
# <a name="deploying-project-types"></a>Wdrażanie typów projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] instaluje nowy typ projektu agregatora (ProjectAggregator2.dll), a także pakiet Instalatora Windows do ponownej dystrybucji (ProjectAggregator2.msi). Dla typów projektów kodu zarządzanego, należy użyć nowego agregatora. ProjectAggregator2 działa ograniczenia arounds [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projektu agregator, który uniemożliwić poprawne działanie w typach projektów kodu zarządzanego. Poniżej opisano sposób zmiany Twojego pakietu VSPackage, aby użyć nowego agregatora.  
  
1.  Usunięcie projektu NativeHierarchyWrapper z rozwiązania.  
  
2.  Usuń wszystkie pliki binarne NativeHierarchyWrapper z konfiguracji.  
  
3.  Dodaj ProjectAggregator2.msi do konfiguracji.
