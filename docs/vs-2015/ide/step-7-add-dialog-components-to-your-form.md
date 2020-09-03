---
title: Krok 7. Dodawanie składników okna dialogowego do formularza | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40b90096f768a7dd836507c83dff935261a99a25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851138"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Krok 7. Dodawanie składników okna dialogowego do formularza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby umożliwić programowi otwieranie plików obrazów i Wybieranie koloru tła, w tym kroku należy dodać składnik **OpenFileDialog** i składnik **ColorDialog** do formularza.

 Składnik jest jak kontrolka na kilka sposobów. Za pomocą przybornika dodasz składnik do formularza i ustawisz jego właściwości przy użyciu okna **Właściwości** . Ale w przeciwieństwie do kontrolki Dodawanie składnika do formularza nie powoduje dodania widocznego elementu, który użytkownik może zobaczyć w formularzu. Zamiast tego zapewnia pewne zachowania, które można wyzwolić przy użyciu kodu. Jest to składnik, który otwiera okno dialogowe **Otwórz plik** .

 ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 3](https://msdn.microsoft.com/vbasic/gg315354.aspx) lub [Samouczek 1: Tworzenie przeglądarki obrazów w języku C# — wideo 3](https://msdn.microsoft.com/vcsharp/gg278411.aspx). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

### <a name="to-add-dialog-components-to-your-form"></a>Aby dodać składniki okna dialogowego do formularza

1. Wybierz Projektant formularzy systemu Windows (Form1.cs [projekt] lub Form1. vb [projekt]), a następnie otwórz grupę **okna dialogowe** w przyborniku.

    > [!NOTE]
    > Grupa **okien dialogowych** w przyborniku zawiera składniki otwierające wiele przydatnych okien dialogowych, które mogą być używane do otwierania i zapisywania plików, przeglądania folderów i wybierania czcionek i kolorów. W tym projekcie są używane dwa składniki okna dialogowego: **OpenFileDialog** i **ColorDialog**.

2. Aby dodać składnik o nazwie **openFileDialog1** do formularza, kliknij dwukrotnie pozycję **OpenFileDialog**. Aby dodać składnik o nazwie **colorDialog1** do formularza, kliknij dwukrotnie pozycję **ColorDialog** w przyborniku. (W następnym kroku samouczka używany jest ten krok). Powinien zostać wyświetlony obszar u dołu Projektant formularzy systemu Windows (poniżej formularza przeglądarki obrazów), który ma ikonę dla każdego z dwóch składników okna dialogowego, które zostały dodane, jak pokazano na poniższej ilustracji.

     ![Składniki okna dialogowego](../ide/media/express-dialogsadded.png "Express_DialogsAdded") Składniki okna dialogowego

3. Wybierz ikonę **openFileDialog1** w obszarze u dołu Projektant formularzy systemu Windows. Ustaw dwie właściwości:

    - Ustaw właściwość **Filter** na następującą (możesz ją skopiować i wkleić):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Ustaw właściwość **title** na następującą: **Wybierz plik obrazu**

         Ustawienia właściwości **filtru** określają rodzaje typów plików, które będą wyświetlane w oknie dialogowym Wybierz plik **obrazu** .

    > [!NOTE]
    > Aby zobaczyć przykład okna dialogowego **Otwórz plik** w innej aplikacji, Otwórz program Notepad lub Paint, a następnie na pasku menu wybierz **plik**, **Otwórz**. Zwróć uwagę na to, jak w dolnej części znajdują się pliki listy rozwijanej **typu** . Właściwość **Filter** w składniku **OpenFileDialog** została właśnie użyta w celu skonfigurowania tego ustawienia. Zwróć również uwagę na to, jak **tytuł** i właściwości **filtru** są pogrubione w oknie **Właściwości** . IDE robi to, aby wyświetlić wszystkie właściwości, które zostały zmienione z wartości domyślnych.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 8. Pisanie kodu dla programu obsługi zdarzeń przycisku Pokaż obraz](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6. nazwa kontrolek przycisku](../ide/step-6-name-your-button-controls.md).
