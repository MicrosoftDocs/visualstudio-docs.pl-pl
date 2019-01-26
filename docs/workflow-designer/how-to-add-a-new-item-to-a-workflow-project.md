---
title: 'Projektant przepływu pracy — jak: Dodawanie nowego elementu do projektu przepływu pracy'
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8988c84ccc3cc1b13e76cff3eedf52083049a828
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936128"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Instrukcje: Dodaj nowy element do projektu przepływu pracy

Po utworzeniu projektu przepływu pracy działania przepływu pracy, projektantów i innych znanych elementów programu Visual Studio można dodać do projektu.

W poniższej tabeli wymieniono elementy Windows Workflow Foundation (WF), które można dodać do projektu przepływu pracy:


| Nazwa | Opis |
|-| - |
| Działanie | Działanie składa się z innymi działaniami. Wybranie tej pozycji dodaje ten sam plik XAML do projektu, jak można uzyskać po wybraniu **Biblioteka działań** szablonu dla nowego projektu. Aby uzyskać więcej informacji na temat z tej procedury zobacz [Tworzenie projektu przepływu pracy](creating-a-workflow-project.md). |
| Projektant działań | Projektant umożliwiający dostosowanie środowiska czasu projektowania, działania. Wybranie tej pozycji dodaje te same pliki do projektu, jak można uzyskać po wybraniu **Biblioteka projektanta działań** szablonu dla nowego projektu. |
| Działanie kodu | Działanie z logiką wykonywania zapisaną w kodzie. Plik kodu źródłowego za pomocą zastąpienia z <xref:System.Activities.CodeActivity.Execute%2A> metoda została już wygenerowana dla Ciebie. |
| Usługa przepływu pracy WCF | A [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] oferująca przy użyciu działań przepływu pracy. Wybranie tej pozycji dodaje te same pliki do projektu, jak można uzyskać po wybraniu **aplikacja usługi przepływu pracy WCF** szablonu dla nowego projektu. Aby uzyskać więcej informacji na temat tej procedury zobacz [jak: Tworzenie aplikacji usługi przepływu pracy WCF](/visualstudio/workflow-designer/creating-a-workflow-project). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Aby dodać nowy element do projektu przepływu pracy

1. Na **projektu** menu, wybierz opcję **Dodaj nowy element**.

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

1. W okienku po lewej stronie wybierz **przepływu pracy** kategorii, a następnie wybierz szablon elementu przepływu pracy.

   > [!NOTE]
   > Jeśli nie widzisz **przepływu pracy** kategorii, wcześniejszej instalacji **Windows Workflow Foundation** składnika programu Visual Studio 2017. Aby uzyskać szczegółowe instrukcje, zobacz [Instalowanie programu Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Wprowadź nazwę dla elementu w **nazwa** u dołu okna dialogowego.

1. Wybierz **Dodaj** można dodać elementu do projektu.

## <a name="see-also"></a>Zobacz także

- [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)