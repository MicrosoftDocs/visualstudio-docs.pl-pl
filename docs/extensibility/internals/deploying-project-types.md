---
title: Wdrażanie typów projektów | Microsoft Docs
description: Dowiedz się, jak wdrażać typy projektów Managed-Code przy użyciu nowego agregatora typu projektu i pakietu Instalator Windows do redystrybucji, w zestawie SDK programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 121dda58b8e01c5b0029d8b3c93ef66d2657446e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090996"
---
# <a name="deploy-project-types"></a>Wdróż typy projektów
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instaluje nowy agregator typu projektu (*ProjectAggregator2.dll*), a także pakiet Instalator Windows do redystrybucji (*ProjectAggregator2.msi*). Należy użyć nowego agregatora dla typów projektów z kodem zarządzanym. ProjectAggregator2 działa wokół ograniczeń w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] agregatorze projektu, które uniemożliwiają poprawne działanie typów projektów kodu zarządzanego. W poniższych krokach opisano, jak zmienić pakietu VSPackage na korzystanie z nowego agregatora.

1. Usuń projekt NativeHierarchyWrapper z rozwiązania.

2. Usuń wszystkie pliki binarne NativeHierarchyWrapper z Instalatora.

3. Dodaj *ProjectAggregator2.msi* do Instalatora.
