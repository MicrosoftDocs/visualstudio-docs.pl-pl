---
title: Widoki działań (starsze) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7546f752ef7ee1053d1b0b785334a8da814720c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851481"
---
# <a name="activity-views-legacy"></a>Widoki działania (starsza wersja)
Wiele działań zapewnianych przez [!INCLUDE[wf](../includes/wf-md.md)] , z których składają się przepływy pracy, ma kilka widoków projektu dostępnych w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Gdy przeciągniesz projektanta aktywności z **przybornika** na powierzchnię projektu, a następnie za każdym razem, gdy wybierzesz działanie, możesz przełączać się między różnymi widokami projektu za pomocą menu **przepływ pracy** lub klikając prawym przyciskiem myszy wybrane działanie. Ponadto, gdy przesuwasz wskaźnik myszy nad nazwą wybranego działania, zostanie wyświetlona lista rozwijana z kartami, za pomocą której można przełączać się między różnymi widokami.

 Każde działanie ma co najmniej jeden widok; jest to domyślny widok pokazywany po przeciągnięciu projektanta działań z **przybornika** na powierzchnię projektu. Ten domyślny widok działania jest dostępny jako opcja **Widok [Activity type]** w menu i karcie, na przykład, **Widok Parallel**. Większość działań ma dodatkowe widoki i różne działania mogą mieć różne widoki. Na przykład działanie [TransactionScopes](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx) ma widok kompensacja, a działanie [EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx) ma widok zdarzeń. Wiele działań, które są dołączone Windows Workflow Foundation ma **program obsługi anulowania wyświetlania** i **Widok projektu błędów** , umożliwia wyświetlenie [działania CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) i skojarzonych z nimi [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) .

 W poniższej tabeli wymieniono nazwy i opisy poszczególnych widoków.

|Opcja menu/karty|Opis|
|----------------------|-----------------|
|**Widok [typ działania]**|Wybierz to menu lub opcję karty, aby wyświetlić domyślną reprezentację wybranego działania.|
|**Wyświetl procedurę obsługi anulowania**|Zaznacz to menu lub widok opcji karty, aby wyświetlić [działania CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) skojarzone z wybranym działaniem.|
|**Wyświetl procedurę obsługi błędów**|Zaznacz to menu lub widok opcji karty, aby wyświetlić [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) skojarzone z wybranym działaniem.|
|**Wyświetl program obsługi kompensacji**|Zaznacz to menu lub widok opcji karty, aby wyświetlić [CompensationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensationhandleractivity.aspx) skojarzone z wybraną funkcją [TransactionScope](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx).|
|**Wyświetl obsługę zdarzeń**|Zaznacz to menu lub widok opcji karty, aby wyświetlić [EventHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlersactivity.aspx) skojarzone z wybranym [EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx).|

 Aby uzyskać informacje o podobnych widokach, zobacz [sekwencyjne widoki przepływu pracy (starsza wersja)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Zobacz też
 [Starsze operacje przepływu pracy](../workflow-designer/legacy-workflow-activities.md) — [widoki sekwencyjnego przepływu pracy (starsza wersja)](../workflow-designer/sequential-workflow-views-legacy.md)
