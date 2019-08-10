---
title: Krok 7. Dodawanie składników okna dialogowego do formularza
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf6769535082e49d891c7065cc18eb05967dc192
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925869"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Krok 7. Dodawanie składników okna dialogowego do formularza
Aby umożliwić programowi otwieranie plików obrazów i Wybieranie koloru tła, w tym kroku należy dodać <xref:System.Windows.Forms.OpenFileDialog> składnik <xref:System.Windows.Forms.ColorDialog> i składnik do formularza.

Składnik jest jak kontrolka na kilka sposobów. Za pomocą **przybornika** dodasz składnik do formularza i ustawisz jego właściwości przy użyciu okna **Właściwości** . Ale w przeciwieństwie do kontrolki Dodawanie składnika do formularza nie powoduje dodania widocznego elementu, który użytkownik może zobaczyć w formularzu. Zamiast tego zapewnia pewne zachowania, które można wyzwolić przy użyciu kodu. Jest to składnik, który otwiera okno dialogowe **Otwórz plik** .

![link do wideo](../data-tools/media/playvideo.gif)dla wersji wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 3](http://go.microsoft.com/fwlink/?LinkId=205213) lub [samouczek 1: Utwórz przeglądarkę obrazów w C# pliku wideo 3.](http://go.microsoft.com/fwlink/?LinkId=205202) Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-add-dialog-components-to-your-form"></a>Aby dodać składniki okna dialogowego do formularza

1. Wybierz **Projektant formularzy systemu Windows** (**Form1.cs [projekt]** lub **Form1. vb [projekt]** ), a następnie otwórz grupę **okna dialogowe** w przyborniku.

    > [!NOTE]
    > Grupa **okien dialogowych** w **przyborniku** zawiera składniki otwierające wiele przydatnych okien dialogowych, które mogą być używane do otwierania i zapisywania plików, przeglądania folderów i wybierania czcionek i kolorów. W tym projekcie są używane dwa składniki okna dialogowego: OpenFileDialog i ColorDialog.

2. Aby dodać składnik o nazwie **openFileDialog1** do formularza, kliknij dwukrotnie pozycję **OpenFileDialog**. Aby dodać składnik o nazwie **colorDialog1** do formularza, kliknij dwukrotnie pozycję **ColorDialog** w przyborniku. (W następnym kroku samouczka używany jest ten krok). Powinien zostać wyświetlony obszar u dołu **Projektant formularzy systemu Windows** (poniżej formularza **przeglądarki obrazów** ), który ma ikonę dla każdego z dwóch składników okna dialogowego, które zostały dodane, jak pokazano na poniższej ilustracji.

     ![Składniki okna](../ide/media/express_dialogsadded.png)
**dialogowego** składników okna dialogowego

3. Wybierz ikonę **openFileDialog1** w obszarze u dołu **Projektant formularzy systemu Windows**. Ustaw dwie właściwości:

    - Ustaw właściwość **Filter** na następującą (możesz ją skopiować i wkleić):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Ustaw właściwość **title** na następującą: **Wybierz plik obrazu**

         Ustawienia właściwości **filtru** określają rodzaje typów plików, które będą wyświetlane w oknie dialogowym Wybierz plik **obrazu** .

    > [!NOTE]
    > Aby zobaczyć przykład okna dialogowego **Otwórz plik** w innej aplikacji, Otwórz program **Notepad** lub **Paint**, a następnie na pasku menu wybierz pozycję **plik** > **Otwórz**. Zwróć uwagę na to, jak w dolnej części znajdują się pliki listy rozwijanej **typu** . Właściwość **Filter** w składniku **OpenFileDialog** została właśnie użyta w celu skonfigurowania tego ustawienia. Zwróć również uwagę na to, jak **tytuł** i właściwości **filtru** są pogrubione w oknie **Właściwości** . IDE robi to, aby wyświetlić wszystkie właściwości, które zostały zmienione z wartości domyślnych.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 8: Napisz kod dla programu obsługi](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)zdarzeń przycisku Pokaż obraz.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6. Nadaj nazwę kontrolkom](../ide/step-6-name-your-button-controls.md)przycisków.
