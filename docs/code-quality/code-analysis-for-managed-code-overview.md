---
title: Analiza kodu zarządzanego
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d13a8afdfcbeb6ae9f91e39779af8b82b2461000
ms.sourcegitcommit: 016bcdc7cd3e3619457beb321800e98544efb6c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2020
ms.locfileid: "89091407"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Przegląd analizy kodu dla platformy .NET w programie Visual Studio

Program Visual Studio może przeanalizować kod zarządzany na dwa sposoby: ze [starszą analizą](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), znaną również jako FxCop statycznej analizy zestawów zarządzanych i bardziej nowoczesnymi [analizatorami kodu opartymi na .NET compiler platform](../code-quality/roslyn-analyzers-overview.md). Analizatory kodu oparte na .NET Compiler Platform, które analizują kod na żywo podczas pisania, Zastąp FxCopą statyczną analizę kodu statycznego, która analizuje tylko skompilowany kod.
