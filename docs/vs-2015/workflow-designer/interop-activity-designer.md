---
title: Interop, Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55829e85b17bcdc70e419a8496d4756d0acb4a56
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767534"
---
# <a name="interop-activity-designer"></a>Interop, projektant działań
**Międzyoperacyjności** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Interop> działania.  
  
## <a name="the-interop-activity"></a>Działań Interop  
 <xref:System.Activities.Statements.Interop> Działanie zarządza wykonaniem typów wyprowadzonych z <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> w przepływie pracy.  
  
### <a name="using-the-interop-activity-designer"></a>Za pomocą Interop, Projektant działań  
 **Międzyoperacyjności** projektanta działań można znaleźć w **migracji** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karty (opcjonalnie zaznacz **przybornika** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 [Migracji](../workflow-designer/migration-activity-designers.md) kategorię, która zawiera <xref:System.Activities.Statements.Interop> działanie tylko zostaną wyświetlone w **przybornika** Jeśli projekt jest przeznaczony dla pełnej [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)].  
  
 Dla projektów C#, można ponownie docelowej projektu, aby użyć pełnej [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając polecenie **właściwości**. Na **aplikacji** zaznacz **.NET Framework 4** opcji **platformę docelową**. Wybierz **tak** znajdujący się w **Target Framework zmienić** okno dialogowe z pytaniem o potwierdzenie tej zmiany.  
  
 Dla projektów w języku VB, można ponownie docelowej projektu, aby użyć pełnej [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] przez kliknięcie prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając polecenie **właściwości**. Na **skompilować** kliknij pozycję **zaawansowane opcje kompilacji** przycisku. Wybierz **.Net Framework 4** z **Target framework listy** a następnie kliknij przycisk **OK**. Kliknij przycisk **tak** znajdujący się w **Target Framework zmienić** okno dialogowe z pytaniem o potwierdzenie tej zmiany.  
  
 **Międzyoperacyjności** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Interop> działanie przy użyciu domyślnego **DisplayName** z międzyoperacyjności. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **międzyoperacyjności** projektanta działań lub **DisplayName** pola siatki właściwości.  
  
 Kliknij przycisk **kliknij, aby przeglądać...** tekst w **ActivityType** pole, albo na **międzyoperacyjności** działanie projektanta lub w siatce właściwości, aby wyświetlić **przeglądania i wybierz pozycję .net typu** okno dialogowe. Są wyświetlane tylko typy workflow 3.0 lub 3.5 w przepływie pracy działań (czyli tylko typy pochodne <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../includes/crabout-md.md)] przy użyciu tego pola, aby określić typ, zobacz [umożliwia przeglądanie i wybieranie typu .NET, okno dialogowe](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) tematu.  
  
### <a name="the-interop-properties"></a>Właściwości międzyoperacyjności  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Interop> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Interop> działania. Wartość domyślna to międzyoperacyjności. Chociaż nazwa wyświetlana nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć nazwy wyświetlanej.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Prawda|Określa typ działania zawarte w <xref:System.Activities.Statements.Interop> działania. Ten typ określony muszą pochodzić od <xref:System.Workflow.ComponentModel.Activity>.|  
  
## <a name="see-also"></a>Zobacz też  
 [Migracja](../workflow-designer/migration-activity-designers.md)