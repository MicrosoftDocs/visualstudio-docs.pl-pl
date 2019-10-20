---
title: Projektant przepływu pracy — Projektant działań DoWhile
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85f8d6c442982fff47a679e8fc2ccc04ee515a9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650518"
---
# <a name="dowhile-activity-designer"></a>DoWhile, projektant działań

Działanie <xref:System.Activities.Statements.DoWhile> wykonuje działanie zawarte w <xref:System.Activities.Statements.DoWhile.Body%2A> co najmniej raz, do momentu, gdy określony warunek zwróci **wartość false**. Jeśli potrzebujesz działania zawartego w pętli, która ma być wykonywana zero lub więcej razy, Użyj działania <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Właściwości DoWhile w Projektant przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne właściwości działania <xref:System.Activities.Statements.DoWhile> i opisano sposób ich używania w projektancie:

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Działanie do wykonania, gdy warunek ma **wartość true**. Aby dodać działanie <xref:System.Activities.Statements.DoWhile.Body%2A>, Usuń działanie z przybornika do pola **treść** w projektancie działań **DoWhile** ze wskazówkami tekst "upuść aktywność tutaj".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Oznacza|Warunek do obliczenia po każdej iteracji pętli. Aby ustawić <xref:System.Activities.Statements.DoWhile.Condition%2A>, wpisz wyrażenie Visual Basic w polu **warunek** w projektancie działań **DoWhile** lub siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [While](../workflow-designer/while-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)