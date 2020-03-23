---
title: 'Krok 7: Dodawanie składników okna dialogowego do formularza'
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9697bf6cf84c2a74daac2017b4f63d52a7019b6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579278"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Krok 7: Dodawanie składników okna dialogowego do formularza

Aby umożliwić aplikacji otwieranie plików obrazów i wybieranie koloru tła, w tym kroku należy dodać <xref:System.Windows.Forms.OpenFileDialog> składnik i <xref:System.Windows.Forms.ColorDialog> składnik do formularza.

Składnik jest jak formant pod pewnymi względami. **Przybornik** służy do dodawania składnika do formularza i ustawia jego właściwości za pomocą okna **Właściwości.** Jednak w przeciwieństwie do formantu dodanie składnika do formularza nie dodaje widocznego elementu, który użytkownik może zobaczyć w formularzu. Zamiast tego zapewnia pewne zachowania, które można wyzwolić za pomocą kodu. Jest to składnik, który otwiera okno dialogowe **Otwórz plik.**

## <a name="to-add-dialog-components-to-your-form"></a>Aby dodać składniki okna dialogowego do formularza

1. Wybierz **projektanta formularzy systemu Windows** (**Form1.cs [Projekt]**), a następnie otwórz grupę **Okna dialogowe** w **przyborniku**.

    > [!NOTE]
    > Grupa **Okna dialogowe** w **przyborniku** zawiera składniki, które otwierają wiele przydatnych okien dialogowych, które mogą być używane do otwierania i zapisywania plików, przeglądania folderów oraz wybierania czcionek i kolorów. W tym projekcie użyto dwóch składników okna dialogowego: OpenFileDialog i ColorDialog.

1. Aby dodać składnik o nazwie **openFileDialog1** do formularza, kliknij dwukrotnie przycisk **OpenFileDialog**. Aby dodać składnik o nazwie **colorDialog1** do formularza, kliknij dwukrotnie **colordialog** w **przyborniku**. (Używasz tego w następnym kroku samouczka.) W dolnej części programu **Windows Forms Designer** (pod formularzem **Podgląd obrazów)** powinien zostać wyświetlony obszar zawierający ikonę dla każdego z dwóch dodanych składników okna dialogowego, jak pokazano na poniższej ilustracji.

     ![Składniki okna dialogowego](../ide/media/express_dialogsadded.png)<br>*Składniki* ***okna dialogowego***

1. Wybierz ikonę **openFileDialog1** w obszarze u dołu **projektanta formularzy systemu Windows**. Ustaw dwie właściwości:

    - Ustaw właściwość **Filter** na następującą (można ją skopiować i wkleić):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Ustaw właściwość **Title** na następującą: **Wybierz plik obrazu**

         Ustawienia właściwości **Filtruj** określają rodzaje typów plików, które będą wyświetlane w oknie **dialogowym Wybieranie** pliku obrazu.

    > [!TIP]
    > Aby wyświetlić przykład okna dialogowego **Otwieranie pliku** w innej aplikacji, otwórz **Notatnik** lub **Paint,** a na pasku menu wybierz pozycję**Otwórz** **plik** > . Zwróć uwagę, jak obok nazwy pliku znajduje się lista rozwijana, która umożliwia wybranie typu pliku. <br/><br/>Właśnie użyto **Filter** właściwości w **OpenFileDialog** składnika, aby skonfigurować go w aplikacji. Ponadto należy zauważyć, jak **tytuł** i **filtr** właściwości są pogrubione w oknie **Właściwości.** IDE robi to, aby pokazać wszystkie właściwości, które zostały zmienione z ich wartości domyślnych.

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[Krok 8: Napisz kod dla programu obsługi zdarzeń przycisku pokaż obraz](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)**.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 6: Nadaj nazw przyciskom .](../ide/step-6-name-your-button-controls.md)

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie quizu matematycznego z czasem](tutorial-2-create-a-timed-math-quiz.md)
* [samouczek 3: Tworzenie pasującej gry](tutorial-3-create-a-matching-game.md)
