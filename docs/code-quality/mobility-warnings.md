---
title: Mobilność — Ostrzeżenia
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf1d9402294980a2202bbd3ab99c03b5e438eaa
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448861"
---
# <a name="mobility-warnings"></a>Mobilność — Ostrzeżenia
Ostrzeżenia dotyczące mobilności obsługują wydajne zużycie mocy.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1600: Nie używaj priorytetu procesu bezczynności](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Nie należy ustawiać priorytetu procesu na Idle. Procesy, które mają System.Diagnostics.ProcessPriorityClass.Idle, zajmują procesor, gdy może on być bezczynny, a zatem będą blokować stan gotowości.|
|[CA1601: Nie używaj czasomierzy, które uniemożliwiają zmiany stanu zasilania](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Wyższa częstotliwość działań okresowych sprawi, że procesor będzie zajęty, co zakłóci działanie czasomierzy bezczynności oszczędzających energię, które wyłączają ekran i dyski twarde.|
