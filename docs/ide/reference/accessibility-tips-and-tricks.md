---
title: Porady i wskazówki dotyczące ułatwień dostępu dla programu Visual Studio
description: Dowiedz się więcej o porady i wskazówki, które mogą ułatwić dostęp do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio wszystkim użytkownikom niepełnosprawnym.
ms.date: 08/06/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59206c206f04aaf3506771ee2310daebd0af273a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939750"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Porady i wskazówki dotyczące ułatwień dostępu dla programu Visual Studio

Program Visual Studio ma wbudowane funkcje ułatwień dostępu, które są zgodne z czytnikami ekranu i innymi technologiami pomocniczymi. Bez względu na to, czy chcesz używać skrótów klawiaturowych do nawigowania w środowisku IDE, czy też korzystać z motywów o dużym kontraście, aby poprawić widoczność, znajdziesz kilka porad, & wskazówki na tej stronie, na której należy to zrobić.

Omówiono również sposób używania adnotacji w celu ujawniania przydatnych informacji o kodzie oraz sposobu ustawiania wskaźników dźwiękowych dla zdarzeń kompilowania i punktów przerwania.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [ułatwienia dostępu dla Visual Studio dla komputerów Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Zapisz ustawienia środowiska IDE

Środowisko IDE można dostosować przez zapisanie układu okna, schematu mapowania klawiatury i innych preferencji. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Modyfikowanie środowiska IDE na potrzeby wyświetlania z wysokim kontrastem

W przypadku niektórych osób niektóre kolory są trudniejsze do wyświetlenia. Jeśli chcesz zwiększyć kontrast podczas pisania kodu, ale nie chcesz używać typowych motywów "duży kontrast", oferujemy teraz motyw "niebieski (dodatkowy kontrast").

  ![Porównanie niebieskiego motywu i niebieskiego motywu o dużym kontraście](media/blue-extra-contrast-theme.png "Zrzut ekranu pokazujący porównanie niebieskiego motywu i niebieskiego motywu o dodatkowych kontrastach")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Używanie adnotacji do ujawniania przydatnych informacji o kodzie

Edytor programu Visual Studio zawiera wiele tekstowych "punktów końcowych", które informują o cechach i funkcjach w określonych punktach w wierszu kodu, takich jak ikony śrubokrętu i żarówki, błędy i ostrzeżenia "zygzaki", zakładki itd. Możesz użyć zestawu poleceń "Pokaż adnotacje z linią", aby ułatwić odnajdywanie i Nawigowanie między tymi modułami.

  ![Użyj polecenia Pokaż adnotacje z linią](media/show-line-annotations-command-set.png "Zrzut ekranu przedstawiający element menu Pokaż adnotacje z linią")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Dostęp do pasków narzędzi za pomocą skrótów klawiaturowych

Środowisko IDE programu Visual Studio zawiera paski narzędzi jako wiele okien narzędzi. Poniższe skróty klawiaturowe ułatwiają dostęp do nich.

|Cecha|Opis|Skrót klawiaturowy|
|-------------|-----------------| - |
|Paski narzędzi IDE|Wybierz pierwszy przycisk na pasku narzędzi Standardowy.|**Alt**, **Ctrl** + **Tab**|
|Paski narzędzi okna narzędzi|Przenieś fokus do pasków narzędzi w oknie narzędzi. <br> <br> **Uwaga:** Działa to w przypadku większości okien narzędzi, ale tylko wtedy, gdy fokus jest w oknie narzędzi. Ponadto musisz wybrać klawisz SHIFT przed klawiszem ALT. W niektórych oknach narzędzi, takich jak Team Explorer, należy nacisnąć klawisz SHIFT na chwilę przed wybraniem klawisza ALT.|**SHIFT** + **Alt**|
|Paski narzędzi|Przejdź do pierwszego elementu na następnym pasku narzędzi (gdy pasek narzędzi ma fokus).|**Ctrl** + **Karta**|

### <a name="other-useful-keyboard-shortcuts"></a>Inne przydatne skróty klawiaturowe

Dostępne są następujące użyteczne skróty klawiaturowe.

