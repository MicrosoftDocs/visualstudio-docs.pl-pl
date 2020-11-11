---
title: 'Projektant przepływu pracy: Dodawanie nowego elementu do projektu przepływu pracy'
description: Dowiedz się, jak dodawać do projektu działania przepływu pracy, projektanci i inne znane elementy programu Visual Studio po utworzeniu projektu przepływu pracy.
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: how-to
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af6563d21ce41d54e66f474de126c3bd4070ff8a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437973"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Instrukcje: Dodawanie nowego elementu do projektu przepływu pracy

Po utworzeniu projektu przepływu pracy można dodać do projektu działania przepływu pracy, projektanci i inne znane elementy programu Visual Studio.

W poniższej tabeli wymieniono elementy Windows Workflow Foundation (WF), które można dodać do projektu przepływu pracy:

| Nazwa | Opis |
|-| - |
| Działanie | Działanie składające się z innych działań. Wybranie tego elementu powoduje dodanie tego samego pliku XAML do projektu, jak uzyskano podczas wybierania szablonu **biblioteki działań** dla nowego projektu. Aby uzyskać więcej informacji na temat tej procedury, zobacz [Tworzenie projektu przepływu pracy](creating-a-workflow-project.md). |
| Projektant działań | Projektant umożliwiający dostosowanie środowiska czasu projektowania działania. Wybranie tego elementu powoduje dodanie do projektu tych samych plików jak w przypadku wybrania szablonu **biblioteki projektanta działań** dla nowego projektu. |
| Działanie kodu | Działanie z logiką wykonywania zapisaną w kodzie. Plik kodu źródłowego z przesłonięciem <xref:System.Activities.CodeActivity.Execute%2A> metody jest już wygenerowany dla Ciebie. |
| Usługa przepływu pracy WCF | [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]Usługa skompilowana przy użyciu działań przepływu pracy. Wybranie tego elementu powoduje dodanie do projektu tych samych plików, co podczas wybierania szablonu **aplikacji usługi przepływu pracy WCF** dla nowego projektu. Aby uzyskać więcej informacji na temat tej procedury, zobacz [jak: Tworzenie aplikacji usługi przepływu pracy WCF](creating-a-workflow-project.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Aby dodać nowy element do projektu przepływu pracy

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

   Zostanie otwarte okno dialogowe **Dodaj nowy element** .

1. W okienku po lewej stronie wybierz kategorię **przepływ pracy** , a następnie wybierz szablon elementu przepływu pracy.

   > [!NOTE]
   > Jeśli nie widzisz kategorii **przepływu pracy** , najpierw zainstaluj składnik **Windows Workflow Foundation** programu Visual Studio. Aby uzyskać szczegółowe instrukcje, zobacz [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Wprowadź nazwę dla elementu w polu **Nazwa** w dolnej części okna dialogowego.

1. Wybierz pozycję **Dodaj** , aby dodać element do projektu.

## <a name="see-also"></a>Zobacz też

- [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)
