---
title: Generowanie szybkiej akcji konstruktora
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c8259841af4511bd782bca1be222353634638f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301812"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Generowanie konstruktora w programie Visual Studio

To generowanie kodu dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu dla nowego konstruktora w klasie.

**Kiedy:** Wprowadzasz nowy konstruktor i chcesz poprawnie zadeklarować go automatycznie lub zmodyfikować istniejącego konstruktora.

**Dlaczego?** Można zadeklarować konstruktora przed użyciem go, jednak ta funkcja wygeneruje go, z odpowiednimi parametrami, automatycznie. Ponadto modyfikowanie istniejącego konstruktora wymaga aktualizacji wszystkich callsites, chyba że używasz tej funkcji, aby zaktualizować je automatycznie.

**W jaki sposób:** Istnieje kilka sposobów generowania konstruktora:

- [Generowanie elementów konstrukcyjnych i elementów członkowskich](#pick)
- [Generowanie konstruktora z wybranych pól](#selection)
- [Generowanie konstruktora z nowego użycia](#usage)
- [Dodawanie parametru do istniejącego konstruktora](#addparameter)
- [Tworzenie i inicjowanie pola/właściwości z parametru konstruktora](#create)

## <a name="generate-constructor-and-pick-members-c-only"></a><a id = "pick"></a>Generowanie elementów konstrukcyjnych i elementów członkowskich pobrania (tylko w języku C#)

1. Umieść kursor w dowolnym pustym wierszu w klasie:

   ![Kursor w pustym wierszu](media/constructor1-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**
      - Kliknij ikonę ![Śrubokręt](media/screwdriver.png) ikona, która pojawia się na lewym marginesie, jeśli kursor tekstowy znajduje się już w pustym wierszu w klasie.

   ![Generowanie podglądu konstruktora](media/constructor1-preview-cs.png)

1. Z menu rozwijanego **wybierz polecenie Generuj konstruktora.**

   Zostanie otwarte okno dialogowe **Wybieranie członków.**

1. Wybierz elementy członkowskie, które chcesz uwzględnić jako parametry konstruktora. Można je zamówić za pomocą strzałek w górę i w dół. Wybierz pozycję **OK**.

   ![Okno dialogowe Wybieranie członków](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Można zaznaczyć pole wyboru **Dodaj czeki zerowe,** aby automatycznie generować czeki wartości null dla parametrów konstruktora.

   Konstruktor jest tworzony z określonymi parametrami.

   ![Generowanie wyniku konstruktora](media/constructor1-result-cs.png)

## <a name="generate-constructor-from-selected-fields-c-only"></a><a id="selection"></a>Generowanie konstruktora z wybranych pól (tylko w języku C#)

1. Wyróżnij członków, które chcesz mieć w wygenerowanym konstruktorze:

   ![Wyróżnianie członków](media/constructor2-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**
      - Kliknij ikonę ![Śrubokręt](media/screwdriver.png) ikonę, która pojawia się na lewym marginesie, jeśli kursor tekstowy znajduje się już w wierszu z zaznaczeniem.

      ![Generowanie podglądu konstruktora](media/constructor2-preview-cs.png)

1. Z menu rozwijanego **wybierz polecenie Generuj konstruktora "TypeName".**

   Konstruktor jest tworzony z wybranymi parametrami.

   ![Generowanie wyniku konstruktora](media/constructor2-result-cs.png)

## <a name="generate-constructor-from-new-usage-c-and-visual-basic"></a><a id="usage"></a>Generowanie konstruktora z nowego użycia (C# i Visual Basic)

1. Umieść kursor na linii, w której znajduje się czerwona falista. Czerwony squiggle wskazuje wywołanie konstruktora, który jeszcze nie istnieje.

   - C#:

       ![Wyróżniony kod C #](media/constructor-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/constructor-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**
      - Najedź kursorem na czerwoną falosę i kliknij przycisk ![błąd żarówki](media/error-bulb.png) pojawi się ikona.
      - Kliknij ikonę ![błąd żarówki](media/error-bulb.png) ikonę, która pojawia się na lewym marginesie, jeśli kursor tekstowy znajduje się już w wierszu z czerwoną faliczkiem.

      ![Generowanie podglądu konstruktora](media/constructor-preview-cs.png)

3. Z menu rozwijanego **wybierz polecenie Generuj konstruktora w '*TypeName*'.**

   > [!TIP]
   > Użyj łącza **Podgląd zmian** u dołu okna podglądu, [aby wyświetlić wszystkie zmiany,](../../ide/preview-changes.md) które zostaną wprowadzone przed dokonaniem wyboru.

   Konstruktor jest tworzony, z wszelkich parametrów wywnioskowane z jego użycia.

   - C#:

       ![Generowanie wyniku metody C #](media/constructor-result-cs.png)

   - Visual Basic:

       ![Generowanie wyniku metody VB](media/constructor-result-vb.png)

## <a name="add-parameter-to-existing-constructor-c-only"></a><a id="addparameter"></a>Dodaj parametr do istniejącego konstruktora (tylko C#)

1. Dodaj parametr do istniejącego wywołania konstruktora.

2. Umieść kursor w wierszu, w którym znajduje się czerwona falista wskazująca, że użyto konstruktora, który jeszcze nie istnieje.

    ![Generowanie podświetlenia konstruktora](media/constructor4-highlight-cs.png)

3. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**
      - Najedź kursorem na czerwoną falosę i kliknij przycisk ![błąd żarówki](media/error-bulb.png) pojawi się ikona.
      - Kliknij ikonę ![błąd żarówki](media/error-bulb.png) ikonę, która pojawia się na lewym marginesie, jeśli kursor tekstowy znajduje się już w wierszu z czerwoną faliczkiem.

      ![Generowanie podglądu konstruktora](media/constructor4-preview-cs.png)

4. Z menu rozwijanego wybierz **polecenie Dodaj parametr do "TypeName".**

   Parametr jest dodawany do konstruktora, z jego typem wywnioskowane z jego użycia.

   ![Generowanie wyniku konstruktora](media/constructor4-result-cs.png)

Można również dodać parametr do istniejącej metody. Aby uzyskać więcej informacji, zobacz [Dodawanie parametru do metody](add-parameter.md).

## <a name="create-and-initialize-a-field-or-property-from-a-constructor-parameter-c-only"></a><a id="create"></a>Tworzenie i inicjowanie pola lub właściwości z parametru konstruktora (tylko w języku C#)

1. Znajdź istniejący konstruktor i dodaj parametr:

   ![Generowanie podświetlenia konstruktora](media/constructor5-highlight-cs.png)

1. Umieść kursor wewnątrz nowo dodanego parametru.

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**
      - Kliknij ikonę ![Śrubokręt](media/screwdriver.png) ikonę, która pojawia się na lewym marginesie, jeśli kursor tekstowy znajduje się już w wierszu z dodanym parametrem.

   ![Generowanie podglądu konstruktora](media/constructor5-preview-cs.png)

1. Wybierz **polecenie Utwórz i zaiszcz właściwość** lub **Utwórz i zainiólj pole** z menu rozwijanego.

   Pole lub właściwość jest zadeklarowana i automatycznie nazwana w celu dopasowania do typów. Wiersz kodu jest również dodawany do inicjowania pola lub właściwości w treści konstruktora.

   ![Generowanie wyniku konstruktora](media/constructor5-result-cs.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
