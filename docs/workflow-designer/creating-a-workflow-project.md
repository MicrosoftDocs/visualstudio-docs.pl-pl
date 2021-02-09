---
title: Tworzenie projektu programu Workflow Foundation
description: Dowiedz się, jak tworzyć biblioteki i aplikacje za pomocą szablonów projektów dostępnych w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cf8c0fe0b716cecee19c00bb0b300d4ffdc99355
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894364"
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

1. Po zainstalowaniu składnika **Windows Workflow Foundation** wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

1. Wyszukaj i wybierz szablon projektu przepływu pracy, na przykład szablon **aplikacji konsoli przepływu pracy** .

1. Kontynuuj, aby utworzyć projekt.

   > [!NOTE]
   > Jeśli chcesz dodać nowy projekt do istniejącego rozwiązania, Otwórz to rozwiązanie w programie Visual Studio, kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.

## <a name="workflow-console-app"></a>Aplikacja konsolowa przepływu pracy

W przypadku wybrania szablonu **aplikacja konsoli przepływu pracy** program Visual Studio utworzy definicję przepływu pracy w języku XAML. Zostanie otwarty Projektant przepływu pracy i zostanie wyświetlona Kanwa utworzonego przepływu pracy. Aby utworzyć przepływ pracy, przeciągnij działania lub inne elementy przepływu pracy z **przybornika** do powierzchni projektowej.

## <a name="wcf-workflow-service-app"></a>Aplikacja usługi przepływu pracy WCF

W przypadku wybrania szablonu **aplikacja usługi przepływu pracy WCF** program Visual Studio utworzy definicję usługi jako kod XAML. Projektant przepływu pracy otwiera widok projektu z <xref:System.Activities.Statements.Sequence> działaniem zawierającym zestaw <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działania.

## <a name="activity-library"></a>Biblioteka działań

W przypadku wybrania szablonu **Biblioteka działań** program Visual Studio utworzy definicję działania w języku XAML. Projektant przepływu pracy zostanie otwarty i zostanie wyświetlona Kanwa niestandardowego działania. Przeciągnij działanie z **przybornika** na powierzchnię projektu, aby uwzględnić je w działaniu niestandardowym.

> [!NOTE]
> W treści działania niestandardowego można używać tylko jednego działania podrzędnego. Jednak działanie podrzędne może być działaniem złożonym, takim jak <xref:System.Activities.Statements.Sequence> działanie lub <xref:System.Activities.Statements.Flowchart> działanie.

## <a name="activity-designer-library"></a>Biblioteka projektanta działań

W przypadku wybrania szablonu **Biblioteka programu Activity Designer** program Visual Studio tworzy definicję projektanta działań w języku XAML i plik implementacji związany z kodem. Zostanie otwarty Projektant przepływu pracy i zostanie wyświetlona Kanwa projektanta działań. Przeciągnij kontrolki Windows Presentation Foundation (WPF) z **przybornika** do powierzchni projektowej, aby użyć ich w niestandardowym projektancie działań.

Aby zapoznać się z przykładem sposobu implementacji niestandardowego projektanta działań, zobacz [How to: Create an Custom Activity Designer](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Niestandardowe Projektanci działań mogą służyć do działań niestandardowych i dla domyślnych działań programu .NET.

## <a name="see-also"></a>Zobacz też

- [Używanie Projektanta przepływu pracy](developing-applications-with-the-workflow-designer.md)
- [Przepływy pracy projektowania (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)
