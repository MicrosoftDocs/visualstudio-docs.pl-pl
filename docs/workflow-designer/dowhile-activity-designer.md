---
title: Projektant przepływu pracy — Projektant działań DoWhile
description: Dowiedz się, w jaki sposób działanie DoWhile wykonuje działanie zawarte w jego treści co najmniej raz, do momentu, gdy określony warunek zwróci wartość false.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e117fcbea0488c4b6a42125971984b86cf78251
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894260"
---
# <a name="dowhile-activity-designer"></a>DoWhile, projektant działań

<xref:System.Activities.Statements.DoWhile>Działanie wykonuje działanie zawarte w <xref:System.Activities.Statements.DoWhile.Body%2A> co najmniej raz, dopóki określony warunek nie zwróci **wartości false**. Jeśli potrzebujesz działania zawartego w treści pętli do wykonania zero lub więcej razy, użyj <xref:System.Activities.Statements.While> działania zamiast tego.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Właściwości DoWhile w Projektant przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.DoWhile> właściwości działania i opisano sposób ich używania w projektancie:

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Fałsz|Działanie do wykonania, gdy warunek ma **wartość true**. Aby dodać <xref:System.Activities.Statements.DoWhile.Body%2A> działanie, Usuń działanie z przybornika do pola **treść** w projektancie działań **DoWhile** z podpowiedzią tekst "upuść działanie tutaj".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Prawda|Warunek do obliczenia po każdej iteracji pętli. Aby ustawić <xref:System.Activities.Statements.DoWhile.Condition%2A> , wpisz wyrażenie Visual Basic w polu **warunek** w projektancie działań **DoWhile** lub siatce właściwości.|

## <a name="see-also"></a>Zobacz też

- [Czekać](../workflow-designer/while-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)