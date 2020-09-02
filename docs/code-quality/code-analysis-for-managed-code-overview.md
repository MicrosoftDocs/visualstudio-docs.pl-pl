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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89091407"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Przegląd analizy kodu dla platformy .NET w programie Visual Studio

Program Visual Studio może przeanalizować kod zarządzany na dwa sposoby: ze [starszą analizą](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), znaną również jako FxCop statycznej analizy zestawów zarządzanych i bardziej nowoczesnymi [analizatorami kodu opartymi na .NET compiler platform](../code-quality/roslyn-analyzers-overview.md). Analizatory kodu oparte na .NET Compiler Platform, które analizują kod na żywo podczas pisania, Zastąp FxCopą statyczną analizę kodu statycznego, która analizuje tylko skompilowany kod.