|Cecha|Opis|Skrót klawiaturowy|
|-------------|-----------------| - |
|IDE|Duży kontrast włączać i wyłączać. <br> <br> **Uwaga:** Standardowy skrót klawiaturowy systemu Windows|**Lewy Alt** + **Przesuń** + w lewo **PrtScn**|
|Okno dialogowe|Zaznacz lub wyczyść opcję pola wyboru w oknie dialogowym. <br> <br> **Uwaga:** Standardowy skrót klawiaturowy systemu Windows|**Spacja**|
|Menu kontekstowe|Otwórz menu kontekstowe (kliknij prawym przyciskiem myszy). <br> <br> **Uwaga:** Standardowy skrót klawiaturowy systemu Windows|**SHIFT** + **F10**|
|Menu|Szybko uzyskuj dostęp do elementu menu za pomocą jego klawiszy skrótów. Wybierz klawisz **Alt** , a po nim podkreślone litery w menu, aby aktywować polecenie. Na przykład aby wyświetlić okno dialogowe Otwieranie projektu w programie Visual Studio, należy wybrać **Alt** + **F** + **O** + **P**.  <br><br> **Uwaga:** Standardowy skrót klawiaturowy systemu Windows|**Alt**  +  **[litera]**|
|Pole wyszukiwania|Użyj funkcji wyszukiwania w programie Visual Studio.|**Ctrl** + **P**|
|Okno przybornika|Przechodzenie między kartami przybornika.|**Ctrl** + **Strzałka w górę**<br /><br /> oraz<br /><br /> **Ctrl** + **Strzałka w dół**|
|Okno przybornika|Dodaj kontrolkę z przybornika do formularza lub projektanta.|**Enter**|
|Opcje — okno dialogowe: środowisko > klawiatura|Usuń kombinację klawiszy wprowadzoną w opcji **naciśnij klawisze skrótów** .|**Backspace**|
|Okno narzędzia powiadomień|Otwórz okno narzędzia powiadomienia przy użyciu dwóch kombinacji klawiszy skrótów klawiaturowych, po których jeden następuje. Następnie należy wyświetlić powiadomienie przy użyciu klawiszy strzałek, aby je wybrać.| **Ctrl** + **&#92;**, **Ctrl** + **N**|

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wydania.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Powiadomienia dostępu za pomocą skrótów klawiaturowych

Gdy w środowisku IDE pojawi się powiadomienie, można uzyskać dostęp do okna powiadomienia za pomocą skrótów klawiaturowych:

1. Z dowolnego miejsca w środowisku IDE naciśnij dwa skróty klawiaturowe w sekwencji, jeden po drugim: **Ctrl** + **&#92;** a następnie **Ctrl** + **N**.

   Zostanie otwarte okno **powiadomienia** .

   ![Okno narzędzia powiadomień w środowisku IDE programu Visual Studio](media/toast-notification.png "Zrzut ekranu okna powiadomień w środowisku IDE programu Visual Studio")

1. Użyj klawisza **Tab** lub klawiszy strzałek, aby wybrać powiadomienie.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Użyj apletu dźwięk, aby ustawić podpowiedzi kompilacji i punktów przerwania

Aby przypisać dźwięk do zdarzeń programu Visual Studio, można użyć apletu dźwięk w systemie Windows. W tym celu można przypisać dźwięki do następujących zdarzeń programu:

* Trafienie punktu przerwania
* Kompilacja anulowana
* Kompilacja nie powiodła się
* Kompilacja powiodła się

Oto kroki tej procedury:

1. W polu **wyszukiwania** na komputerze z systemem Windows 10 wpisz polecenie **Zmień dźwięki systemowe**.

   ![Pole wyszukiwania w systemie Windows 10](media/type-here-to-search.png "Zrzut ekranu pola wyszukiwania w systemie Windows 10")

   (W przypadku włączenia Cortany należy powiedzieć "Hey Cortana", a następnie powiedzieć "zmiana dźwięków systemu").

1. Kliknij dwukrotnie pozycję **Zmień dźwięki systemowe**.

   ![Wyniki wyszukiwania w systemie Windows 10](media/change-system-sounds.png "Zrzut ekranu przedstawiający wyniki wyszukiwania "Zmień dźwięki systemu" w systemie Windows 10")

1. W oknie dialogowym **dźwięk** kliknij kartę **dźwięki** .

1. W obszarze **zdarzenia programu** przewiń do **Microsoft Visual Studio**, a następnie wybierz dźwięki, które chcesz zastosować do wybranych zdarzeń.

   ![Karta dźwięki apletu dźwięk w systemie Windows 10](media/sound-applet.png "Karta dźwięki apletu dźwięk w systemie Windows 10")

1. Kliknij przycisk **OK**.

::: moniker range="vs-2017"

> [!TIP]
> Aby dowiedzieć się więcej na temat aktualizacji ułatwień dostępu, zobacz wpis w blogu dotyczący [ulepszeń ułatwień dostępu w programie Visual Studio 2017 version 15,3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) .

::: moniker-end

## <a name="see-also"></a>Zobacz też

* [Funkcje ułatwień dostępu programu Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Instrukcje: Dostosowywanie menu i pasków narzędzi w programie Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Ułatwienia dostępu (Visual Studio dla komputerów Mac)](/visualstudio/mac/accessibility)
* [Ułatwienia dostępu firmy Microsoft](https://www.microsoft.com/Accessibility)
