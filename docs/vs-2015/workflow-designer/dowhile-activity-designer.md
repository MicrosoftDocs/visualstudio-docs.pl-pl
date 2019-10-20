---
title: DoWhile — Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b63c3e2e0907bcaf13ada4cbb20ce5527a240fe3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656773"
---
# <a name="dowhile-activity-designer"></a>DoWhile, projektant działań
Działanie <xref:System.Activities.Statements.DoWhile> wykonuje działanie zawarte w <xref:System.Activities.Statements.DoWhile.Body%2A> co najmniej raz, do momentu, gdy określony warunek zwróci **wartość false**. Jeśli potrzebujesz działania zawartego w pętli, która ma być wykonywana zero lub więcej razy, Użyj działania <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Właściwości DoWhile w Projektant przepływu pracy
 W poniższej tabeli przedstawiono najbardziej przydatne właściwości działania <xref:System.Activities.Statements.DoWhile> i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Działanie do wykonania, gdy warunek ma **wartość true**. Aby dodać działanie <xref:System.Activities.Statements.DoWhile.Body%2A>, Usuń działanie z przybornika do pola **treść** w projektancie działań **DoWhile** ze wskazówkami tekst "upuść aktywność tutaj".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Oznacza|Warunek do obliczenia po każdej iteracji pętli. Aby ustawić <xref:System.Activities.Statements.DoWhile.Condition%2A>, wpisz wyrażenie [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] w polu **warunek** w projektancie działań **DoWhile** lub siatce właściwości.|

## <a name="see-also"></a>Zobacz też
 [Podczas](../workflow-designer/while-activity-designer.md) [przepływu sterowania](../workflow-designer/control-flow-activity-designers.md)