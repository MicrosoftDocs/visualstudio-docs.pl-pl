---
title: 'Samouczek 1: Tworzenie przeglądarki obrazów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c56eb091e6d4efbe33dc8f05d5040272307c274
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299909"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Samouczek 1: Tworzenie podglądu obrazów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym samouczku utworzysz program, który ładuje obraz z pliku i wyświetla go w oknie. Dowiesz się, jak przeciągać formanty, takie jak przyciski i pola obrazu w formularzu, ustawiać ich właściwości i bezproblemowo zmieniać rozmiar formularza za pomocą kontenerów. Zacznij również pisać kod. Dowiesz się, jak:

- Utwórz nowy projekt.

- Testowanie (Debugowanie) aplikacji.

- Dodaj podstawowe kontrolki, takie jak pola wyboru i przyciski do formularza.

- Kontrolki położenia w formularzu przy użyciu układów.

- Dodaj okna dialogowe **otwieranie pliku** i **koloru** do formularza.

- Napisz kod przy użyciu funkcji IntelliSense i fragmentów kodu.

- Napisz metody obsługi zdarzeń.

  Po zakończeniu program będzie wyglądać jak na poniższej ilustracji.

  ![Obraz utworzony w tym samouczku](../ide/media/express-pictureviewerdone.png "Express_PictureViewerDone") Obraz utworzony w tym samouczku

  ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [How to: Create a Picture Viewer in Visual Basic?](https://go.microsoft.com/fwlink/?LinkId=205207) lub [How to: Create a Picture Viewer in C#?](https://go.microsoft.com/fwlink/?LinkId=205198).

> [!NOTE]
> Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio. Wizualizacje C# i Visual Basic zostały omówione w tym samouczku, dlatego należy skoncentrować się na informacjach specyficznych dla języka programowania, którego używasz.
>
> Aby wyświetlić kod dla Visual Basic, wybierz kartę **VB** w górnej części bloków kodu i aby wyświetlić kod wizualizacji C#, wybierz **C#** kartę. Jeśli interesują Cię informacje o wizualizacji C++, zobacz samouczek [wprowadzenie](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) i [ C++ języka](http://www.cplusplus.com/doc/tutorial/).
>
> Jeśli chcesz dowiedzieć się, jak pisać wizualizacje C# lub Visual Basic aplikacje dla Sklepu Windows, zobacz [Tworzenie pierwszej aplikacji do sklepu Windows przy użyciu C# lub Visual Basic](https://msdn.microsoft.com/library/windows/apps/hh974581.aspx). Aby uzyskać informacje na temat tworzenia aplikacji JavaScript dla Sklepu Windows, zobacz [Tworzenie pierwszej aplikacji do sklepu Windows przy użyciu języka JavaScript](https://msdn.microsoft.com/library/windows/apps/br211385.aspx).

## <a name="related-topics"></a>Tematy pokrewne

|Stanowisko|Opis|
|-----------|-----------------|
|[Krok 1. Tworzenie projektu aplikacji Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Zacznij od utworzenia projektu aplikacji Windows Forms.|
|[Krok 2. Uruchamianie programu](../ide/step-2-run-your-program.md)|Uruchom program aplikacji Windows Forms, który został utworzony w poprzednim kroku.|
|[Krok 3. Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md)|Zmień wygląd formularza przy użyciu okna **Właściwości** .|
|[Krok 4. Określanie układu formularza przy użyciu kontrolki TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Dodaj kontrolkę `TableLayoutPanel` do formularza.|
|[Krok 5. Dodawanie kontrolek do formularza](../ide/step-5-add-controls-to-your-form.md)|Dodawanie kontrolek, takich jak kontrolka `PictureBox` i kontrolka `CheckBox`, do formularza. Dodaj przyciski do formularza.|
|[Krok 6. Nadawanie nazw kontrolkom przycisków](../ide/step-6-name-your-button-controls.md)|Zmień nazwy przycisków na bardziej zrozumiałe.|
|[Krok 7. Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md)|Dodaj składnik **OpenFileDialog** i składnik **ColorDialog** do formularza.|
|[Krok 8. Tworzenie kodu procedury obsługi zdarzeń dla przycisku Pokaż obraz](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Napisz kod przy użyciu narzędzia IntelliSense.|
|[Krok 9. Przegląd, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md)|Przejrzyj i Przetestuj swój kod. Dodaj komentarze zgodnie z wymaganiami.|
|[Krok 10. Tworzenie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Napisz kod, aby inne przyciski i pole wyboru działały przy użyciu funkcji IntelliSense.|
|[Krok 11. Uruchamianie programu i wypróbowanie innych funkcji](../ide/step-11-run-your-program-and-try-other-features.md)|Uruchom program i Ustaw kolor tła. Wypróbuj inne funkcje, takie jak Zmienianie kolorów, czcionek i obramowań.|
