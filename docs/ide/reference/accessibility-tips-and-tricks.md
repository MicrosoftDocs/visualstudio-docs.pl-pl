---
title: Wskazówki dotyczące dostępności i wskazówki dotyczące programu Visual Studio
description: Więcej informacji na temat porady i wskazówki, które mogą pomóc, że program Visual Studio zintegrowane środowisko programistyczne (IDE) jest bardziej dostępny dla każdego, w tym osobom niepełnosprawnym.
ms.date: 09/15/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 473f46e87ded78e134ab021b68c57248f8ac1a33
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349208"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Wskazówki dotyczące dostępności i wskazówki dotyczące programu Visual Studio

> [!TIP]
> Aby dowiedzieć się więcej o najnowszych aktualizacjach ułatwień dostępu, zobacz [ulepszenia ułatwień dostępu w programie Visual Studio 2017 w wersji 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) wpis w blogu.

Visual Studio ma wbudowanych funkcji ułatwień dostępu, które są zgodne z czytnikami ekranu i innych technologii pomocniczych. Ten temat zawiera listę typowych kombinacje klawiszy skrótu można używać do wykonywania zadań przy użyciu tylko klawiatury i zawiera informacje o używaniu motywy o wysokim kontraście poprawi widoczność. Także pokazuje jak ujawnić przydatnych informacji o kodzie za pomocą adnotacji i jak ustawić dźwięku wskazówek dla kompilacji i punkt przerwania zdarzenia.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [ułatwień dostępu dla programu Visual Studio dla komputerów Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Zapisz ustawienia IDE

 Aby dostosować swoje środowisko IDE, należy zapisywanie układu okna, schemat mapowania klawiatury i inne preferencje. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Zmodyfikuj swoje środowisko IDE przeznaczone do wyświetlania o wysokim kontraście

Dla niektórych osób niektóre kolory są trudne do wyświetlić. Jeśli chcesz więcej kontrastu w trakcie kodowania, ale nie mają być używane Typowe motywy "O wysokim kontraście", oferujemy teraz motywu "Niebieski (dodatkowy kontrast)".

  ![Porównaj motyw niebieski i motyw niebieski dodatkowy kontrast](media/blue-extra-contrast-theme.png)

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Aby wyświetlić przydatnych informacji o kodzie korzystanie z adnotacji

Edytor programu Visual Studio zawiera wiele tekst "zakończeń", które pozwalają poznać cechy i funkcje w punktach konkretnego wiersza kodu, takie jak lightbulbs, błąd i ostrzeżenie "zygzaki" zakładek i tak dalej. Można użyć zestaw ułatwiają odnajdywanie i następnie przechodzić między zakończeniami tych poleceń "Pokaż adnotacje z linią".

  ![Użyj zestawu poleceń Pokaż adnotacje z linią](media/show-line-annotations-command-set.png)

## <a name="access-toolbars-by-using-shortcut-key-combinations"></a>Dostęp do pasków narzędzi, za pomocą kombinacji klawiszy skrótów

Visual Studio IDE ma paski narzędzi, jak wielu okien narzędziowych. Następujące kombinacje klawiszy skrótu ułatwiają dostęp do nich.

|Funkcja|Opis|Kombinacja klawiszy|
|-------------|-----------------| - |
|Paski narzędzi IDE|Wybierz pierwszy przycisk na pasku narzędzi Standardowy.|**ALT**, **CTRL** + **KARTĘ**|
|Paskach narzędzi okna|Przenieś fokus na paski narzędzi w oknie narzędzi. <br> <br> **Uwaga:** działa to dla większości okien narzędzi, ale tylko wtedy, gdy fokus znajduje się w oknie narzędzi. Ponadto musisz wybrać klawisz SHIFT przed klawisza ALT. W niektórych oknach narzędzi, takich jak Team Explorer musi przytrzymaj klawisz SHIFT, przez chwilę przed wybraniem klawisza ALT.|**SHIFT** + **ALT**|
|Paski narzędzi|Przejdź do pierwszego elementu w pasku dalej (w przypadku pasek narzędzi jest ustawiony fokus).|**CTRL** + **KARTĘ**|

### <a name="other-useful-shortcut-key-combinations"></a>Inne kombinacje klawiszy skrótu przydatne

Oto niektóre inne przydatne kombinacje klawiszy skrótu.

|Funkcja|Opis|Kombinacja klawiszy|
|-------------|-----------------| - |
|IDE|Przełącz wysokiego kontrastu, włączać i wyłączać. <br> <br> **Uwaga:** skrótów Windows Standard|**Lewy ALT + lewy SHIFT + PRINT SCREEN**|
|Okno dialogowe|Zaznacz lub wyczyść pole wyboru opcji w oknie dialogowym. <br> <br> **Uwaga:** skrótów Windows Standard|**SPACJA**|
|Menu kontekstowe|Otwórz menu kontekstowe (kliknij prawym przyciskiem myszy). <br> <br> **Uwaga:** skrótów Windows Standard|**SHIFT** + **F10**|
|Menu|Szybki dostęp do elementu menu przy użyciu jego klawiszy skrótów. Wybierz **ALT** klucz następuje podkreślnikiem w menu, aby uaktywnić to polecenie. Na przykład, aby wyświetlić okno dialogowe Otwórz projekt w programie Visual Studio, możesz wybrać **ALT** + **F** + **O**  +  **P**.  <br><br> **Uwaga:** skrótów Windows Standard|**ALT** + **[list]**|
|Okno przybornika|Przechodzenie między karty przybornika.|**CTRL** + **UPARROW**<br /><br /> and<br /><br /> **CTRL** + **STRZAŁKA W DÓŁ**|
|Okno przybornika|Dodawanie formantu z przybornika do formularza lub projektanta.|**WPROWADŹ**|
|Klawiatura, środowisko, opcje — Okno dialogowe|Usunąć kombinacja klawiszy w **naciśnij klawisze skrótu** opcji.|**BACKSPACE**|

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Użyj apletu dźwięku, aby ustawić podpowiedzi kompilacji i punkt przerwania

Aplet dźwięku w Windows służy do przypisywania dźwięk do zdarzenia programu Visual Studio. W szczególności można przypisać dźwięków do następujących programów:

 * Trafiony punkt przerwania
 * Kompilacja anulowana
 * Kompilacja nie powiodła się
 * Kompilacja powiodła się

Poniżej przedstawiono sposób.

1. W **wyszukiwania** okno na komputerze z systemem Windows 10, typ **Zmień dźwięki systemu**.

   ![Pole wyszukiwania w systemie Windows 10](media/type-here-to-search.png)

   (Również w przypadku Cortana włączone powiedzieć "Hey Cortana", a następnie powiedział do was "Zmień dźwięki systemu".)

2. Kliknij dwukrotnie **Zmień dźwięki systemu**.

   ![Wyniki wyszukiwania w systemie Windows 10](media/change-system-sounds.png)

3. W **dźwięk** okno dialogowe, kliknij przycisk **dźwięki** kartę. <br><br>
   Następnie w **zdarzenia programu**, przewiń do **programu Microsoft Visual Studio**i wybierz dźwięki, które chcesz zastosować do zdarzenia, które wybierzesz.

   ![Dźwięki karty dźwiękowej apletu w systemie Windows 10](media/sound-applet.png)

4. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

* [Funkcje ułatwień dostępu programu Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Porady: Dostosowywanie menu i pasków zadań w programie Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Microsoft poświęconą ułatwieniom dostępu](https://www.microsoft.com/Accessibility)
* [Ułatwienia dostępu (Visual Studio dla komputerów Mac)](/visualstudio/mac/accessibility)