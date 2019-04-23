---
title: 'Instrukcje: Tworzenie obsługi zdarzeń w projektach pakietu Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 577b12be220e2a695609db6c508d7aaf69c79f92
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054524"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Instrukcje: Tworzenie obsługi zdarzeń w projektach pakietu Office
  Istnieje kilka sposobów, aby utworzyć procedury obsługi zdarzeń w języku Visual Basic i C#. W widoku Projekt, możesz utworzyć domyślny procedury obsługi zdarzeń dla kontrolek przez dwukrotne kliknięcie formantu lub za pomocą okienka zdarzenia z **właściwości** okna, aby utworzyć procedury obsługi dla dowolnego zdarzenia w formancie. Jednak jeśli jesteś w widoku kodu, może nie chcesz przełączyć do widoku projektu, aby utworzyć program obsługi zdarzeń.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>Aby utworzyć program obsługi zdarzeń w języku Visual Basic

1. Z **Nazwa klasy** listy rozwijanej u góry strony edytora kodu, zaznacz obiekt, który chcesz utworzyć program obsługi zdarzeń dla.

    > [!NOTE]
    >  Jeśli chcesz tworzyć programy obsługi zdarzeń dla `ThisDocument` lub `ThisWorkbook`, musisz wybrać **(ThisDocument zdarzenia)** lub **(ThisWorkbook zdarzenia)** w **Nazwa klasy**listy rozwijanej

2. Z **nazwę metody** listy rozwijanej u góry strony edytora kodu, wybierz zdarzenie.

     Visual Studio tworzy program obsługi zdarzeń i przenosi punkt wstawiania do nowo utworzonego zdarzenia programu obsługi. Jeśli program obsługi zdarzeń już istnieje, punkt wstawiania przechodzi do istniejącego programu obsługi zdarzeń.

### <a name="to-create-an-event-handler-in-c"></a>Aby utworzyć program obsługi zdarzeń w języku C\#

1. Utwórz delegata zdarzenia w **uruchamiania** zdarzeń klasy przez wpisanie nazwy kwalifikowanej zdarzeń, spację, a następnie wpisując **+=** później bez spacji. Na przykład:

     `this.<object name>.<event name> +=`

2. Na końcu wiersza kodu naciśnij klawisz TAB dwa razy.

     Visual Studio automatycznie zakończy wiersz kodu, tworzy program obsługi zdarzeń i przenosi punkt wstawiania do nowo utworzonego zdarzenia programu obsługi.

## <a name="see-also"></a>Zobacz także
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Przewodnik: Program w odniesieniu do zdarzeń formantu NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
