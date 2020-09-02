---
title: 'Instrukcje: Tworzenie obsługi zdarzeń w projektach pakietu Office'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: ee85d89dcb990cebd595dadbd7b28add4a7b371a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538310"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Instrukcje: Tworzenie obsługi zdarzeń w projektach pakietu Office
  Istnieje kilka sposobów tworzenia programów obsługi zdarzeń w Visual Basic i C#. W widoku Projekt można utworzyć domyślne programy obsługi zdarzeń dla kontrolek, klikając dwukrotnie formant lub korzystając z okienka zdarzenia okna **Właściwości** , aby utworzyć programy obsługi dla każdego zdarzenia na kontrolce. Jeśli jednak Jesteś w widoku kodu, możesz nie chcieć przełączyć się do widok Projekt, aby utworzyć procedurę obsługi zdarzeń.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>Aby utworzyć procedurę obsługi zdarzeń w Visual Basic

1. Z listy rozwijanej **Nazwa klasy** w górnej części edytora kodu wybierz obiekt, dla którego chcesz utworzyć procedurę obsługi zdarzeń.

    > [!NOTE]
    > Jeśli chcesz utworzyć programy obsługi zdarzeń dla `ThisDocument` lub `ThisWorkbook` , musisz wybrać **(ThisDocument Events)** lub **(zdarzenia ThisWorkbook)** na liście rozwijanej **Nazwa klasy**

2. Z listy rozwijanej **Nazwa metody** w górnej części edytora kodu wybierz zdarzenie.

     Program Visual Studio tworzy program obsługi zdarzeń i przenosi punkt wstawiania do nowo utworzonego programu obsługi zdarzeń. Jeśli program obsługi zdarzeń już istnieje, punkt wstawiania zostanie przeniesiony do istniejącego programu obsługi zdarzeń.

### <a name="to-create-an-event-handler-in-c"></a>Aby utworzyć procedurę obsługi zdarzeń w języku C\#

1. Utwórz delegata zdarzenia w zdarzeniu **uruchamiania** klasy, wpisując kwalifikowaną nazwę zdarzenia, a następnie spację, a następnie wpisując **+=** bez odstępów. Na przykład:

     `this.<object name>.<event name> +=`

2. Na końcu wiersza kodu naciśnij dwukrotnie klawisz TAB.

     Program Visual Studio automatycznie uzupełnia wiersz kodu, tworzy program obsługi zdarzeń i przenosi punkt wstawiania do nowo utworzonego programu obsługi zdarzeń.

## <a name="see-also"></a>Zobacz też
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Przewodnik: program dla zdarzeń kontrolki NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
