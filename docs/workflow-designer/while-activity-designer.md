---
title: Projektant przepływu pracy — while — Projektant działań
description: Dowiedz się, w jaki sposób działanie while wykonuje działanie zawarte w jego treści, podczas gdy określony warunek ma wartość true.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9447d32f17283e7123e2f99490acc49c1613360d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837999"
---
# <a name="while-activity-designer"></a>While, projektant działań

<xref:System.Activities.Statements.While>Działanie wykonuje działanie zawarte w elemencie, <xref:System.Activities.Statements.While.Body%2A> podczas gdy określony <xref:System.Activities.Statements.While.Condition%2A> wynik ma **wartość true**. Zawarte działanie może nigdy nie zostać wykonane. Jeśli chcesz, aby zawarte działanie było wykonywane co najmniej raz, użyj <xref:System.Activities.Statements.DoWhile> działania zamiast tego.

## <a name="while-properties-in-workflow-designer"></a>Właściwości w Projektant przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.While> właściwości działania i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę <xref:System.Activities.Statements.While> projektanta działań w nagłówku. Wartość domyślna to while. Wartość można edytować w oknie **Właściwości** lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.While.Body%2A>|Fałsz|Zawiera działanie do wykonania, gdy <xref:System.Activities.Statements.While.Condition%2A> wynikiem jest **wartość true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Prawda|Zawiera wyrażenie Visual Basic, które jest oceniane, aby określić, czy działanie <xref:System.Activities.Statements.While.Body%2A> ma być wykonywane.|

## <a name="see-also"></a>Zobacz też

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
