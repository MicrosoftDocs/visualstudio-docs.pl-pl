---
title: Tworzenie projektu programu Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f793e6ff468bdec6df499c5e5eb6b8524e9e4d5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650574"
---
# <a name="workflow-project-templates"></a>Szablony projektów przepływu pracy

Za pomocą szablonów projektów programu Visual Studio można tworzyć przepływy pracy, Windows Communication Foundation (WCF), działania niestandardowe i niestandardowe projektantów działań. W tym artykule opisano sposób tworzenia bibliotek i aplikacji z szablonami projektu dostępnymi w programie Visual Studio.

## <a name="create-a-workflow-project"></a>Tworzenie projektu przepływu pracy

Program Visual Studio udostępnia cztery różne szablony projektów przepływu pracy:

- Aplikacja konsolowa przepływu pracy

- Aplikacja usługi przepływu pracy WCF

- Biblioteka działań

- Biblioteka projektanta działań

Aby uzyskać dostęp do tych szablonów, najpierw Zainstaluj składnik **Windows Workflow Foundation** programu Visual Studio. Aby uzyskać szczegółowe instrukcje, zobacz [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Po zainstalowaniu składnika **Windows Workflow Foundation** wybierz pozycję **plik**  > **Nowy**  > **Project**.

1. Wyszukaj i wybierz szablon projektu przepływu pracy, na przykład szablon **aplikacji konsoli przepływu pracy** .

1. Kontynuuj, aby utworzyć projekt.

   > [!NOTE]
   > Jeśli chcesz dodać nowy projekt do istniejącego rozwiązania, Otwórz to rozwiązanie w programie Visual Studio, kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań**i wybierz polecenie **Dodaj**  > **Nowy projekt**.

## <a name="workflow-console-app"></a>Aplikacja konsolowa przepływu pracy

W przypadku wybrania szablonu **aplikacja konsoli przepływu pracy** program Visual Studio utworzy definicję przepływu pracy w języku XAML. Zostanie otwarty Projektant przepływu pracy i zostanie wyświetlona Kanwa utworzonego przepływu pracy. Aby utworzyć przepływ pracy, przeciągnij działania lub inne elementy przepływu pracy z **przybornika** do powierzchni projektowej.

## <a name="wcf-workflow-service-app"></a>Aplikacja usługi przepływu pracy WCF

W przypadku wybrania szablonu **aplikacja usługi przepływu pracy WCF** program Visual Studio utworzy definicję usługi jako kod XAML. Projektant przepływu pracy otwiera widok projektu z działaniem <xref:System.Activities.Statements.Sequence>, które zawiera zestaw działań <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>.

## <a name="activity-library"></a>Biblioteka działań

W przypadku wybrania szablonu **Biblioteka działań** program Visual Studio utworzy definicję działania w języku XAML. Projektant przepływu pracy zostanie otwarty i zostanie wyświetlona Kanwa niestandardowego działania. Przeciągnij działanie z **przybornika** na powierzchnię projektu, aby uwzględnić je w działaniu niestandardowym.

> [!NOTE]
> W treści działania niestandardowego można używać tylko jednego działania podrzędnego. Jednak działanie podrzędne może być działaniem złożonym, takim jak działanie <xref:System.Activities.Statements.Sequence> lub <xref:System.Activities.Statements.Flowchart>.

## <a name="activity-designer-library"></a>Biblioteka projektanta działań

W przypadku wybrania szablonu **Biblioteka programu Activity Designer** program Visual Studio tworzy definicję projektanta działań w języku XAML i plik implementacji związany z kodem. Zostanie otwarty Projektant przepływu pracy i zostanie wyświetlona Kanwa projektanta działań. Przeciągnij kontrolki Windows Presentation Foundation (WPF) z **przybornika** do powierzchni projektowej, aby użyć ich w niestandardowym projektancie działań.

Aby zapoznać się z przykładem sposobu implementacji niestandardowego projektanta działań, zobacz [How to: Create an Custom Activity Designer](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Niestandardowe Projektanci działań mogą służyć do działań niestandardowych i dla domyślnych działań programu .NET.

## <a name="see-also"></a>Zobacz także

- [Użyj Projektant przepływu pracy](developing-applications-with-the-workflow-designer.md)
- [Przepływy pracy projektowania (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)