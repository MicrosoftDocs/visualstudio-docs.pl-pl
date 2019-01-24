---
title: Krok 7. Dodawanie składników okna dialogowego do formularza | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 051f88f81f443b1748ce3d8b0c9ce33e89fac77d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796662"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Krok 7. Dodawanie składników okna dialogowego do formularza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby umożliwić programowi otwieranie plików obrazów i Wybieranie koloru tła, w tym kroku należy dodać **OpenFileDialog** składnika i **ColorDialog** składnika do formularza.  
  
 Składnik to podobnie jak kontrolka pod pewnymi względami. Używasz przybornika, aby dodać składnik do formularza i ustaw jego właściwości, za pomocą **właściwości** okna. Jednak w przeciwieństwie do formantu, dodawanie składnika do formularza nie powoduje dodania widocznego elementu, który użytkownik może wyświetlić w formularzu. Zamiast tego zapewnia pewne zachowania, które mogą wyzwalać przy użyciu kodu. Jest składnik, który otwiera **Otwórz plik** okno dialogowe.  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 3](http://go.microsoft.com/fwlink/?LinkId=205213) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# — wideo 3](http://go.microsoft.com/fwlink/?LinkId=205202). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.  
  
### <a name="to-add-dialog-components-to-your-form"></a>Aby dodać elementy dialogu do formularza  
  
1.  Wybierz projektanta Windows Forms (Form1.cs [projekt] lub Form1.vb [projekt]), a następnie otwórz **okien dialogowych** grupy w przyborniku.  
  
    > [!NOTE]
    >  **Okien dialogowych** grupa w przyborniku zawiera składniki, które otwierają wiele przydatnych okien dialogowych, które mogą służyć do otwierania i zapisywania plików, przeglądania folderów i wybierania czcionek i kolorów. Używasz dwóch elementów dialogu w tym projekcie: **OpenFileDialog** i **ColorDialog**.  
  
2.  Aby dodać składnik o nazwie **openFileDialog1** do formularza, kliknij dwukrotnie **OpenFileDialog**. Aby dodać składnik o nazwie **colorDialog1** do formularza, kliknij dwukrotnie **ColorDialog** w przyborniku. (Możesz użyć go w następnym kroku samouczka). Powinieneś widzieć obszar w dolnej części projektanta formularzy Windows (poniżej formularza Picture Viewer), który zawiera ikonę dla każdego z dwóch składników dialogu, które dodałeś, jak pokazano na poniższej ilustracji.  
  
     ![Składniki okna dialogowego](../ide/media/express-dialogsadded.png "Express_DialogsAdded")  
Składniki okna dialogowego  
  
3.  Wybierz **openFileDialog1** ikonę w obszarze w dolnej części projektanta Windows Forms. Ustaw dwie właściwości:  
  
    -   Ustaw **filtru** właściwość następująco (możesz skopiować i wkleić):  
  
        ```  
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*  
        ```  
  
    -   Ustaw **tytuł** właściwości do następującego: **Wybierz plik obrazu**  
  
         **Filtru** ustawienia właściwości określają rodzaje typów plików, które będą wyświetlane w **wybierz obraz** okno dialogowe pliku.  
  
    > [!NOTE]
    >  Aby zobaczyć przykład **Otwórz plik** okno dialogowe w innej aplikacji, otwórz Notatnik lub Paint, a na pasku menu wybierz **pliku**, **Otwórz**. Zwróć uwagę, jak istnieje **pliki typu** listy rozwijanej u dołu. Użyłeś właśnie **filtru** właściwość **OpenFileDialog** składnik to skonfigurować. Zauważ również, jak **tytuł** i **filtru** właściwości są pogrubione w **właściwości** okna. IDE robi to, aby pokazać wszystkie właściwości, które zostały zmienione z wartościami domyślnymi.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 8: Pisanie kodu dla programu obsługi zdarzeń przycisku Obraz](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Nazw kontrolkom przycisków](../ide/step-6-name-your-button-controls.md).
