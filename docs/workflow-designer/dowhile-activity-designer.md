---
title: Projektant przepływu pracy — DoWhile, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc96d44a38a0cf8a1865de236b9f7ef473c960a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960433"
---
# <a name="dowhile-activity-designer"></a>DoWhile, projektant działań

<xref:System.Activities.Statements.DoWhile> Działanie wykonuje działania zawarte w jego <xref:System.Activities.Statements.DoWhile.Body%2A> co najmniej raz, aż określony warunek ma **false**. Jeśli potrzebujesz działania zawarte w treści pętli do wykonania, zero lub więcej razy, użyj <xref:System.Activities.Statements.While> działania zamiast tego.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Właściwości DoWhile w Projektancie przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.DoWhile> właściwości działań i informacje dotyczące używania ich w Projektancie:

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Działanie do wykonania, gdy wynikiem warunku jest **true**. Można dodać <xref:System.Activities.Statements.DoWhile.Body%2A> działania, listy działanie z przybornika do **treści** polu na **DoWhile** projektanta działań z tekst wskazówki "Upuść działanie tutaj".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Prawda|Warunek do oceny po każdej iteracji pętli. Aby ustawić <xref:System.Activities.Statements.DoWhile.Condition%2A>, wpisz wyrażenie języka Visual Basic w **warunek** polu na **DoWhile** działanie projektanta lub w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [While](../workflow-designer/while-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)