---
title: 'Samouczek 1: Tworzenie przeglądarki obrazów'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ce0ae86e7b49867383351d9b2c045c4f4a50c96
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853615"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Samouczek 1: Tworzenie przeglądarki obrazów

W tym samouczku kompilujesz program, który ładuje obraz z pliku i wyświetla go w oknie. Dowiesz się, jak używać **Windows Forms Designer** przeciągać formanty, takie jak przyciski i pola obrazu w formularzu, ustawiać ich właściwości i używać kontenerów, aby sprawnie zmieniać rozmiar formularza. Można również rozpocząć pisanie kodu. Dowiesz się, jak:

-   Utwórz nowy projekt.

-   Testuj (Debuguj) aplikację.

-   Dodaj podstawowe formanty, takie jak pola wyboru i przyciski do formularza.

-   Położenie formantów w formularzu za pomocą układów.

-   Dodaj **Otwórz plik** i **kolor** do formularza przy użyciu okna dialogowego.

-   Pisz kod, używając funkcji IntelliSense i fragmentów kodu.

-   Opisz metody obsługi zdarzeń.

Po zakończeniu program będzie wyglądać jak na poniższym obrazie:

![Obraz tworzony w ramach tego samouczka](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Samouczek łącza

Aby pobrać pełną wersję przykładu, zobacz [przykładowy samouczek podglądu pełny obraz](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).

![Link do wideo](../data-tools/media/playvideo.gif)wersja wideo tego tematu, zobacz [jak: Tworzenie przeglądarki obrazów w języku Visual Basic? ](http://go.microsoft.com/fwlink/?LinkId=205207) lub [jak: Tworzenie przeglądarki obrazów w C#? ](http://go.microsoft.com/fwlink/?LinkId=205198).

> [!NOTE]
> W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio. Visual C# i Visual Basic zostały omówione w tym samouczku, więc Skoncentruj się na informacjach specyficznych dla języka programowania, którego używasz.
>
> Aby wyświetlić kod w języku Visual Basic, wybierz opcję **VB** u góry bloków kodu, a następnie, aby wyświetlić kod Visual C#, wybierz opcję **C#** kartę. Jeśli interesuje Cię Nauka języka Visual C++, zobacz [wprowadzenie](../ide/getting-started-with-cpp-in-visual-studio.md) i [samouczek języka C++](http://www.cplusplus.com/doc/tutorial/).
>
> Jeśli chcesz się dowiedzieć, jak pisanie aplikacji Visual C# lub Visual Basic platformy uniwersalnej systemu Windows, zobacz [kompilacji platformy uwp](https://developer.microsoft.com/windows/apps).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1: Utwórz projekt aplikacji Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Rozpocznij od utworzenia projektu aplikacji Windows Forms.|
|[Krok 2: Uruchom program](../ide/step-2-run-your-program.md)|Uruchom program aplikacji Windows Forms, który został utworzony w poprzednim kroku.|
|[Krok 3: Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md)|Zmień wygląd formularz za pomocą **właściwości** okna.|
|[Krok 4: Określić układ formularza z formantem TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Dodaj `TableLayoutPanel` formantu do formularza.|
|[Krok 5: Dodawanie formantów do formularza](../ide/step-5-add-controls-to-your-form.md)|Dodaj formanty, takie jak `PictureBox` kontroli i `CheckBox` formantu do formularza. Dodaj do formularza przyciski.|
|[Krok 6: Nazw kontrolkom przycisków](../ide/step-6-name-your-button-controls.md)|Zmień nazwy przycisków na nieco bardziej opisowe.|
|[Krok 7: Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md)|Dodaj `OpenFileDialog` składnika i `ColorDialog` składnika do formularza.|
|[Krok 8: Pisanie kodu dla programu obsługi zdarzeń przycisku obrazu](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Pisz kod, używając funkcji IntelliSense.|
|[Krok 9: Przejrzyj, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md)|Przejrzyj i przetestuj swój kod. W razie potrzeby dodaj komentarze.|
|[Krok 10: Pisanie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Napisz kod, aby inne przyciski i pole wyboru będą działać przy użyciu technologii IntelliSense.|
|[Krok 11: Uruchamianie programu i próbowanie innych funkcji](../ide/step-11-run-your-program-and-try-other-features.md)|Uruchom program i ustawić kolor tła. Spróbuj innych funkcji, takich jak zmienianie kolorów, czcionek i obramowania.|
