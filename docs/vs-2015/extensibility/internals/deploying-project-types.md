---
title: Wdrażanie typów projektów | Microsoft Docs
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
ms.openlocfilehash: 0fda84d5f7467a65b254d3b12b0466b6ab415d61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196881"
---
# <a name="deploying-project-types"></a>Wdrażanie typów projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] instaluje nowy agregator typu projektu (ProjectAggregator2.dll), a także pakiet Instalator Windows do redystrybucji (ProjectAggregator2.msi). Należy użyć nowego agregatora dla typów projektów z kodem zarządzanym. ProjectAggregator2 działa wokół ograniczeń w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] agregatorze projektu, które uniemożliwiają poprawne działanie typów projektów kodu zarządzanego. W poniższych krokach opisano, jak zmienić pakietu VSPackage na korzystanie z nowego agregatora.  
  
1. Usuń projekt NativeHierarchyWrapper z rozwiązania.  
  
2. Usuń wszystkie pliki binarne NativeHierarchyWrapper z Instalatora.  
  
3. Dodaj ProjectAggregator2.msi do Instalatora.
