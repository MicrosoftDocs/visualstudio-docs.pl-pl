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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 542747f650888b384a9f9c4910b0d9caea93e948
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860571"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Przegląd analizy kodu dla platformy .NET w programie Visual Studio

Program Visual Studio może przeanalizować kod zarządzany na dwa sposoby: ze [starszą analizą](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), znaną również jako FxCop statycznej analizy zestawów zarządzanych i bardziej nowoczesnymi [analizatorami kodu opartymi na .NET compiler platform](../code-quality/roslyn-analyzers-overview.md). Analizatory kodu oparte na .NET Compiler Platform, które analizują kod na żywo podczas pisania, Zastąp FxCopą statyczną analizę kodu statycznego, która analizuje tylko skompilowany kod.
