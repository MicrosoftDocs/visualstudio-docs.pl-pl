---
title: Porady i wskazówki dotyczące ułatwień dostępu dla programu Visual Studio
description: Dowiedz się więcej o porady i wskazówki, które mogą ułatwić dostęp do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio wszystkim użytkownikom niepełnosprawnym.
ms.date: 08/02/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a3a70f061ea4fd6dd51a3badbed922675b99fba
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2019
ms.locfileid: "68740249"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Porady i wskazówki dotyczące ułatwień dostępu dla programu Visual Studio

> [!TIP]
> Aby dowiedzieć się więcej na temat aktualizacji ułatwień dostępu, zobacz wpis w blogu dotyczący [ulepszeń ułatwień dostępu w programie Visual Studio 2017 version 15,3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) .

Program Visual Studio ma wbudowane funkcje ułatwień dostępu, które są zgodne z czytnikami ekranu i innymi technologiami pomocniczymi. W tym temacie wymieniono typowe kombinacje klawiszy skrótów, których można użyć do wykonywania zadań tylko za pomocą klawiatury, a także informacje na temat korzystania z motywów o dużym kontraście w celu poprawienia widoczności. Pokazuje również, jak za pomocą adnotacji ujawniać użyteczne informacje o kodzie oraz jak ustawiać podpowiedzi dźwiękowe dla zdarzeń kompilacji i punktów przerwania.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [ułatwienia dostępu dla Visual Studio dla komputerów Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Zapisz ustawienia środowiska IDE

 Środowisko IDE można dostosować przez zapisanie układu okna, schematu mapowania klawiatury i innych preferencji. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Modyfikowanie środowiska IDE na potrzeby wyświetlania z wysokim kontrastem

W przypadku niektórych osób niektóre kolory są trudniejsze do wyświetlenia. Jeśli chcesz zwiększyć kontrast podczas pisania kodu, ale nie chcesz używać typowych motywów "duży kontrast", oferujemy teraz motyw "niebieski (dodatkowy kontrast").

  ![Porównanie niebieskiego motywu i niebieskiego motywu o dużym kontraście](media/blue-extra-contrast-theme.png)

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Używanie adnotacji do ujawniania przydatnych informacji o kodzie

Edytor programu Visual Studio zawiera wiele tekstowych "punktów końcowych", które informują o cechach i funkcjach w określonych punktach w wierszu kodu, takich jak ikony śrubokrętu i żarówki, błędy i ostrzeżenia "zygzaki", zakładki itd. Możesz użyć zestawu poleceń "Pokaż adnotacje z linią", aby ułatwić odnajdywanie i Nawigowanie między tymi modułami.

  ![Użyj polecenia Pokaż adnotacje z linią](media/show-line-annotations-command-set.png)

## <a name="access-toolbars-by-using-shortcut-key-combinations"></a>Dostęp do pasków narzędzi przy użyciu kombinacji klawiszy skrótów

Środowisko IDE programu Visual Studio zawiera paski narzędzi jako wiele okien narzędzi. Poniższe kombinacje klawiszy skrótów ułatwiają uzyskiwanie dostępu do nich.

|Funkcja|Opis|Kombinacja klawiszy|
|-------------|-----------------| - |
|Paski narzędzi IDE|Wybierz pierwszy przycisk na pasku narzędzi Standardowy.|**Alt**, **Ctrl** + **Tab**|
|Paski narzędzi okna narzędzi|Przenieś fokus do pasków narzędzi w oknie narzędzi. <br> <br> **UWAGA:** Działa to w przypadku większości okien narzędzi, ale tylko wtedy, gdy fokus jest w oknie narzędzi. Ponadto musisz wybrać klawisz SHIFT przed klawiszem ALT. W niektórych oknach narzędzi, takich jak Team Explorer, należy nacisnąć klawisz SHIFT na chwilę przed wybraniem klawisza ALT.|**Shift**Alt + |
|Paski narzędzi|Przejdź do pierwszego elementu na następnym pasku narzędzi (gdy pasek narzędzi ma fokus).| + **Karta** Ctrl|

### <a name="other-useful-shortcut-key-combinations"></a>Inne przydatne kombinacje klawiszy skrótów

