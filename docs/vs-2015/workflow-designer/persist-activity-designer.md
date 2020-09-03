---
title: Trwały Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60a63dd4036863641646e85a89f5018cba786802
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672626"
---
# <a name="persist-activity-designer"></a>Persist, projektant działań
Projektant działań **utrwalania** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Persist> działania.

## <a name="the-persist-activity"></a>Działanie utrwalania
 <xref:System.Activities.Statements.Persist>Działanie zapisuje przepływ pracy na dysku, jeśli jest to możliwe. <xref:System.Activities.Statements.Persist>Działanie nie może zostać wykonane w strefie nietrwałości, jak na przykład w ramach <xref:System.Activities.Statements.TransactionScope> działania. Jeśli używasz <xref:System.Activities.Statements.Persist> działania w zakresie nietrwałości, wyjątek jest zgłaszany w czasie wykonywania.

### <a name="using-the-persist-activity-designer"></a>Korzystanie z projektanta działań utrwalania
 Projektanta działań **utrwalania** można znaleźć w kategorii **środowiska uruchomieniowego** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** (można również wybrać **Przybornik** z menu **Widok** lub CTRL + ALT + X).

 Projektanta działań **utrwalania** można przeciągać z **przybornika** i znajdować się na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.Persist> działania z domyślną wartością **DisplayName** elementu utrwalania. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **trwałych** lub w polu **DisplayName** siatki właściwości.

### <a name="the-persist-properties"></a>Właściwości utrwalania
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Persist> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.Persist> działania. Wartość domyślna to utrwalanie. Chociaż nazwa wyświetlana nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie nazwy wyświetlanej.|

## <a name="see-also"></a>Zobacz też
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) [środowiska uruchomieniowego](../workflow-designer/runtime-activity-designers.md)