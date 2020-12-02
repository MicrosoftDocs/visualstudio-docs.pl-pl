---
title: 'Samouczek 1: Tworzenie przeglądarki obrazów'
description: Dowiedz się, jak utworzyć aplikację, która ładuje obraz z pliku i wyświetla go w oknie.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1c0eea844b04cbe8ba261fd4d65a6d21fb99aa4b
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479137"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Samouczek 1: Tworzenie przeglądarki obrazów

W tym samouczku utworzysz aplikację, która ładuje obraz z pliku i wyświetla go w oknie. Dowiesz się, jak za pomocą **Projektant formularzy systemu Windows** przeciągać formanty, takie jak przyciski i pola obrazu w formularzu, ustawiać ich właściwości i korzystać z kontenerów w celu bezproblemowego zmiany rozmiaru formularza. Zacznij również pisać kod.

> [!NOTE]
> Ten samouczek obejmuje języki C# i Visual Basic, dlatego należy skoncentrować się na informacjach specyficznych dla języka programowania, którego używasz.

Ten samouczek przeprowadzi Cię przez następujące zadania:

* Tworzenie nowego projektu.

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
|[Krok 4. Określanie układu formularza przy użyciu kontrolki TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Dodaj `TableLayoutPanel` kontrolkę do formularza.|
|[Krok 5. Dodawanie kontrolek do formularza](../ide/step-5-add-controls-to-your-form.md)|Dodaj kontrolki, takie jak `PictureBox` kontrolka i `CheckBox` kontrolka, do formularza. Dodaj przyciski do formularza.|
|[Krok 6. Nadawanie nazw kontrolkom przycisków](../ide/step-6-name-your-button-controls.md)|Zmień nazwy przycisków na bardziej zrozumiałe.|
|[Krok 7. Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md)|Dodaj `OpenFileDialog` składnik i `ColorDialog` składnik do formularza.|
|[Krok 8. Pisanie kodu dla programu obsługi zdarzeń przycisku Pokaż obraz](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Napisz kod przy użyciu narzędzia IntelliSense.|
|[Krok 9. Przeglądanie, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md)|Przejrzyj i Przetestuj swój kod. Dodaj komentarze zgodnie z wymaganiami.|
|[Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Napisz kod, aby inne przyciski i pole wyboru działały przy użyciu funkcji IntelliSense.|
|[Krok 11. Uruchamianie aplikacji i wypróbowywanie innych funkcji](../ide/step-11-run-your-program-and-try-other-features.md)|Uruchom aplikację i Ustaw kolor tła. Wypróbuj inne funkcje, takie jak Zmienianie kolorów, czcionek i obramowań.|

Dostępne są również wspaniałe, bezpłatne zasoby szkoleniowe dotyczące wideo. Aby dowiedzieć się więcej na temat programowania w języku C#, zobacz [podstawy języka c#: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat programowania w Visual Basic, zobacz [Visual Basic podstawy: Programowanie dla bezwzględnych początkujących](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć pracę z samouczkiem, Zacznij od **[kroku 1: Tworzenie projektu aplikacji Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)**.

## <a name="see-also"></a>Zobacz też

* [Więcej samouczków dotyczących języka C#](../get-started/csharp/index.yml)
* [Samouczki Visual Basic](../get-started/visual-basic/index.yml)
* [Samouczki języka C++](/cpp/get-started/tutorial-console-cpp)