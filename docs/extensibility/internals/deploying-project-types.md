---
title: Wdrażanie typów projektów | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708791"
---
# <a name="deploy-project-types"></a>Wdróż typy projektów
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instaluje nowy agregator typu projektu (*ProjectAggregator2.dll*), a także pakiet Instalator Windows do redystrybucji (*ProjectAggregator2.msi*). Należy użyć nowego agregatora dla typów projektów z kodem zarządzanym. ProjectAggregator2 działa wokół ograniczeń w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] agregatorze projektu, które uniemożliwiają poprawne działanie typów projektów kodu zarządzanego. W poniższych krokach opisano, jak zmienić pakietu VSPackage na korzystanie z nowego agregatora.

1. Usuń projekt NativeHierarchyWrapper z rozwiązania.

2. Usuń wszystkie pliki binarne NativeHierarchyWrapper z Instalatora.

3. Dodaj *ProjectAggregator2.msi* do Instalatora.
