---
title: Krok 7. Dodawanie składników okna dialogowego do formularza
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
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
ms.openlocfilehash: 58721610a493283ff0bed8fca9cf6e6f6d668c4d
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293478"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Krok 7. Dodawanie składników okna dialogowego do formularza

Aby umożliwić programowi otwieranie plików obrazów i Wybieranie koloru tła, w tym kroku należy dodać <xref:System.Windows.Forms.OpenFileDialog> składnik <xref:System.Windows.Forms.ColorDialog> i składnik do formularza.

Składnik jest jak kontrolka na kilka sposobów. Za pomocą **przybornika** dodasz składnik do formularza i ustawisz jego właściwości przy użyciu okna **Właściwości** . Ale w przeciwieństwie do kontrolki Dodawanie składnika do formularza nie powoduje dodania widocznego elementu, który użytkownik może zobaczyć w formularzu. Zamiast tego zapewnia pewne zachowania, które można wyzwolić przy użyciu kodu. Jest to składnik, który otwiera okno dialogowe **Otwórz plik** .

## <a name="to-add-dialog-components-to-your-form"></a>Aby dodać składniki okna dialogowego do formularza

1. Wybierz **Projektant formularzy systemu Windows** (**Form1.cs [projekt]** ), a następnie otwórz grupę **okna dialogowe** w **przyborniku**.

    > [!NOTE]
    > Grupa **okien dialogowych** w **przyborniku** zawiera składniki otwierające wiele przydatnych okien dialogowych, które mogą być używane do otwierania i zapisywania plików, przeglądania folderów i wybierania czcionek i kolorów. W tym projekcie są używane dwa składniki okna dialogowego: OpenFileDialog i ColorDialog.

1. Aby dodać składnik o nazwie **openFileDialog1** do formularza, kliknij dwukrotnie pozycję **OpenFileDialog**. Aby dodać składnik o nazwie **colorDialog1** do formularza, kliknij dwukrotnie pozycję **ColorDialog** w **przyborniku**. (W następnym kroku samouczka używany jest ten krok). Powinien zostać wyświetlony obszar u dołu **Projektant formularzy systemu Windows** (poniżej formularza **przeglądarki obrazów** ), który ma ikonę dla każdego z dwóch składników okna dialogowego, które zostały dodane, jak pokazano na poniższej ilustracji.

     ![Składniki okna dialogowego](../ide/media/express_dialogsadded.png)<br>***Okno dialogowe*** *składniki*

1. Wybierz ikonę **openFileDialog1** w obszarze u dołu **Projektant formularzy systemu Windows**. Ustaw dwie właściwości:

    - Ustaw właściwość **Filter** na następującą (możesz ją skopiować i wkleić):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Ustaw właściwość **title** na następującą: **Wybierz plik obrazu**

         Ustawienia właściwości **filtru** określają rodzaje typów plików, które będą wyświetlane w oknie dialogowym Wybierz plik **obrazu** .

    > [!TIP]
    > Aby zobaczyć przykład okna dialogowego **Otwórz plik** w innej aplikacji, Otwórz program **Notepad** lub **Paint**, a następnie na pasku menu wybierz pozycję **plik** > **Otwórz**. Zwróć uwagę na to, jak znajduje się lista rozwijana obok nazwy pliku, który umożliwia wybranie typu pliku. <br/><br/>Po prostu użyto właściwości **Filter** w składniku **OpenFileDialog** , aby ustawić, że w aplikacji. Zwróć również uwagę na to, jak **tytuł** i właściwości **filtru** są pogrubione w oknie **Właściwości** . IDE robi to, aby wyświetlić wszystkie właściwości, które zostały zmienione z wartości domyślnych.

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz [krok 8: Napisz kod dla programu obsługi](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)zdarzeń przycisku Pokaż obraz.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6. Nadaj nazwę kontrolkom](../ide/step-6-name-your-button-controls.md)przycisków.

## <a name="see-also"></a>Zobacz także

* [Samouczek 2: Tworzenie quizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry zgodnej](tutorial-3-create-a-matching-game.md)
