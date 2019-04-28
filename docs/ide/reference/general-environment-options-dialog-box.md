---
title: Ogólne, środowisko, opcje — Okno dialogowe
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f860293669ddab035ddd1c53e09dbb9962df01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790138"
---
# <a name="options-dialog-box-environment--general"></a>Okno dialogowe Opcje: Środowisko \> ogólne

Użyj tej strony, aby zmienić motywy kolorów, ustawienia paska stanu i skojarzenia rozszerzeń plików, między innymi do zintegrowanego środowiska programistycznego (IDE). Możesz uzyskać dostęp **opcje** okno dialogowe, otwierając **narzędzia** menu, wybierając **opcje**, otwierając **środowiska** folder i następnie Wybieranie **ogólne** strony. Jeśli ta strona nie jest wyświetlana na liście, wybierz opcję **Pokaż wszystkie ustawienia** pole wyboru w **opcje** okno dialogowe.

## <a name="visual-experience"></a>Środowisko wizualne

**Motyw kolorów**

Wybierz **niebieski**, **światła**, **ciemny**, lub **niebieski (dodatkowy kontrast)** motyw kolorów IDE.

Można zainstalować dodatkowe predefiniowane motywy i utworzyć motywy dostosowane pobierając i instalując **Edytor motywów kolorystycznych programu Visual Studio** z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Po zainstalowaniu tego narzędzia, motywy kolorów dodatkowe są wyświetlane w **motyw kolorów** pola listy.

**Zastosuj wielkość liter, ustawianie stylów na pasku menu**

Menu Użyj wielkimi literami style domyślnie. Usuń zaznaczenie tej opcji spowoduje użycie wszystkie wielkie litery style zamiast tego.

::: moniker range=">=vs-2019"

**Optymalizowanie renderowania na ekranach o różnych pikseli gęstości (wymaga ponownego uruchomienia)**

Ta opcja włącza lub wyłącza — monitorowanie punktów na cal (DPI) świadomości (lub *PMA*). Po włączeniu PMA interfejsu użytkownika programu Visual Studio pojawia się wyraźny w dowolnych współczynnik skali wyświetlania monitor i konfiguracją DPI, z uwzględnieniem na wiele monitorów. Aby włączyć PMA, musisz mieć systemu Windows 10 kwietnia 2018 r. Zaktualizuj lub nowszej i .NET Framework 4,8 lub nowszej. (Ta opcja pojawia się wyszarzonym Jeśli te dwa wymagania wstępne nie są spełnione.)

> [!TIP]
> - Windows 10 ma ustawienie informujący, że **Windows Pozwól spróbować naprawić aplikacji, aby nie były one rozmyte**. Włączenie tego ustawienia Windows **na** ma niewielki wpływ, jeśli masz **optymalizacji renderowania na ekranach o różnych pikseli gęstości** zaznaczoną opcją.
> - Windows 10 zawiera również **Rozwiązywanie problemów ze zgodnością programu**. Nie zaleca się próby naprawienia wyglądu programu Visual Studio za pomocą tego narzędzia do rozwiązywania problemów.

::: moniker-end

**Automatycznie Dostosuj wygląd bazując na wydajności klienta**

Określa, czy program Visual Studio ustawia dostosowania środowisko wizualne automatycznie, lub jawnie ustaw dostosowania. To dostosowanie może zmienić sposób wyświetlania kolorów z gradientów kolorów prostego lub jego może ograniczyć użycie animacji w menu lub okna podręcznego.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10 ma ustawienie informujący, że **Windows Pozwól spróbować naprawić aplikacji, aby nie były one rozmyte**. Włączenie tego ustawienia **na** jest zalecane, jeśli program Visual Studio pojawia się rozmyte na monitorze. Rozważ uaktualnienie do [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), która znacznie ulepszono przejrzystości wyświetlania ponieważ punktów — monitorowanie, na aplikację świadomą CAL.

::: moniker-end

**Włącz bogate doświadczenia**

Włącza pełne wizualne środowisko programu Visual Studio, w tym w gradientach i animacji. Usuń zaznaczenie tej opcji, podczas korzystania z połączeniami pulpitu zdalnego lub starszych kart graficznych, ponieważ te funkcje mogą mieć niskiej wydajności w tych przypadkach. Ta opcja jest dostępna tylko wtedy, gdy usuniesz zaznaczenie **automatycznie Dostosuj wygląd bazując na kliencie** opcji.

**Użyj sprzętowego przyspieszania grafiki, jeśli jest dostępny**

Używa sprzętowego przyspieszania grafiki, jeśli jest on dostępny, zamiast przyspieszenie oprogramowania.

## <a name="other"></a>Inne

**Elementów do wyświetlenia w menu Okno**

Dostosowuje liczbę przedziałów, które pojawiają się na liście Windows **okna** menu. Wprowadź liczbę między 1 a 24. Wartość domyślna to 10.

**Elementy wyświetlane na listach ostatnio używanych**

Dostosowuje liczbę niedawno używanych projektów i plików, które pojawiają się na **pliku** menu. Wprowadź liczbę między 1 a 24. Wartość domyślna to 10. Jest to prosty sposób pobierania niedawno używanych projektów i plików.

**Pokaż pasek stanu**

Wyświetla na pasku stanu. Na pasku stanu znajduje się w dolnej części okna środowiska IDE i wyświetla informacje o postępie trwające operacje.

**Przycisk Zamknij dotyczy tylko aktywnego okna narzędzi**

Określa, że w przypadku **Zamknij** kliknięty przycisk tylko okna narzędzi, które ma fokus został zamknięty i nie wszystkie okien narzędzi zadokowanych zestawu. Domyślnie ta opcja jest zaznaczona.

**Przycisk Ukryj automatycznie dotyczy tylko aktywnego okna narzędzi**

Określa, że w przypadku **Autoukrywanie** przycisku, okna narzędzi, który ma fokus jest ukryta, automatycznie, a nie wszystkich okien narzędzi zadokowanych zestawu. Domyślnie ta opcja nie jest zaznaczona.

## <a name="see-also"></a>Zobacz także

- [Środowisko, Opcje — okno dialogowe](../../ide/reference/environment-options-dialog-box.md)
- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)