---
title: Widoki sekwencyjnego przepływu pracy (starsze) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8acc9bfcac476425ac6c6b967b1a3b3a34310d8a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663226"
---
# <a name="sequential-workflow-views-legacy"></a>Widoki sekwencyjnego przepływu pracy (starsza wersja)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] zapewnia starszą [!INCLUDE[wfd1](../includes/wfd1-md.md)], której można użyć do [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 @No__t_0 zapewnia sposób graficznego tworzenia aplikacji [!INCLUDE[wf](../includes/wf-md.md)] przy użyciu znanego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu użytkownika. [!INCLUDE[wf](../includes/wf-md.md)] aplikacje składają się z kroków procesu przepływu pracy o nazwie Activities. Aby utworzyć przepływ pracy, Zredaguj działania na powierzchni projektowej, przeciągając odpowiednie Projektanci działań z **przybornika** na powierzchnię projektu.

 Po utworzeniu sekwencyjnego przepływu pracy, który jest [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), dostępne są trzy widoki przepływu pracy. Te widoki są dostępne z menu **przepływ pracy** oraz z menu kontekstowego na powierzchni projektowej.

 W poniższej tabeli wymieniono nazwy i opisy poszczególnych widoków.

|Opcja menu/karty|Opis|
|----------------------|-----------------|
|**Wyświetl SequentialWorkflow**|Kliknij prawym przyciskiem myszy powierzchnię projektu i wybierz opcję **Wyświetl SequentialWorkflow** z menu kontekstowego, aby wyświetlić widok **sekwencyjnego przepływu pracy** , który pokazuje graficzną reprezentację przepływu pracy sekwencyjnej na podstawie działania. Lub wybierz pozycję **Wyświetl SequentialWorkflow** w menu **przepływ pracy** .|
|**Wyświetl procedurę obsługi anulowania**|Kliknij prawym przyciskiem myszy powierzchnię projektu i wybierz opcję **Wyświetl anulowania obsługi** z menu kontekstowego, aby wyświetlić widok **sekwencyjnego przepływu pracy** , który pokazuje działanie [działania CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) skojarzone z przepływem pracy. Lub wybierz opcję **Wyświetl program obsługi Anuluj** z menu **przepływ pracy** .|
|**Wyświetl procedurę obsługi błędów**|Kliknij prawym przyciskiem myszy powierzchnię projektu i wybierz opcję **Wyświetl procedurę obsługi błędów** z menu kontekstowego, aby wyświetlić widok **błędów** , który pokazuje działanie [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) skojarzone z przepływem pracy. Lub wybierz opcję **Wyświetl procedurę obsługi błędów** z menu **przepływ pracy** .|

 Aby uzyskać więcej informacji o podobnych widokach, zobacz [widoki działań (starsza wersja)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Zobacz też
 [Widoki działań (starsze)](../workflow-designer/activity-views-legacy.md) [Tworzenie starszych projektów przepływu](../workflow-designer/creating-legacy-workflow-projects.md) pracy — [Tryby tworzenia przepływu pracy](http://go.microsoft.com/fwlink?LinkID=65014)