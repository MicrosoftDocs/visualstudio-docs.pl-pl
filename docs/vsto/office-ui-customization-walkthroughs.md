---
title: Wskazówki dotyczące dostosowywania interfejsu użytkownika pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes, walkthroughs
- smart documents, walkthroughs
- walkthroughs [Office development in Visual Studio], smart tags
- walkthroughs [Office development in Visual Studio], action panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 95561f1404da1efd71ff3418f9154392f393795c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977890"
---
# <a name="office-ui-customization-walkthroughs"></a>Wskazówki dotyczące dostosowywania interfejsu użytkownika pakietu Office
  Poniższe instruktaże przedstawiają że sposoby dostosowywania użytkowników interfejsu aplikacji pakietu Microsoft Office za pomocą dostosowań na poziomie dokumentu i dodatków narzędzi VSTO.

## <a name="actions-pane-walkthroughs"></a>Wskazówki dotyczące okienka akcji
- [Przewodnik: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md) pokazuje, jak tworzyć okienka akcji w dokumencie programu Word. W okienku Akcje zawiera dwie kontrolki, które wysyłają dane wejściowe użytkownika do dokumentu.

- [Przewodnik: Wiązanie danych z kontrolkami w okienku akcji programu Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md) pokazuje, jak powiązać kontrolkami w okienku akcji programu Word z danymi. Formanty pokazują wzorzec/szczegół relacji między tabelami w bazie danych programu SQL Server.

- [Przewodnik: Wiązanie danych z kontrolkami w okienku akcji programu Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md) zawiera opis sposobu dodawania formantów, które są powiązane ze źródłem danych do okienka akcji w programie Excel.

## <a name="custom-task-pane-walkthroughs"></a>Wskazówki dotyczące okienko zadania niestandardowego
- [Przewodnik: Automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md) przedstawia sposób tworzenia niestandardowego okienka zadań, który zawiera formant, który automatyzuje aplikacji hosta, gdy użytkownik kliknie kontrolkę.

- [Przewodnik: Synchronizuj niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md) przedstawia sposób tworzenia niestandardowego okienka zadań, które użytkownicy mogą ukryć lub wyświetlić, klikając przycisk przełącznika na Wstążce.

- [Przewodnik: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md) pokazuje sposób wyświetlania unikatowego wystąpienia niestandardowego okienka zadań w każdej wiadomości e-mail, który został utworzony lub otwarty w programie Outlook.

## <a name="ribbon-walkthroughs"></a>Wskazówki dotyczące wstążki
- [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md) pokazuje, jak utworzyć kartę niestandardowa Wstążka przy użyciu projektanta wstążki. Karta zawiera przycisk, który może służyć do ukryć lub wyświetlić okienka akcji.

- [Przewodnik: Aktualizowanie formantów na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md) pokazuje, jak aktualizowanie formantów na Wstążce po załadowaniu wstążki do aplikacji pakietu Office za pomocą modelu obiektów wstążki.

- [Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md) pokazuje, jak utworzyć kartę niestandardowa Wstążka za pomocą XML wstążki, a nie przy użyciu projektanta wstążki.

## <a name="controls-on-word-documents"></a>Formanty w dokumentach programu Word
- [Przewodnik: Dodawanie formantów do dokumentów w czasie wykonywania w dodatku narzędzi VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md) pokazuje, jak dodać kontrolki do dokumentu za pomocą dodatku narzędzi VSTO.

- [Przewodnik: Zmiana formatowania dokumentu za pomocą formantów CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md) pokazuje, jak zmienianie formatowania w dokumencie programu Word za pomocą pól wyboru w dostosowaniu na poziomie dokumentu.

- [Przewodnik: Wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md) pokazuje, jak używać przycisków i pola tekstowe w dokumentach programu Word.

- [Przewodnik: Aktualizacja wykresu w dokumencie za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md) pokazuje, jak zmienić styl wykresu w dokumencie programu Word za pomocą przycisków opcji w dostosowaniu na poziomie dokumentu.

## <a name="controls-on-excel-worksheets"></a>Formanty w arkuszach Excel
- [Przewodnik: Dodawanie formantów do arkusza w czasie wykonywania w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) przedstawiono sposób dodawania formantów do arkusza za pomocą dodatku narzędzi VSTO.

- [Przewodnik: Zmiana formatowania arkusza za pomocą formantów CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md) pokazuje podstawy używania pola wyboru w arkuszu programu Excel, aby zmienić formatowanie.

- [Przewodnik: Wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md) pokazuje podstawy używania przycisków i pola tekstowe w arkuszach programu Excel.

- [Przewodnik: Aktualizacja wykresu w arkuszu za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md) przedstawiono podstawowe informacje dotyczące zmiany stylów wykresu za pomocą przycisków opcji w arkuszu programu Excel.

## <a name="see-also"></a>Zobacz także
- [Wskazówki dotyczące przy użyciu programu Word](../vsto/walkthroughs-using-word.md)
- [Wskazówki dotyczące za pomocą programu Excel](../vsto/walkthroughs-using-excel.md)
- [Dane w wskazówki dotyczące rozwiązań pakietu Office](../vsto/data-in-office-solutions-walkthroughs.md)
- [Wskazówki dotyczące wdrażania i zabezpieczeń](../vsto/security-and-deployment-walkthroughs.md)
- [Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Typowe zadania w programowaniu pakietu Office](../vsto/common-tasks-in-office-programming.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
