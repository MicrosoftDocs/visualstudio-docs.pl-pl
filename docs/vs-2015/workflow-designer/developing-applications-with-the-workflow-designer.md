---
title: Tworzenie aplikacji przy użyciu Projektant przepływu pracy | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848300c54800e229ee1f487fc415bad45d982a6c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656825"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Tworzenie aplikacji przy użyciu Projektanta przepływu pracy
@No__t_0 to wizualny Projektant i debuger służący do graficznego tworzenia i debugowania aplikacji [!INCLUDE[wf](../includes/wf-md.md)] w [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] hostowanym w [!INCLUDE[vs2010](../includes/vs2010-md.md)] środowisku deweloperskim. Umożliwia ona tworzenie złożonej aplikacji przepływu pracy, biblioteki działań lub usługi [!INCLUDE[indigo1](../includes/indigo1-md.md)] za pomocą szablonów i projektantów działań. [!INCLUDE[crabout](../includes/crabout-md.md)] przepływy pracy, [zobacz &#91;Windows Workflow Foundation .NET Framework&#93;4](https://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Poniżej przedstawiono kilka nowych funkcji projektowania, które ustawiają tę nową wersję [!INCLUDE[wfd2](../includes/wfd2-md.md)] niezależnie od starszych wersji [!INCLUDE[wfd2](../includes/wfd2-md.md)]:

- @No__t_0 jest tworzona przy użyciu [!INCLUDE[avalon1](../includes/avalon1-md.md)]. Usprawnia to środowisko projektanta działań i zwiększa wydajność dużych i złożonych przepływów pracy.

- Działania niestandardowe są teraz zaprojektowane z użyciem [!INCLUDE[avalon2](../includes/avalon2-md.md)] przy użyciu języka XAML i modelu programowania na potrzeby tworzenia projektantów działań.

- Działanie Flowchart zostało zaimplementowane, dzięki czemu można wizualizować przepływ programu przy użyciu znanego stylu modelowania schematu blokowego.

- @No__t_0 ma nowy Projektant zmiennych, który umożliwia deklarowanie i określanie zakresu zmiennych w przepływach pracy, powiązanie ich z działaniami.

- W [!INCLUDE[vs2010](../includes/vs2010-md.md)] [!INCLUDE[wfd2](../includes/wfd2-md.md)] udostępnia pełne funkcje IntelliSense podczas tworzenia wyrażeń Visual Basic w ramach przepływów pracy [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

- Środowisko debugowania jest teraz rozszerzane do języka XAML, co pozwala na ustawienie punktów przerwania w definicji przepływu pracy XAML i przechodzenie do kodu XAML w czasie wykonywania, który zapewnia środowisko podobne do tego w kodzie zarządzanym.

- Przehostowanie [!INCLUDE[wfd2](../includes/wfd2-md.md)] poza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest znacznie uproszczone w porównaniu z poprzednimi wersjami, a teraz wymaga tylko kilku wierszy kodu.

- Nowe działanie <xref:System.Activities.Statements.Flowchart> i jego [schemat blokowy](../workflow-designer/flowchart-activity-designer.md) umożliwiają wizualizowanie przepływu programu przy użyciu znanego stylu modelowania schematu blokowego.

- Działania związane z obsługą komunikatów zostały ulepszone, co pozwala na pisanie w pełni deklaratywnych (bez kodu) [!INCLUDE[indigo1](../includes/indigo1-md.md)] usług.

- **Dodaj odwołanie do usługi...** funkcja umożliwia generowanie działań automatycznie, które uzyskują dostęp do usług sieci Web.

## <a name="in-this-section"></a>W tej sekcji
 [Korzystanie z Projektant przepływu pracy](../workflow-designer/using-the-workflow-designer.md) Pokazuje, w jaki sposób tworzyć nowe działania i projekty przepływu pracy przy użyciu wbudowanych projektantów oraz jak korzystać z innych narzędzi udostępnianych przez projektanta do obsługi argumentów, zmiennych, wyrażeń, importów i nawigacji do stron nadrzędnych.

 [Korzystanie z projektantów działań](../workflow-designer/using-the-activity-designers.md) Opisuje kategorie działań i szablonów oraz ich projektantów, które są udostępniane przez system.

 [Debugowanie przepływów pracy za pomocą Projektant przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) Opisz sposób wykonywania tradycyjnych procedur debugowania, jak również debugowania XAML i wyrażeń.

 [Pomoc interfejsu użytkownika Projektant przepływu pracy](../workflow-designer/workflow-designer-ui-help.md) Zawiera tematy pomocy kontekstowej dla okien dialogowych udostępnianych przez [!INCLUDE[wfd1](../includes/wfd1-md.md)], a także wskazówki dotyczące funkcji powłoki projektanta, skrótów klawiaturowych i komunikatów o błędach.

 [Opracowywanie aplikacji przepływu pracy przeznaczonych dla platformy .net 3,0 lub .net 3,5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md) Zawiera wskazówki dotyczące korzystania ze starszego projektanta, który jest przeznaczony dla [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 [Rehostowanie przykładów &#91;&#93; WF przez projektanta](https://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d) Ten przykład pokazuje, jak utworzyć układ WPF, aby zawierał projektanta.

 [Projektanci działań niestandardowych](https://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075) Ta sekcja zawiera przykłady działań, które używają niestandardowych projektantów do wyświetlania w Projektancie przepływu pracy.