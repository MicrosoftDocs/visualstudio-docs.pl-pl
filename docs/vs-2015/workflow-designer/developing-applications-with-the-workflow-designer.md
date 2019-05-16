---
title: Tworzenie aplikacji za pomocą projektanta przepływów pracy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9eea79978b7b61de1e56d787b5a4cd9797be1aa6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704786"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Tworzenie aplikacji za pomocą projektanta przepływów pracy
[!INCLUDE[wfd1](../includes/wfd1-md.md)] Jest widoczny Projektant wizualny oraz debugera dla konstrukcji graficznego i debugowanie [!INCLUDE[wf](../includes/wf-md.md)] aplikacji w [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] hostowaną w [!INCLUDE[vs2010](../includes/vs2010-md.md)] środowiska deweloperskiego. Pozwala ona do tworzenia aplikacji złożonych przepływu pracy, biblioteka działań lub [!INCLUDE[indigo1](../includes/indigo1-md.md)] usługi przy użyciu szablonów i projektantów działań. [!INCLUDE[crabout](../includes/crabout-md.md)] przepływy pracy, zobacz [Windows Workflow Foundation &#91;.NET Framework 4&#93;](https://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
 Poniżej przedstawiono kilka nowych funkcji projektowania modyfikujące tej nowej wersji składnika [!INCLUDE[wfd2](../includes/wfd2-md.md)] oprócz starsze wersje [!INCLUDE[wfd2](../includes/wfd2-md.md)]:  
  
- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Został skompilowany przy użyciu [!INCLUDE[avalon1](../includes/avalon1-md.md)]. To zwiększają komfort projektanta działań i zwiększa wydajność dużych i złożonych przepływów pracy.  
  
- Działania niestandardowe, teraz są skonstruowane z [!INCLUDE[avalon2](../includes/avalon2-md.md)], przy użyciu XAML i model programowania do tworzenia Projektanci działań zostały uproszczone.  
  
- Działania został zaimplementowany, co pozwala wizualizować przepływem programu za pomocą dobrze znanych schematów blokowych modelowania stylu.  
  
- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Ma nowej zmiennej projektanta umożliwiającego zadeklarować i określać ich zakresy zmiennych w ramach przepływów pracy, powiązanie ich z działania.  
  
- W [!INCLUDE[vs2010](../includes/vs2010-md.md)], [!INCLUDE[wfd2](../includes/wfd2-md.md)] zapewnia wszystkie funkcje IntelliSense podczas tworzenia wyrażeń języka Visual Basic w ramach Twojej [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] przepływów pracy.  
  
- Środowisko debugowania teraz obejmuje XAML, dzięki czemu możesz ustawić punkty przerwania w definicji przepływu pracy XAML i aby wejść do kodu XAML w czasie wykonywania, który zapewnia środowisko, podobnie jak w kodzie zarządzanym.  
  
- Rehostowanie [!INCLUDE[wfd2](../includes/wfd2-md.md)] poza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] znacznie jest uproszczony w porównaniu z poprzednimi wersjami, teraz wymaga tylko kilku wierszy kodu.  
  
- Nowy <xref:System.Activities.Statements.Flowchart> działanie i jego [schemat blokowy](../workflow-designer/flowchart-activity-designer.md) pozwala na wizualizowanie przepływu programu przy użyciu dobrze znanych schematów blokowych modelowania stylu.  
  
- Zostały rozszerzone działań dotyczących komunikatów, umożliwiającego pisanie pełni deklaracyjnego (Brak kodu) [!INCLUDE[indigo1](../includes/indigo1-md.md)] usług.  
  
- **Dodaj odwołanie do usługi...** funkcja umożliwia generowanie działania automatycznie uzyskiwać dostęp do usług sieci Web.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie projektanta przepływu pracy](../workflow-designer/using-the-workflow-designer.md)  
 Pokazuje sposób tworzenia nowych działań i projektów przepływu pracy przy użyciu wbudowanych projektantów oraz używać innych narzędzi dostarczonych przez projektanta do obsługi argumentów, zmienne, wyrażeń, importuje i nadrzędnych.  
  
 [Używanie projektantów działań](../workflow-designer/using-the-activity-designers.md)  
 Opis kategorii działań i szablony oraz ich projektantów, które są dostarczane przez system.  
  
 [Debugowanie przepływów pracy za pomocą Projektanta przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Opisano sposób wykonywania tradycyjnych debugowanie procedur, a także debugowanie XAML i wyrażeń.  
  
 [Pomoc interfejsu użytkownika Projektanta przepływu pracy](../workflow-designer/workflow-designer-ui-help.md)  
 Zawiera tematy pomocy kontekstowej dla okien dialogowych, dostarczone przez [!INCLUDE[wfd1](../includes/wfd1-md.md)], a także wskazówki dotyczące funkcje powłoki projektanta, za pomocą klawiatury skróty i komunikaty o błędach.  
  
 [Opracowywanie aplikacji przepływu pracy przeznaczonych dla platformy .NET 3.0 lub .NET 3.5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Zawiera wskazówki dotyczące używania starszej wersji projektanta, który jest przeznaczony dla [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 [Rehostowanie projektanta &#91;WF — przykłady&#93;](https://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 W tym przykładzie przedstawiono sposób tworzenia układu WPF zawiera projektanta.  
  
 [Projektanci działań niestandardowych](https://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075)  
 Ta sekcja zawiera przykłady działań, które za pomocą projektantów niestandardowych do wyświetlania w Projektancie przepływu pracy.