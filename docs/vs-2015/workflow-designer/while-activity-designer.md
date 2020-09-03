---
title: Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fae1b4905d66a5162591fd7c720ba81ed7ffda82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606607"
---
# <a name="while-activity-designer"></a>While, projektant działań

<xref:System.Activities.Statements.While>Działanie wykonuje działanie zawarte w jego <xref:System.Activities.Statements.While.Body%2A> czasie, podczas gdy określony warunek ma **wartość true**. Zawarte działanie może nigdy nie zostać wykonane. Jeśli chcesz, aby zawarte działanie było wykonywane co najmniej raz, użyj <xref:System.Activities.Statements.DoWhile> działania zamiast tego.

## <a name="while-properties-in-workflow-designer"></a>Właściwości w Projektant przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.While> właściwości działania i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę <xref:System.Activities.Statements.While> projektanta działań w nagłówku. Wartość domyślna to while. Wartość można edytować w oknie **Właściwości** lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.While.Body%2A>|Fałsz|Zawiera działanie do wykonania, gdy <xref:System.Activities.Statements.While.Condition%2A> wynikiem jest **wartość true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Prawda|Zawiera [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wyrażenie, które jest oceniane, aby określić, czy działanie <xref:System.Activities.Statements.While.Body%2A> ma być wykonywane.|

## <a name="see-also"></a>Zobacz też

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)