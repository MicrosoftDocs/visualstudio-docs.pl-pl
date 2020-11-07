---
title: Analiza kodu zarządzanego
ms.date: 08/27/2020
description: Dowiedz się więcej na temat analizatorów kodu opartych na .NET Compiler Platform w programie Visual Studio. Dowiedz się, dlaczego te analizatory zastępują FxCop statycznej analizy zestawów zarządzanych.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 643e8457dbbe838d593a7bad38064537b6cbe57d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348531"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Przegląd analizy kodu dla platformy .NET w programie Visual Studio

Program Visual Studio może przeanalizować kod zarządzany na dwa sposoby: ze [starszą analizą](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), znaną również jako FxCop statycznej analizy zestawów zarządzanych i bardziej nowoczesnymi [analizatorami kodu opartymi na .NET compiler platform](../code-quality/roslyn-analyzers-overview.md). Analizatory kodu oparte na .NET Compiler Platform, które analizują kod na żywo podczas pisania, Zastąp FxCopą statyczną analizę kodu statycznego, która analizuje tylko skompilowany kod.
