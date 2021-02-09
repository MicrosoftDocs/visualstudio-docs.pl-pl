---
title: 'Instrukcje: Tworzenie obsługi zdarzeń w projektach pakietu Office'
description: Dowiedz się więcej o kilku sposobach tworzenia domyślnych programów obsługi zdarzeń dla formantów w Visual Basic i C#.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b2aed6102b6aed5938ecfab826363e62dcfac48a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889424"
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
