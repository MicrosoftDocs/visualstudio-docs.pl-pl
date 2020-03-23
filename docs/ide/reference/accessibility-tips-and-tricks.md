---
title: Porady i wskazówki dotyczące ułatwień dostępu dla programu Visual Studio
description: Dowiedz się więcej o poradach i wskazówkach, które mogą pomóc w ułatwienia korzystania ze zintegrowanego środowiska programistycznego programu Visual Studio (IDE) dla wszystkich osób niepełnosprawnych, w tym dla osób niepełnosprawnych.
ms.date: 08/06/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5828fb114a4df559c46dd6ae7f64887ab48e7429
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68919523"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Porady i wskazówki dotyczące ułatwień dostępu dla programu Visual Studio

Visual Studio ma wbudowane funkcje ułatwień dostępu, które są zgodne z czytnikami ekranu i innymi technologiami pomocniczymi. Niezależnie od tego, czy chcesz używać skrótów klawiaturowych do poruszania się po ideu, czy używać motywów o wysokim kontraście, aby poprawić widoczność, na tej stronie znajdziesz kilka wskazówek & dotyczących tego, jak to zrobić.

Omówimy również, jak używać adnotacji do ujawnienia przydatnych informacji o kodzie i jak ustawić sygnały dźwiękowe dla zdarzeń kompilacji i punktu przerwania.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [Ułatwienia dostępu dla programu Visual Studio dla komputerów Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Zapisywanie ustawień IDE

Środowisko IDE można dostosować, zapisując układ okna, schemat mapowania klawiatury i inne preferencje. Aby uzyskać więcej informacji, zobacz [Personalizowanie ide programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Modyfikowanie środowiska IDE w celu wyświetlania w celu uzyskania wysokiego kontrastu

Dla niektórych ludzi, niektóre kolory są trudniejsze do zobaczenia. Jeśli chcesz więcej kontrastu podczas kodu, ale nie chcesz używać typowych motywów "Wysoki kontrast", teraz oferujemy motyw "Niebieski (dodatkowy kontrast)".

  ![Porównaj kompozycję Niebieski i Niebieski dodatkowy kontrast](media/blue-extra-contrast-theme.png "Zrzut ekranu przedstawiający porównanie motywu Niebieski i motywu Niebieski kontrast dodatkowy")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Użyj adnotacji, aby wyświetlić przydatne informacje o kodzie

Edytor programu Visual Studio zawiera wiele "ozdoby" tekstu, które pozwalają wiedzieć o cechach i funkcji w określonych punktach w wierszu kodu, takich jak ikony śrubokręta i żarówki, błąd i ostrzeżenie "squiggles", zakładki i tak dalej. Możesz użyć polecenia "Pokaż adnotacje linii", aby ułatwić odnajdywanie, a następnie nawigowanie między tymi ozdobami.

  ![Użyj zestawu poleceń Pokaż adnotacje wiersza](media/show-line-annotations-command-set.png "Zrzut ekranu przedstawiający element menu Pokaż adnotacje wiersza")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Dostęp do pasków narzędzi przy użyciu skrótów klawiaturowych

Ide programu Visual Studio ma paski narzędzi, podobnie jak wiele okien narzędzi. Poniższe skróty klawiaturowe ułatwiają dostęp do nich.

|Funkcja|Opis|Skrót klawiaturowy|
|-------------|-----------------| - |
|Paski narzędzi IDE|Wybierz pierwszy przycisk na pasku narzędzi Standardowy.|**Alt**, **Ctrl**+**Karta**|
|Paski narzędzi okna narzędzi|Przenoszenie fokusu na paski narzędzi w oknie narzędzia. <br> <br> **UWAGA:** Działa to w przypadku większości okien narzędzi, ale tylko wtedy, gdy fokus znajduje się w oknie narzędzia. Ponadto należy wybrać klawisz SHIFT przed klawiszem ALT. W niektórych oknach narzędzi, takich jak Eksplorator zespołu, przed wybraniem klawisza ALT należy przytrzymać klawisz SHIFT przez chwilę.|**Klawisz Shift**+**Alt**|
|Paski narzędzi|Przejdź do pierwszego elementu na następnym pasku narzędzi (gdy pasek narzędzi ma fokus).|**Ctrl**+**Karta** Ctrl|

### <a name="other-useful-keyboard-shortcuts"></a>Inne przydatne skróty klawiaturowe

Niektóre inne przydatne skróty klawiaturowe są następujące.

|Funkcja|Opis|Skrót klawiaturowy|
|-------------|-----------------| - |
|IDE|Włączanie i wyłączanie wysokiego kontrastu. <br> <br> **UWAGA:** Standardowy skrót klawiaturowy systemu Windows|**Lewa alt**+**przesunięcie**+w lewo**PrtScn**|
|Okno dialogowe|Zaznacz lub wyczyść opcję pola wyboru w oknie dialogowym. <br> <br> **UWAGA:** Standardowy skrót klawiaturowy systemu Windows|**Spacja**|
|Menu kontekstowe|Otwórz menu kontekstu (kliknij prawym przyciskiem myszy). <br> <br> **UWAGA:** Standardowy skrót klawiaturowy systemu Windows|**Zmiana**+**F10**|
|Menu|Szybki dostęp do elementu menu za pomocą klawiszy akceleratora. Wybierz klawisz **Alt,** po którym następuje podkreślone litery w menu, aby aktywować polecenie. Na przykład, aby wyświetlić okno dialogowe Otwórz projekt w programie Visual Studio, należy wybrać **alt**+**F**+**O**+**P**.  <br><br> **UWAGA:** Standardowy skrót klawiaturowy systemu Windows|**Alt** + **[litera]**|
|Pole wyszukiwania|Użyj funkcji wyszukiwania w programie Visual Studio.|**Ctrl**+**Q**|
|Okno przybornika|Poruszaj się między kartami Przybornika.|**Ctrl**+**Strzałka w górę**<br /><br /> i<br /><br /> **Strzałka ctrl**+**w dół**|
|Okno przybornika|Dodaj formant z przybornika do formularza lub projektanta.|**Wprowadź**|
|Okno dialogowe Opcje: Środowisko > klawiatura|Usuń kombinację klawiszy wprowadzona w opcji **Naciśnij klawisze skrótów.**|**Backspace**|
|Okno narzędzia Powiadomienia|Otwórz okno narzędzia Powiadomienia, używając dwóch kombinacji klawiszy skrótu klawiaturowego, a następnie drugiej. Następnie wyświetl powiadomienie za pomocą klawiszy strzałek, aby je zaznaczyć.| **Ctrl** + **&#92;**, **Ctrl**+**N**|

> [!NOTE]
> Okna dialogowe i polecenia menu mogą różnić się od tych opisanych w Pomocy, w zależności od aktywnych ustawień lub wersji.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Uzyskiwanie dostępu do powiadomień przy użyciu skrótów klawiaturowych

Gdy w ide pojawi się powiadomienie, oto jak uzyskać dostęp do okna Powiadomienia za pomocą skrótów klawiaturowych:

1. Z dowolnego miejsca w IDE naciśnij kolejno dwa skróty klawiaturowe, jeden po drugim: **Ctrl** + **&#92;** a następnie **Ctrl**+**N**.

   Zostanie otwarte okno **Powiadomienia.**

   ![Okno narzędzia Powiadomienia w programie Visual Studio IDE](media/toast-notification.png "Zrzut ekranu przedstawiający okno Powiadomienia w programie Visual Studio IDE")

1. Użyj **klawisza Tab** lub klawiszy strzałek, aby wybrać powiadomienie.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Ustawianie sygnałów kompilacji i punktów przerwania za pomocą apletu Dźwięk

Apletu Dźwięk w systemie Windows można przypisać dźwięk do zdarzeń programu Visual Studio. W szczególności można przypisać dźwięki do następujących zdarzeń programu:

* Trafienie punktu przerwania
* Kompilacja anulowana
* Kompilacja nie powiodła się
* Kompilacja powiodła się

Oto kroki tej procedury:

1. W polu **Wyszukiwanie** na komputerze z systemem Windows 10 wpisz **Zmień dźwięki systemu**.

   ![Pole wyszukiwania w systemie Windows 10](media/type-here-to-search.png "Zrzut ekranu przedstawiający pole wyszukiwania w systemie Windows 10")

   (Alternatywnie, jeśli masz włączoną Cortanę, powiedz "Hey Cortana", a następnie powiedz "Zmień dźwięki systemu".)

1. Kliknij dwukrotnie pozycję **Zmień dźwięki systemu**.

   ![Wyniki wyszukiwania w systemie Windows 10](media/change-system-sounds.png "Zrzut ekranu przedstawiający wyniki wyszukiwania "Zmień dźwięki systemu" w systemie Windows 10")

1. W oknie dialogowym **Dźwięk** kliknij kartę **Dźwięki.**

1. W **obszarze Zdarzenia programu**przewiń do programu Microsoft Visual **Studio**, a następnie wybierz dźwięki, które chcesz zastosować do wybranych zdarzeń.

   ![Karta Dźwięki apletu Dźwięk w systemie Windows 10](media/sound-applet.png "Karta Dźwięki apletu Dźwięk w systemie Windows 10")

1. Kliknij przycisk **OK**.

::: moniker range="vs-2017"

> [!TIP]
> Aby dowiedzieć się więcej o aktualizacjach ułatwień dostępu, zobacz wpis w blogu [dotyczące ułatwień dostępu w programie Visual Studio 2017 w wersji 15.3.](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/)

::: moniker-end

## <a name="see-also"></a>Zobacz też

* [Funkcje ułatwień dostępu programu Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Jak: Dostosowywanie menu i pasków narzędzi w programie Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Ułatwienia dostępu (Visual Studio dla komputerów Mac)](/visualstudio/mac/accessibility)
* [Ułatwienia dostępu firmy Microsoft](https://www.microsoft.com/Accessibility)
