---
title: Pomijanie ostrzeżeń przy użyciu atrybutu SuppressMessage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- VC.Project.VCFxCopTool.InputAssemblyFileName
- VC.Project.VCFxCopTool.FxCopModuleSuppressionsFile
- VC.Project.VCFxCopTool.FxCopUseTypeNameInSuppression
- VC.Project.VCFxCopTool.OutputFile
helpviewer_keywords:
- code analysis, source suppression
- source suppression
- SuppressMessage attribute
- code analysis, SuppressMessage attribute
ms.assetid: a38c57a2-d29d-43c0-84ff-3308b2484ce6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a5d64a27759cf844550297beb19b026bbeaa0e40
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546825"
---
# <a name="suppress-warnings-by-using-the-suppressmessage-attribute"></a>Tłumienie ostrzeżeń przy użyciu atrybutu SuppressMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Często warto wskazać, że ostrzeżenie nie ma zastosowania, aby umożliwić członkom zespołu znać, że kod został zweryfikowany i stwierdzono, że ostrzeżenie powinno być pominięte. W przypadku pomijania źródła (ISS) umożliwia deweloperowi umieszczenie atrybutu, który pomija ostrzeżenie blisko lokalizacji, która wygenerowała ostrzeżenie. Można dodać atrybut ISS bezpośrednio do pliku źródłowego lub użyć menu skrótów w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.

## <a name="in-this-section"></a>W tej sekcji

|Tytuł|Opis|
|-|-|
|[Pomijanie w kodzie źródłowym — przegląd](../code-quality/in-source-suppression-overview.md)|Dowiedz się więcej o platformie ISS i sposobach używania jej w kodzie.|
|[Instrukcje: Pomijanie ostrzeżeń przy użyciu pozycji menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)|Informacje o pomijaniu ostrzeżeń w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE przy użyciu menu skrótów.|

## <a name="related-sections"></a>Sekcje pokrewne
 [Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
