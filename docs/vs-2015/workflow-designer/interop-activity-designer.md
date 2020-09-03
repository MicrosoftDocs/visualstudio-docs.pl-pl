---
title: Projektant działań międzyoperacyjnych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 994d7776ff7c32f8dd309e667597550637ef2b5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659040"
---
# <a name="interop-activity-designer"></a>Interop, projektant działań
Projektant działań **międzyoperacyjnych** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Interop> działania.

## <a name="the-interop-activity"></a>Działanie międzyoperacyjności
 <xref:System.Activities.Statements.Interop>Działanie zarządza wykonywaniem typów, które pochodzą z <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> przepływu pracy.

### <a name="using-the-interop-activity-designer"></a>Korzystanie z projektanta działań międzyoperacyjnych
 Projektanta działań **międzyoperacyjnych** można znaleźć w kategorii **migracji** **przybornika**, do którego jest uzyskiwany dostęp przez kliknięcie karty **przybornika** (można również wybrać **Przybornik** z menu **Widok** lub CTRL + ALT + X).

 Kategoria [migracji](../workflow-designer/migration-activity-designers.md) , która zawiera <xref:System.Activities.Statements.Interop> działanie, jest wyświetlana tylko w **przyborniku** , jeśli projekt jest przeznaczony dla całego projektu [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] .

 W przypadku projektów C# można zmienić cel projektu, aby użyć pełnego, [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierając pozycję **Właściwości**. Na karcie **aplikacja** wybierz opcję **.NET Framework 4** w **platformie docelowej**. Wybierz przycisk **tak** w oknie dialogowym **zmiany platformy docelowej** , które wyświetla monit o potwierdzenie zmiany.

 W przypadku projektów w języku VB można zmienić cel projektu, aby użyć pełnego, [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierając pozycję **Właściwości**. Na karcie **Kompilowanie** kliknij przycisk **Zaawansowane opcje kompilacji** . Z **listy platforma docelowa** wybierz pozycję **.NET Framework 4** , a następnie kliknij przycisk **OK**. Kliknij przycisk **tak** w oknie dialogowym **Zmień platformę docelową** , które wyświetli monit o potwierdzenie tej zmiany.

 Projektanta działań **międzyoperacyjnych** można przeciągać z **przybornika** i znajdować się na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.Interop> działania z domyślną wartością **DisplayName** międzyoperacyjności. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **międzyoperacyjnych** lub w polu **DisplayName** siatki właściwości.

 Kliknij **przycisk kliknij, aby przeglądać...** tekst w polu **ActivityType** , w projektancie działań **międzyoperacyjnych**  lub w siatce właściwości, aby wyświetlić okno dialogowe **Przeglądaj i wybierz typ platformy .NET** . Wyświetlane są tylko typy dla działań przepływu pracy 3,0 lub przepływu pracy 3,5 (to jest tylko typy pochodzące z <xref:System.Workflow.ComponentModel.Activity> ). [!INCLUDE[crabout](../includes/crabout-md.md)] przy użyciu tego pola, aby określić typ, zobacz okno [dialogowe Przeglądaj i wybierz typ platformy .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) .

### <a name="the-interop-properties"></a>Właściwości międzyoperacyjności
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Interop> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.Interop> działania. Wartość domyślna to międzyoperacyjność. Chociaż nazwa wyświetlana nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie nazwy wyświetlanej.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Prawda|Określa typ działania zawartego w <xref:System.Activities.Statements.Interop> działaniu. Określony typ musi pochodzić od <xref:System.Workflow.ComponentModel.Activity> .|

## <a name="see-also"></a>Zobacz też
 [Migracja](../workflow-designer/migration-activity-designers.md)