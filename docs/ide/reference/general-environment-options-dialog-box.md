---
title: Ogólne, środowisko, opcje — Okno dialogowe
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.Environment.General
- VS.Message.0x800a002e
- VS.OptionsDialog.Environment
- VS.ToolsOptionsPages.Environment
- VS.ToolsOptionsPages.Environment.General
helpviewer_keywords:
- recently used file lists
- Windows menu, customizing
- status bar, displaying
- Options dialog box, General Environment
- General Environment Options dialog box
- Environment Options dialog box
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb1dbbcc4adf8305aad119ac8a4cb223e0f89902
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180284"
---
# <a name="options-dialog-box-environment--general"></a>Opcje — okno dialogowe: Środowisko \> ogólne

Ta strona służy do zmiany motywów kolorów, ustawień paska stanu i skojarzeń rozszerzeń plików między innymi opcjami dla zintegrowanego środowiska programistycznego (IDE). Dostęp do okna dialogowego **Opcje** można uzyskać, otwierając menu **Narzędzia** , wybierając **Opcje**, otwierając folder **środowiska** , a następnie wybierając stronę **Ogólne** . Jeśli ta strona nie jest wyświetlana na liście, zaznacz pole wyboru **Pokaż wszystkie ustawienia** w oknie dialogowym **Opcje** .

## <a name="visual-experience"></a>Środowisko wizualne

**Motyw kolorów**

Wybierz motyw koloru **niebieski**, **jasny**, **ciemny**lub **niebieski (dodatkowy kontrast)** dla środowiska IDE.

Możesz zainstalować dodatkowe wstępnie zdefiniowane motywy i utworzyć niestandardowe motywy, pobierając i instalując **Edytor motywów kolorów programu Visual Studio** z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Po zainstalowaniu tego narzędzia w polu listy **motywu kolorów** zostaną wyświetlone dodatkowe motywy koloru.

**Zastosuj styl wielkości liter dla tytułu do paska menu**

Menu domyślnie używają stylu wielkości liter. Usuń zaznaczenie tej opcji, aby zamiast tego użyć wszystkich wielkich stylów.

::: moniker range=">=vs-2019"

**Optymalizacja renderowania dla ekranów o różnych gęstościach pikseli (wymaga ponownego uruchomienia)**

Ta opcja włącza lub wyłącza funkcję rozpoznawania punktów na cal (DPI) (lub *PMA*). Gdy PMA jest włączona, interfejs użytkownika programu Visual Studio jest bardziej wyrazisty w dowolnym monitorze monitora wyświetlania ekranu i konfiguracji DPI, w tym na wielu monitorach. Aby włączyć PMA, wymagana jest aktualizacja systemu Windows 10 z kwietnia 2018 lub nowsza i .NET Framework 4,8 lub nowsza. (Ta opcja jest wyświetlana w kolorze szarym, jeśli te dwa wymagania wstępne nie są spełnione).

> [!TIP]
> - System Windows 10 ma ustawienie informujące o tym, że **system Windows próbuje naprawić aplikacje, tak aby nie były zamazane**. Włączenie tego ustawienia systemu Windows ma niewielki efekt, jeśli jest zaznaczone pole wyboru **Optymalizuj Render dla ekranów z inną gęstością pikseli** .
> - System Windows 10 zawiera również **Narzędzie do rozwiązywania problemów ze zgodnością programu**. Nie zalecamy próby naprawienia wyglądu programu Visual Studio za pomocą tego narzędzia do rozwiązywania problemów.

::: moniker-end

**Automatycznie Dostosuj środowisko wizualne na podstawie wydajności klienta**

Określa, czy program Visual Studio ustawia automatyczne dopasowanie do wizualizacji, czy też ustawia się w sposób jawny. Ta korekta może zmienić sposób wyświetlania kolorów z gradientów na płaskie kolory lub ograniczyć użycie animacji w menu lub oknach podręcznych.

::: moniker range="vs-2017"

> [!TIP]
> System Windows 10 ma ustawienie informujące o tym, że **system Windows próbuje naprawić aplikacje, tak aby nie były zamazane**. Włączenie tego ustawienia jest zalecane, jeśli program Visual Studio wydaje się zamazany na monitorze. Rozważ uaktualnienie do [programu Visual Studio 2019](https://visualstudio.microsoft.com/downloads), która znacznie poprawiła czytelność ekranu, ponieważ jest to liczba punktów monitora na aplikację obsługującą cal.

::: moniker-end

**Włącz rozbudowane środowisko klienta**

Umożliwia pełne środowisko wizualne programu Visual Studio, w tym gradienty i animacje. Wyczyść tę opcję w przypadku używania połączeń Pulpit zdalny lub starszych kart graficznych, ponieważ te funkcje mogą mieć w takich przypadkach niską wydajność. Ta opcja jest dostępna tylko w przypadku usunięcia zaznaczenia opcji **automatycznie Dostosuj środowisko wizualne na podstawie klienta** .

**Użyj sprzętowego przyspieszania grafiki, jeśli jest dostępne**

Używa sprzętowego przyspieszania grafiki, jeśli jest dostępne, a nie przyspieszenia oprogramowania.

## <a name="other"></a>Inne

**Elementy do wyświetlenia w menu okna**

Dostosowuje liczbę okien, które są wyświetlane na liście systemu Windows w menu **okno** . Wprowadź liczbę z zakresu od 1 do 24. Wartość domyślna to 10.

**Elementy wyświetlane na listach ostatnio używanych**

Dostosowuje liczbę ostatnio używanych projektów i plików, które są wyświetlane w menu **plik** . Wprowadź liczbę z zakresu od 1 do 24. Wartość domyślna to 10. Jest to prosty sposób na pobranie niedawno używanych projektów i plików.

**Pokaż pasek stanu**

Wyświetla pasek stanu. Pasek stanu znajduje się u dołu okna IDE i wyświetla informacje o postępie trwających operacji.

**Przycisk zamykania ma wpływ tylko na aktywne okno narzędzi**

Określa, że po kliknięciu przycisku **Zamknij** tylko okno narzędzia z fokusem jest zamknięte, a nie wszystkie okna narzędzi w zestawie zadokowanym. Domyślnie ta opcja jest zaznaczona.

**Przycisk Autoukrywanie ma wpływ tylko na aktywne okno narzędzi**

Określa, że po kliknięciu przycisku Autoukrywanie tylko okno narzędzia z fokusem jest ukryte automatycznie i nie wszystkie okna narzędzi w zestawie zadokowanym. Domyślnie ta opcja nie jest zaznaczona.

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)