---
title: Utwórz projekt Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 577bb58101556dc17c62453bfe18e9618c879405
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999954"
---
# <a name="workflow-project-templates"></a>Szablony projektów przepływu pracy

Przy użyciu szablonów projektów programu Visual Studio, można utworzyć przepływy pracy, usługi przepływu pracy usług Windows Communication Foundation (WCF), niestandardowych działań i projektanci działań niestandardowych. W tym artykule opisano sposób tworzenia bibliotek i aplikacji przy użyciu szablonów projektów dostępnych w programie Visual Studio.

## <a name="create-a-workflow-project"></a>Tworzenie projektu przepływu pracy

Program Visual Studio oferuje cztery różne szablony projektu przepływu pracy:

- Aplikacja konsoli przepływu pracy

- Aplikacja usługi przepływu pracy WCF

- Biblioteka działań

- Biblioteka projektanta działań

Aby uzyskać dostęp do tych szablonów, należy najpierw zainstalować **Windows Workflow Foundation** składnika programu Visual Studio 2017. Aby uzyskać szczegółowe instrukcje, zobacz [Instalowanie programu Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Po zainstalowaniu **Windows Workflow Foundation** składnika, otwórz **nowy projekt** okna dialogowego wybierając **pliku** > **New**  >  **Projektu**.

1. W okienku po lewej stronie wybierz **Visual C#**   >  **przepływu pracy** kategorii (lub **języka Visual Basic** > **przepływupracy** Jeśli wolisz języka Visual Basic).

1. W środkowym okienku wybierz szablon projektu, taki jak **Aplikacja konsoli przepływu pracy**.

1. W **nazwa** wprowadź opisową nazwę projektu ułatwić identyfikowanie.

1. W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub wybierz **Przeglądaj** można przejść do niego.

1. W **rozwiązania** wprowadź nazwę dla nowego rozwiązania. Wybierz **OK** do tworzenia aplikacji.

   > [!NOTE]
   > Jeśli chcesz dodać nowy projekt do istniejącego rozwiązania, otwórz rozwiązanie w programie Visual Studio kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań**i wybierz **Dodaj** > **New Projekt** otworzyć **nowy projekt** okno dialogowe.

## <a name="workflow-console-app"></a>Aplikacja konsoli przepływu pracy

Jeśli wybierzesz **Aplikacja konsoli przepływu pracy** szablon, Visual Studio tworzy definicję przepływu pracy w XAML. Projektant przepływu pracy otwiera i wyświetla kanwy dla przepływu pracy, który został utworzony. Do tworzenia przepływu pracy, przeciągnij działania lub inne elementy przepływu pracy z **przybornika** do powierzchni projektowej.

## <a name="wcf-workflow-service-app"></a>Aplikacja usługi przepływu pracy WCF

Jeśli wybierzesz **aplikacja usługi przepływu pracy WCF** szablon, Visual Studio tworzy definicję usługi jako XAML. Zostanie otwarty projektant przepływu pracy do widoku projektu za pomocą <xref:System.Activities.Statements.Sequence> działania, który zawiera zbiór <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań.

## <a name="activity-library"></a>Biblioteka działań

Jeśli wybierzesz **Biblioteka działań** szablon, Visual Studio umożliwia utworzenie definicji działania w XAML. Projektant przepływu pracy otwiera i wyświetla obszar roboczy dla działania niestandardowego. Przeciągnij działanie z **przybornika** do powierzchni projektu, które mają zostać objęte działanie niestandardowe.

> [!NOTE]
> Możesz tylko jeden element podrzędny działania w treści działanie niestandardowe. Jednak działania podrzędne może być złożone działania, takie jak <xref:System.Activities.Statements.Sequence> działania lub <xref:System.Activities.Statements.Flowchart> działania.

## <a name="activity-designer-library"></a>Biblioteka projektanta działań

Jeśli wybierzesz **Biblioteka projektanta działań** szablon, Visual Studio tworzy definicję projektanta działań w XAML i kodem pliku implementacji. Projektant przepływu pracy otwiera i wyświetla kanwy dla projektanta działań. Przeciągnij Windows Presentation Foundation (WPF) kontrolki z **przybornika** do powierzchni projektu, który z nich korzystać w swojej niestandardowego projektanta działań.

Na przykład sposób implementacji niestandardowego projektanta działań zobacz [jak: Tworzenie niestandardowego projektanta działań](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Niestandardowi Projektanci działań może służyć dla działań niestandardowych i domyślnych działań .NET Framework.

## <a name="see-also"></a>Zobacz także

- [Za pomocą projektanta przepływu pracy](developing-applications-with-the-workflow-designer.md)
- [Projektowanie przepływów pracy (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)