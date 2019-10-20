---
title: Generuj szybką akcję konstruktora
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 41bb9a0e3921495629a10d6783432e8b4999a117
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661738"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Generowanie konstruktora w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu dla nowego konstruktora w klasie.

**Kiedy:** Wprowadzasz nowy Konstruktor i chcesz go prawidłowo zadeklarować automatycznie lub zmodyfikować istniejący Konstruktor.

**Dlaczego:** Konstruktor można zadeklarować przed użyciem, jednak ta funkcja będzie generować ją z odpowiednimi parametrami, automatycznie. Ponadto modyfikowanie istniejącego konstruktora wymaga aktualizacji wszystkich callsites, chyba że ta funkcja jest używana do automatycznego aktualizowania.

**Jak:** Istnieje kilka sposobów generowania konstruktora:

- [Generuj konstruktora i wybieraj członków](#pick)
- [Generuj Konstruktor z wybranych pól](#selection)
- [Generuj Konstruktor na podstawie nowego użycia](#usage)
- [Dodaj parametr do istniejącego konstruktora](#addparameter)
- [Utwórz i zainicjuj pole/właściwość z parametru konstruktora](#create)

## <a id = "pick"></a>Generuj konstruktora i wybieraj elementyC# członkowskie (tylko)

1. Umieść kursor w dowolnym pustym wierszu w klasie:

   ![Kursor w pustym wierszu](media/constructor1-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Kliknij ikonę ![śrubokręt](media/screwdriver.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w pustym wierszu w klasie.

   ![Generuj Podgląd konstruktora](media/constructor1-preview-cs.png)

1. Wybierz pozycję **Generuj Konstruktor** z menu rozwijanego.

   Zostanie otwarte okno dialogowe **Wybierz członków** .

1. Wybierz elementy członkowskie, które mają być dołączane jako parametry konstruktora. Można je zamówić przy użyciu strzałek w górę i w dół. Wybierz **przycisk OK**.

   ![Okno dialogowe wyboru członków](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Można zaznaczyć pole wyboru **Dodaj sprawdzanie wartości null** , aby automatycznie generować sprawdzanie wartości null dla parametrów konstruktora.

   Konstruktor jest tworzony z określonymi parametrami.

   ![Generuj wynik konstruktora](media/constructor1-result-cs.png)

## <a id="selection"></a>Generuj Konstruktor z wybranych pól (C# tylko)

1. Zaznacz członków, których chcesz mieć w wygenerowanym konstruktorze:

   ![Wyróżnij elementy członkowskie](media/constructor2-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Kliknij ikonę ![śrubokręt](media/screwdriver.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z zaznaczeniem.

      ![Generuj Podgląd konstruktora](media/constructor2-preview-cs.png)

1. Wybierz pozycję **Generuj Konstruktor "TypeName (...)"** z menu rozwijanego.

   Konstruktor jest tworzony z wybranymi parametrami.

   ![Generuj wynik konstruktora](media/constructor2-result-cs.png)

## <a id="usage"></a>Generuj Konstruktor na podstawie nowego użyciaC# (i Visual Basic)

1. Umieść kursor w wierszu, w którym znajduje się czerwona zygzakowata. Czerwona zygzakowata wskazuje wywołanie konstruktora, który jeszcze nie istnieje.

   - C#:

       ![Wyróżniony kodC#](media/constructor-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/constructor-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Umieść kursor na czerwono, a następnie kliknij przycisk ![Żarówka błędów](media/error-bulb.png) zostanie wyświetlona ikona.
      - Kliknij ikonę ![Żarówka błędów](media/error-bulb.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z czerwonym obramowaniem.

      ![Generuj Podgląd konstruktora](media/constructor-preview-cs.png)

3. Wybierz pozycję **Generuj Konstruktor w elemencie "*TypeName*"** z menu rozwijanego.

   > [!TIP]
   > Użyj linku **Podgląd zmian** w dolnej części okna Podgląd, [Aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) , które zostaną wprowadzone przed dokonaniem wyboru.

   Konstruktor jest tworzony, z dowolnego parametru wywnioskowanego z jego użycia.

   - C#:

       ![Generowanie wyniku metodyC#](media/constructor-result-cs.png)

   - Visual Basic:

       ![Generuj wynik metody VB](media/constructor-result-vb.png)

## <a id="addparameter"></a>Dodaj parametr do istniejącego konstruktora (C# tylko)

1. Dodaj parametr do istniejącego wywołania konstruktora.

2. Umieść kursor w wierszu, w którym znajduje się czerwony zygzak wskazujący, że użyto konstruktora, który jeszcze nie istnieje.

    ![Wyróżnij generowanie konstruktora](media/constructor4-highlight-cs.png)

3. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Umieść kursor na czerwono, a następnie kliknij przycisk ![Żarówka błędów](media/error-bulb.png) zostanie wyświetlona ikona.
      - Kliknij ikonę ![Żarówka błędów](media/error-bulb.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z czerwonym obramowaniem.

      ![Generuj Podgląd konstruktora](media/constructor4-preview-cs.png)

4. Wybierz pozycję **Dodaj parametr do elementu "TypeName (...)"** z menu rozwijanego.

   Parametr jest dodawany do konstruktora, z którego typ został wywnioskowany na podstawie jego użycia.

   ![Generuj wynik konstruktora](media/constructor4-result-cs.png)

Możesz również dodać parametr do istniejącej metody. Aby uzyskać więcej informacji, zobacz [Dodawanie parametru do metody](add-parameter.md).

## <a id="create"></a>Utwórz i zainicjuj pole lub właściwość z parametru konstruktora (C# tylko)

1. Znajdź istniejący Konstruktor i Dodaj parametr:

   ![Wyróżnij generowanie konstruktora](media/constructor5-highlight-cs.png)

1. Umieść kursor wewnątrz nowo dodanego parametru.

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Kliknij ikonę ![śrubokręt](media/screwdriver.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z dodanym parametrem.

   ![Generuj Podgląd konstruktora](media/constructor5-preview-cs.png)

1. Wybierz opcję **Utwórz i zainicjuj Właściwość** lub **Utwórz i zainicjuj pole** z menu rozwijanego.

   Pole lub właściwość są zadeklarowane i automatycznie nazwane, aby odpowiadały typom. Wiersz kodu jest również dodawany do zainicjowania pola lub właściwości w treści konstruktora.

   ![Generuj wynik konstruktora](media/constructor5-result-cs.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)