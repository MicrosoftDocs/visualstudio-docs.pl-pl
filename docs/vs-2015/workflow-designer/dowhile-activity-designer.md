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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656773"
---
# <a name="dowhile-activity-designer"></a>DoWhile, projektant działań
<xref:System.Activities.Statements.DoWhile>Działanie wykonuje działanie zawarte w <xref:System.Activities.Statements.DoWhile.Body%2A> co najmniej raz, dopóki określony warunek nie zwróci **wartości false**. Jeśli potrzebujesz działania zawartego w treści pętli do wykonania zero lub więcej razy, użyj <xref:System.Activities.Statements.While> działania zamiast tego.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Właściwości DoWhile w Projektant przepływu pracy
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.DoWhile> właściwości działania i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Fałsz|Działanie do wykonania, gdy warunek ma **wartość true**. Aby dodać <xref:System.Activities.Statements.DoWhile.Body%2A> działanie, Usuń działanie z przybornika do pola **treść** w projektancie działań **DoWhile** z podpowiedzią tekst "upuść działanie tutaj".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Prawda|Warunek do obliczenia po każdej iteracji pętli. Aby ustawić <xref:System.Activities.Statements.DoWhile.Condition%2A> , wpisz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wyrażenie w polu **warunek** w projektancie działań **DoWhile** lub w siatce właściwości.|

## <a name="see-also"></a>Zobacz też
 [Podczas](../workflow-designer/while-activity-designer.md) [przepływu sterowania](../workflow-designer/control-flow-activity-designers.md)