Niektóre inne przydatne kombinacje klawiszy skrótów obejmują następujące elementy.

|Funkcja|Opis|Kombinacja klawiszy|
|-------------|-----------------| - |
|IDE|Duży kontrast włączać i wyłączać. <br> <br> **UWAGA:** Standardowy skrót systemu Windows|**Lewy Alt + Strzałka w lewo + PrtScn**|
|Okno dialogowe|Zaznacz lub wyczyść opcję pola wyboru w oknie dialogowym. <br> <br> **UWAGA:** Standardowy skrót systemu Windows|**Spacja**|
|Menu kontekstowe|Otwórz menu kontekstowe (kliknij prawym przyciskiem myszy). <br> <br> **UWAGA:** Standardowy skrót systemu Windows|**Shift**F10 + |
|Menu|Szybko uzyskuj dostęp do elementu menu za pomocą jego klawiszy skrótów. Wybierz klawisz **Alt** , a po nim podkreślone litery w menu, aby aktywować polecenie. Na przykład aby wyświetlić okno dialogowe Otwieranie projektu w programie Visual Studio, należy wybrać **Alt** + **F** + **O** + **P**.  <br><br> **UWAGA:** Standardowy skrót systemu Windows|Alt +  **[litera]**|
|Pole wyszukiwania|Użyj funkcji wyszukiwania w programie Visual Studio.|**CTRL** + **funkcji pytania i odpowiedzi**|
|Okno przybornika|Przechodzenie między kartami przybornika.|**Ctrl +**  + **Strzałka w górę**<br /><br /> and<br /><br /> Ctrl + **Strzałka w dół**|
|Okno przybornika|Dodaj kontrolkę z przybornika do formularza lub projektanta.|**Wprowadź**|
|Opcje — okno dialogowe: Klawiatura > środowiska|Usuń kombinację klawiszy wprowadzoną w opcji **naciśnij klawisze skrótów** .|**BACKSPACE**|
|Okno narzędzia powiadomień|Otwórz okno narzędzia powiadomienia przy użyciu dwóch kombinacji klawiszy skrótów klawiaturowych, po których jeden następuje. Następnie należy wyświetlić powiadomienie przy użyciu klawiszy strzałek, aby je wybrać.| **Przytrzymaj** +  **&#92;** <br>**Ctrl**N + |

> [!NOTE]
> Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wersji.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Użyj apletu dźwięk, aby ustawić podpowiedzi kompilacji i punktów przerwania

Aby przypisać dźwięk do zdarzeń programu Visual Studio, można użyć apletu dźwięk w systemie Windows. W tym celu można przypisać dźwięki do następujących zdarzeń programu:

* Trafienie punktu przerwania
* Kompilacja anulowana
* Kompilacja nie powiodła się
* Kompilacja powiodła się

Oto jak to zrobić:

1. W polu **wyszukiwania** na komputerze z systemem Windows 10 wpisz polecenie **Zmień dźwięki systemowe**.

   ![Pole wyszukiwania w systemie Windows 10](media/type-here-to-search.png)

   (W przypadku włączenia Cortany należy powiedzieć "Hey Cortana", a następnie powiedzieć "zmiana dźwięków systemu").

2. Kliknij dwukrotnie pozycję **Zmień dźwięki systemowe**.

   ![Wyniki wyszukiwania w systemie Windows 10](media/change-system-sounds.png)

3. W oknie dialogowym **dźwięk** kliknij kartę **dźwięki** . <br><br>
   Następnie w obszarze **zdarzenia programu**przewiń do **Microsoft Visual Studio**i wybierz dźwięki, które chcesz zastosować do wybranych zdarzeń.

   ![Karta dźwięki apletu dźwięk w systemie Windows 10](media/sound-applet.png)

4. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

* [Funkcje ułatwień dostępu programu Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Instrukcje: Dostosowywanie menu i pasków narzędzi w programie Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Ułatwienia dostępu firmy Microsoft](https://www.microsoft.com/Accessibility)
* [Ułatwienia dostępu (Visual Studio dla komputerów Mac)](/visualstudio/mac/accessibility)