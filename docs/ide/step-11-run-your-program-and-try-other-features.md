---
title: Krok 11. Uruchamianie programu i próbowanie innych funkcji
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f37018a7ccc642b06382308b366644d5580d4cc
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853277"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Krok 11. Uruchamianie programu i próbowanie innych funkcji
Program jest gotowy i gotowa do uruchomienia. Możesz uruchomić program i ustawić kolor tła <xref:System.Windows.Forms.PictureBox>. Aby dowiedzieć się więcej, spróbuj poprawić program zmieniając kolor formularza, dostosowując przyciski i pole wyboru i zmieniając właściwości formularza.

 Aby pobrać pełną wersję przykładu, zobacz [przykładowy samouczek podglądu pełny obraz](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).

 ![Link do wideo](../data-tools/media/playvideo.gif)wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 5](http://go.microsoft.com/fwlink/?LinkId=205216) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# -5 wideo](http://go.microsoft.com/fwlink/?LinkId=205206). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-run-your-program-and-set-the-background-color"></a>Aby uruchomić program i ustawić kolor tła

1.  Wybierz **F5**, lub na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie**.

2.  Przed otwarciem obrazu wybierz **Ustaw kolor tła** przycisku. **Kolor** zostanie otwarte okno dialogowe.

     ![Okno dialogowe kolorów](../ide/media/express_colordialog.png)
**kolor** okno dialogowe

3.  Wybierz kolor, aby ustawić kolor tła PictureBox. Przyjrzyj się bliżej `backgroundButton_Click()` metodę, aby zrozumieć, jak to działa.

    > [!NOTE]
    >  Możesz załadować obraz z Internetu wklejając jego adres URL do **Otwórz plik** okno dialogowe. Spróbuj odnaleźć obraz z przezroczystym tłem, więc pojawia się kolor tła.

4.  Wybierz **Wyczyść obraz** przycisk, aby upewnić się, czy to powoduje wyczyszczenie. Następnie zamknij program, wybierając **Zamknij** przycisku.

## <a name="to-try-other-features"></a>Aby wypróbować inne funkcje

-   Zmień kolor formularza i przyciski za pomocą **BackColor** właściwości.

-   Dostosuj przyciski i pola wyboru za pomocą **czcionki** i **ForeColor** właściwości.

-   Zmień formularza **FormBorderStyle** i **ControlBox** właściwości.

-   Użyj formularza **AcceptButton** i **CancelButton** właściwości, tak aby przyciski są wybierane automatycznie kiedy użytkownik naciśnie **Enter** lub **Esc** klucza. Ten program był otwarty **Otwórz plik** okno dialogowe, gdy użytkownik wybierze **Enter** i zamknąć okno, gdy użytkownik wybierze **Esc**.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby dowiedzieć się więcej na temat programowania w programie Visual Studio, zobacz [pojęcia związane z programowaniem](https://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6).

-   Aby dowiedzieć się więcej na temat języka Visual Basic, zobacz [opracowywania aplikacji za pomocą Visual Basic](/dotnet/visual-basic/developing-apps/index).

-   Aby dowiedzieć się więcej na temat Visual C#, zobacz [wprowadzenie do C# języka i platformy .NET Framework](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework).

-   Aby przejść do następnego samouczka, zobacz [samouczek 2: Utwórz quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 10: Pisanie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
