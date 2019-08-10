---
title: Krok 11. Uruchamianie programu i wypróbowywanie innych funkcji
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43cb58c65131b5cc7e01b0f59306761a3b275dc7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925925"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Krok 11. Uruchamianie programu i wypróbowywanie innych funkcji
Program jest gotowy i gotowy do uruchomienia. Można uruchomić program i ustawić kolor <xref:System.Windows.Forms.PictureBox>tła. Aby dowiedzieć się więcej, spróbuj poprawić program, zmieniając kolor formularza, dostosowując przyciski i pole wyboru i zmieniając właściwości formularza.

Aby pobrać kompletną wersję przykładu, zobacz [przykładowy samouczek dotyczący programu Picture Viewer](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).

![link do wideo](../data-tools/media/playvideo.gif)dla wersji wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 5](http://go.microsoft.com/fwlink/?LinkId=205216) lub [samouczek 1: Utwórz przeglądarkę obrazów w C# pliku wideo 5.](http://go.microsoft.com/fwlink/?LinkId=205206) Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-run-your-program-and-set-the-background-color"></a>Aby uruchomić program i ustawić kolor tła

1. Wybierz **F5**lub na pasku menu wybierz **Debuguj** > **Rozpocznij debugowanie**.

2. Przed otwarciem obrazu wybierz przycisk **Ustaw kolor tła** . Zostanie otwarte okno dialogowe **koloru** .

     ![Okno dialogowe Kolor](../ide/media/express_colordialog.png)
okna dialogowego koloru

3. Wybierz kolor, aby ustawić kolor tła PictureBox. Dokładnie `backgroundButton_Click()` Obejrzyj metodę, aby zrozumieć, jak to działa.

    > [!NOTE]
    > Możesz załadować obraz z Internetu, wklejając jego adres URL do okna dialogowego **Otwórz plik** . Spróbuj znaleźć obraz z przezroczystym tłem, aby wyświetlić kolor tła.

4. Wybierz przycisk **Wyczyść obraz** , aby upewnić się, że został wyczyszczony. Następnie zamknij program, wybierając przycisk **Zamknij** .

## <a name="to-try-other-features"></a>Aby wypróbować inne funkcje

- Zmień kolor formularza i przycisków przy użyciu właściwości **BackColor** .

- Dostosuj przyciski i pola wyboru przy użyciu właściwości **Font** i **ForeColor** .

- Zmień właściwości **FormBorderStyle** i **ControlBox** formularza.

- Użyj właściwości **AcceptButton** i **CancelButton** formularza, aby przyciski były wybierane automatycznie, gdy użytkownik wybierze klawisz **Enter** lub **ESC** . Uruchom okno dialogowe **Otwórz plik** , gdy użytkownik wybierze **klawisz ENTER** i zamknie pole, gdy użytkownik wybierze **klawisz ESC**.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby dowiedzieć się więcej na temat programowania w programie Visual Studio, zobacz [pojęcia związane](https://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6)z programowaniem.

- Aby dowiedzieć się więcej na temat Visual Basic, zobacz [opracowywanie aplikacji z Visual Basic](/dotnet/visual-basic/developing-apps/index).

- Aby dowiedzieć się więcej C#na temat wizualizacji, zobacz [wprowadzenie do C# języka i .NET Framework](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework).

- Aby przejść do następnego samouczka, zobacz [samouczek 2: Utwórz Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md)matematyczny z limitem czasu.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 10: Napisz kod dla dodatkowych przycisków i pola](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)wyboru.
