---
title: 'Samouczek 1: Tworzenie przeglądarki obrazów'
ms.date: 08/30/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 803bd02b43b290cba4a3afe7bc7040e0dee1e2eb
ms.sourcegitcommit: 6993bcb0d2b0067b1b7b7899bfba52c31c70b7e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095336"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Samouczek 1: Tworzenie przeglądarki obrazów

W tym samouczku utworzysz aplikację, która ładuje obraz z pliku i wyświetla go w oknie. Dowiesz się, jak za pomocą **Projektant formularzy systemu Windows** przeciągać formanty, takie jak przyciski i pola obrazu w formularzu, ustawiać ich właściwości i korzystać z kontenerów w celu bezproblemowego zmiany rozmiaru formularza. Zacznij również pisać kod.

> [!NOTE]
> Ten samouczek obejmuje wizualizacje C# i Visual Basic, dlatego należy skoncentrować się na informacjach specyficznych dla języka programowania, którego używasz.

Ten samouczek przeprowadzi Cię przez następujące zadania:

* Utwórz nowy projekt.

* Testowanie (Debugowanie) aplikacji.

* Dodaj podstawowe kontrolki, takie jak pola wyboru i przyciski do formularza.

* Kontrolki położenia w formularzu przy użyciu układów.

* Dodaj okna dialogowe **otwieranie pliku** i **koloru** do formularza.

* Napisz kod przy użyciu funkcji IntelliSense i fragmentów kodu.

* Napisz metody obsługi zdarzeń.

Po zakończeniu aplikacja powinna wyglądać podobnie do poniższej ilustracji:

![Aplikacja przeglądarka obrazów utworzona w tym samouczku](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Linki samouczków

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1. Tworzenie projektu aplikacji Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Zacznij od utworzenia projektu aplikacji Windows Forms.|
|[Krok 2. Uruchamianie aplikacji Przeglądarka obrazów](../ide/step-2-run-your-program.md)|Uruchom projekt aplikacji Windows Forms, który został utworzony w poprzednim kroku.|
|[Krok 3. Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md)|Zmień wygląd formularza przy użyciu okna **Właściwości** .|
|[Krok 4. Układanie formularza przy użyciu kontrolki TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|`TableLayoutPanel` Dodaj kontrolkę do formularza.|
|[Krok 5. Dodawanie kontrolek do formularza](../ide/step-5-add-controls-to-your-form.md)|Dodaj kontrolki, takie jak `PictureBox` kontrolka `CheckBox` i kontrolka, do formularza. Dodaj przyciski do formularza.|
|[Krok 6. Nadaj nazwę kontrolkom przycisków](../ide/step-6-name-your-button-controls.md)|Zmień nazwy przycisków na bardziej zrozumiałe.|
|[Krok 7. Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md)|`OpenFileDialog` Dodaj składnik`ColorDialog` i składnik do formularza.|
|[Krok 8. Napisz kod dla programu obsługi zdarzeń przycisku Pokaż obraz](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Napisz kod przy użyciu narzędzia IntelliSense.|
|[Krok 9. Przeglądanie, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md)|Przejrzyj i Przetestuj swój kod. Dodaj komentarze zgodnie z wymaganiami.|
|[Krok 10. Napisz kod dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Napisz kod, aby inne przyciski i pole wyboru działały przy użyciu funkcji IntelliSense.|
|[Krok 11. Uruchom aplikację i wypróbuj inne funkcje](../ide/step-11-run-your-program-and-try-other-features.md)|Uruchom aplikację i Ustaw kolor tła. Wypróbuj inne funkcje, takie jak Zmienianie kolorów, czcionek i obramowań.|

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć pracę z samouczkiem, **Zacznij od [kroku 1: Utwórz projekt](../ide/step-1-create-a-windows-forms-application-project.md)** aplikacji Windows Forms.

## <a name="see-also"></a>Zobacz także

* [Więcej C# samouczków](/visualstudio/get-started/csharp/)
* [Samouczki Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++Podręcznik](/cpp/get-started/tutorial-console-cpp)
