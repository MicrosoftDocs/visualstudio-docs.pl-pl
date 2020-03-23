---
title: 'Samouczek 1: Tworzenie przeglądarki obrazów'
ms.date: 10/16/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f1431d56516c749004cef1b35ada482a6c53446
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579724"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Samouczek 1: Tworzenie przeglądarki obrazów

W tym samouczku tworzysz aplikację, która ładuje obraz z pliku i wyświetla go w oknie. Dowiesz się, jak używać **Projektanta formularzy systemu Windows** do przeciągania formantów, takich jak przyciski i pola obrazów, do formularza, ustawiania ich właściwości i używania kontenerów do płynnej ponownego rozmiaru formularza. Możesz również rozpocząć pisanie kodu.

> [!NOTE]
> W tym samouczku omówiono zarówno język C#, jak i język Visual Basic, więc skup się na informacjach specyficznych dla używanego języka programowania.

W tym samouczku przedstawiono następujące zadania:

* Tworzenie nowego projektu.

* Test (debugowanie) aplikacji.

* Dodaj podstawowe kontrolki, takie jak pola wyboru i przyciski do formularza.

* Pozycjonuj formanty w formularzu przy użyciu układów.

* Dodawanie okien dialogowych **Otwieranie pliku** i **kolor** do formularza.

* Napisz kod przy użyciu intellisense i fragmenty kodu.

* Napisz metody obsługi zdarzeń.

Po zakończeniu aplikacja powinna wyglądać podobnie do następującego obrazu:

![Aplikacja Picture Viewer, którą tworzysz w tym samouczku](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Łącza do samouczka

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1: Tworzenie projektu aplikacji Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Rozpocznij od utworzenia projektu aplikacji Windows Forms.|
|[Krok 2: Uruchamianie aplikacji przeglądarki obrazów](../ide/step-2-run-your-program.md)|Uruchom projekt aplikacji Windows Forms, który został utworzony w poprzednim kroku.|
|[Krok 3: Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md)|Zmień wygląd formularza za pomocą okna **Właściwości.**|
|[Krok 4: Rozmieść formularz za pomocą kontrolki TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Dodaj `TableLayoutPanel` formant do formularza.|
|[Krok 5: Dodawanie kontrolek do formularza](../ide/step-5-add-controls-to-your-form.md)|Dodaj formanty, `PictureBox` takie `CheckBox` jak formant i formant, do formularza. Dodaj przyciski do formularza.|
|[Krok 6: Nadaj nazwy przyciskom](../ide/step-6-name-your-button-controls.md)|Zmień nazwę przycisków na coś bardziej znaczącego.|
|[Krok 7: Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md)|Dodaj `OpenFileDialog` komponent i `ColorDialog` komponent do formularza.|
|[Krok 8: Napisz kod dla programu obsługi zdarzeń przycisku obrazu](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Napisz kod za pomocą narzędzia IntelliSense.|
|[Krok 9: Przejrzyj, komentuj i przetestuj swój kod](../ide/step-9-review-comment-and-test-your-code.md)|Przejrzyj i przetestuj swój kod. W razie potrzeby dodaj komentarze.|
|[Krok 10: Napisz kod dodatkowych przycisków i pole wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Napisz kod, aby inne przyciski i pole wyboru działało przy użyciu programu IntelliSense.|
|[Krok 11: Uruchamianie aplikacji i wypróbowanie innych funkcji](../ide/step-11-run-your-program-and-try-other-features.md)|Uruchom aplikację i ustaw kolor tła. Wypróbuj inne funkcje, takie jak zmiana kolorów, czcionek i obramowań.|

Dostępne są również świetne, bezpłatne materiały do nauki wideo. Aby dowiedzieć się więcej o programowaniu w języku C#, zobacz [C# podstawy: Rozwój dla początkujących absolutnych](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej o programowaniu w języku Visual Basic, zobacz [Visual Basic podstawy: Rozwój dla początkujących .](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć samouczek, zacznij od **[kroku 1: Tworzenie projektu aplikacji formularzy systemu Windows](../ide/step-1-create-a-windows-forms-application-project.md)**.

## <a name="see-also"></a>Zobacz też

* [Więcej samouczków języka C#](/visualstudio/get-started/csharp/)
* [Samouczki dotyczące języka Visual Basic](/visualstudio/get-started/visual-basic/)
* [Samouczki języka C++](/cpp/get-started/tutorial-console-cpp)
