---
title: 'Projektant przepływu pracy: Dodawanie nowego elementu do projektu przepływu pracy'
ms.date: 06/25/2018
ms.topic: conceptual
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7bedc36af2e8fbe19fbb3cc85d82be09d8673de
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593957"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Instrukcje: Dodawanie nowego elementu do projektu przepływu pracy

Po utworzeniu projektu przepływu pracy można dodać do projektu działania przepływu pracy, projektanci i inne znane elementy programu Visual Studio.

W poniższej tabeli wymieniono elementy Windows Workflow Foundation (WF), które można dodać do projektu przepływu pracy:

| Nazwa | Opis |
|-| - |
| Działanie | Działanie składające się z innych działań. Wybranie tego elementu powoduje dodanie tego samego pliku XAML do projektu, jak uzyskano podczas wybierania szablonu **biblioteki działań** dla nowego projektu. Aby uzyskać więcej informacji na temat tej procedury, zobacz [Tworzenie projektu przepływu pracy](creating-a-workflow-project.md). |
| Projektant czynności | Projektant umożliwiający dostosowanie środowiska czasu projektowania działania. Wybranie tego elementu powoduje dodanie do projektu tych samych plików jak w przypadku wybrania szablonu **biblioteki projektanta działań** dla nowego projektu. |
| Działanie kodu | Działanie z logiką wykonywania zapisaną w kodzie. Plik kodu źródłowego z przesłonięciem metody <xref:System.Activities.CodeActivity.Execute%2A> jest już wygenerowany dla Ciebie. |
| Usługa przepływu pracy WCF | Usługa [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] utworzona przy użyciu działań przepływu pracy. Wybranie tego elementu powoduje dodanie do projektu tych samych plików, co podczas wybierania szablonu **aplikacji usługi przepływu pracy WCF** dla nowego projektu. Aby uzyskać więcej informacji na temat tej procedury, zobacz [jak: Tworzenie aplikacji usługi przepływu pracy WCF](creating-a-workflow-project.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Aby dodać nowy element do projektu przepływu pracy

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

1. W okienku po lewej stronie wybierz kategorię **przepływ pracy** , a następnie wybierz szablon elementu przepływu pracy.

   > [!NOTE]
   > Jeśli nie widzisz kategorii **przepływu pracy** , najpierw zainstaluj składnik **Windows Workflow Foundation** programu Visual Studio. Aby uzyskać szczegółowe instrukcje, zobacz [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Wprowadź nazwę dla elementu w polu **Nazwa** w dolnej części okna dialogowego.

1. Wybierz pozycję **Dodaj** , aby dodać element do projektu.

## <a name="see-also"></a>Zobacz także

- [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)
