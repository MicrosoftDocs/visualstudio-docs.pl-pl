---
title: Analiza kodu zarządzanego
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e6515c0df7a9c3389e754d5238788d716be49e2e
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800089"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Przegląd analizy kodu dla kodu zarządzanego w programie Visual Studio

Program Visual Studio może przeanalizować kod zarządzany na dwa sposoby:
- Dzięki [starszej analizie](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), znanej również jako FxCop statycznej analizy zestawów zarządzanych.
- Z bardziej nowoczesnymi [analizatorami kodu opartymi na .NET compiler platform](../code-quality/roslyn-analyzers-overview.md). Analizatory kodu oparte na .NET Compiler Platform, które analizują kod na żywo podczas pisania, Zastąp FxCopą statyczną analizę kodu statycznego, która analizuje tylko skompilowany kod.