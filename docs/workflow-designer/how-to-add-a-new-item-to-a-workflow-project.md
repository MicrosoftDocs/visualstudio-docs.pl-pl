---
title: 'Projektant przepływu pracy: Dodawanie nowego elementu do projektu przepływu pracy'
ms.date: 06/25/2018
ms.topic: conceptual
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5cdea5b3cbf99ab8213c320acc82665816062dca
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189637"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Instrukcje: Dodawanie nowego elementu do projektu przepływu pracy

Po utworzeniu projektu przepływu pracy można dodać do projektu działania przepływu pracy, projektanci i inne znane elementy programu Visual Studio.

W poniższej tabeli wymieniono elementy Windows Workflow Foundation (WF), które można dodać do projektu przepływu pracy:

| Nazwa | Opis |
|-| - |
| Działanie | Działanie składające się z innych działań. Wybranie tego elementu powoduje dodanie tego samego pliku XAML do projektu, jak uzyskano podczas wybierania szablonu **biblioteki działań** dla nowego projektu. Aby uzyskać więcej informacji na temat tej procedury, zobacz [Tworzenie projektu przepływu pracy](creating-a-workflow-project.md). |
| Projektant działań | Projektant umożliwiający dostosowanie środowiska czasu projektowania działania. Wybranie tego elementu powoduje dodanie do projektu tych samych plików jak w przypadku wybrania szablonu **biblioteki projektanta działań** dla nowego projektu. |
| Działanie kodu | Działanie z logiką wykonywania zapisaną w kodzie. Plik kodu źródłowego z przesłonięciem metody <xref:System.Activities.CodeActivity.Execute%2A> jest już wygenerowany dla Ciebie. |
| Usługa przepływu pracy WCF | Usługa [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] utworzona przy użyciu działań przepływu pracy. Wybranie tego elementu powoduje dodanie do projektu tych samych plików, co podczas wybierania szablonu **aplikacji usługi przepływu pracy WCF** dla nowego projektu. Aby uzyskać więcej informacji na temat tej procedury, zobacz [jak: Tworzenie aplikacji usługi przepływu pracy WCF](creating-a-workflow-project.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Aby dodać nowy element do projektu przepływu pracy

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

   Zostanie otwarte okno dialogowe **Dodaj nowy element** .

1. W okienku po lewej stronie wybierz kategorię **przepływ pracy** , a następnie wybierz szablon elementu przepływu pracy.

   > [!NOTE]
   > Jeśli nie widzisz kategorii **przepływu pracy** , najpierw zainstaluj składnik **Windows Workflow Foundation** programu Visual Studio. Aby uzyskać szczegółowe instrukcje, zobacz [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Wprowadź nazwę dla elementu w polu **Nazwa** w dolnej części okna dialogowego.

1. Wybierz pozycję **Dodaj** , aby dodać element do projektu.

## <a name="see-also"></a>Zobacz także

- [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)