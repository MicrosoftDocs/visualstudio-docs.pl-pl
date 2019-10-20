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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659040"
---
# <a name="interop-activity-designer"></a>Interop, projektant działań
Projektant działań **międzyoperacyjnych** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.Interop>.

## <a name="the-interop-activity"></a>Działanie międzyoperacyjności
 Działanie <xref:System.Activities.Statements.Interop> zarządza wykonywaniem typów, które pochodzą od <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> w ramach przepływu pracy.

### <a name="using-the-interop-activity-designer"></a>Korzystanie z projektanta działań międzyoperacyjnych
 Projektanta działań **międzyoperacyjnych** można znaleźć w kategorii **migracji** **przybornika**, do którego jest uzyskiwany dostęp przez kliknięcie karty **przybornika** (można również wybrać **Przybornik** z menu **Widok** lub CTRL + ALT + X).

 Kategoria [migracji](../workflow-designer/migration-activity-designers.md) , która zawiera działanie <xref:System.Activities.Statements.Interop>, zostanie wyświetlona tylko w **przyborniku** , jeśli projekt jest przeznaczony dla pełnego [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)].

 W C# przypadku projektów można zmienić cel projektu, aby użyć pełnego [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] przez kliknięcie prawym przyciskiem myszy projektu w **Eksplorator rozwiązań** i wybranie **Właściwości**. Na karcie **aplikacja** wybierz opcję **.NET Framework 4** w **platformie docelowej**. Wybierz przycisk **tak** w oknie dialogowym **zmiany platformy docelowej** , które wyświetla monit o potwierdzenie zmiany.

 W przypadku projektów VB można zmienić docelowy projekt, aby użyć pełnego [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] przez kliknięcie prawym przyciskiem myszy nad projektem w **Eksplorator rozwiązań** i wybranie **Właściwości**. Na karcie **Kompilowanie** kliknij przycisk **Zaawansowane opcje kompilacji** . Z **listy platforma docelowa** wybierz pozycję **.NET Framework 4** , a następnie kliknij przycisk **OK**. Kliknij przycisk **tak** w oknie dialogowym **Zmień platformę docelową** , które wyświetli monit o potwierdzenie tej zmiany.

 Projektanta działań **międzyoperacyjnych** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, wszędzie tam, gdzie działania są zwykle umieszczane, na przykład wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.Interop> z domyślną wartością **DisplayName** międzyoperacyjności. @No__t_0 można edytować w nagłówku projektanta działań **międzyoperacyjnych** lub w polu **DisplayName** siatki właściwości.

 Kliknij **przycisk kliknij, aby przeglądać...** tekst w polu **ActivityType** , w projektancie działań **międzyoperacyjnych** lub w siatce właściwości, aby wyświetlić okno dialogowe **Przeglądaj i wybierz typ platformy .NET** . Wyświetlane są tylko typy dla działań przepływu pracy 3,0 lub przepływu pracy 3,5 (to jest tylko typy pochodzące z <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../includes/crabout-md.md)] przy użyciu tego pola, aby określić typ, zapoznaj się z tematem okno [dialogowe Przeglądaj i wybierz typ platformy .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) .

### <a name="the-interop-properties"></a>Właściwości międzyoperacyjności
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Interop> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.Interop>. Wartość domyślna to międzyoperacyjność. Chociaż nazwa wyświetlana nie jest ściśle wymagana, najlepszym rozwiązaniem jest użycie nazwy wyświetlanej.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Oznacza|Określa typ działania zawartego w działaniu <xref:System.Activities.Statements.Interop>. Określony typ musi pochodzić od <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Zobacz też
 [Migracja](../workflow-designer/migration-activity-designers.md)