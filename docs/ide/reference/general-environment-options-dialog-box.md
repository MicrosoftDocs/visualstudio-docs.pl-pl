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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 973e08ca6555f7da7873d3068e2794b8d34e3640
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569442"
---
# <a name="options-dialog-box-environment--general"></a>Okno dialogowe \> Opcje: Środowisko ogólne

Ta strona służy do zmiany motywów kolorów, ustawień paska stanu i skojarzeń rozszerzeń plików, między innymi dla zintegrowanego środowiska programistycznego (IDE). Dostęp do okna dialogowego **Opcje** można uzyskać, otwierając menu **Narzędzia,** wybierając **polecenie Opcje,** otwierając folder **Środowisko,** a następnie wybierając stronę **Ogólne.** Jeśli ta strona nie jest wyświetlana na liście, zaznacz pole wyboru **Pokaż wszystkie ustawienia** w oknie dialogowym **Opcje.**

## <a name="visual-experience"></a>Wrażenia wizualne

**Motyw kolorystyczny**

Wybierz motyw kolorów **Niebieski,** **Jasny,** **Ciemny**lub **Niebieski (Dodatkowy kontrast)** dla IDE.

Dodatkowe wstępnie zdefiniowane motywy można zainstalować i utworzyć motywy niestandardowe, pobierając i instalując **Edytor motywów kolorowych programu Visual Studio** z portalu Visual Studio [Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Po zainstalowaniu tego narzędzia w polu listy Motyw kolorów pojawią się dodatkowe motywy **kolorystykowe.**

**Stosowanie stylów litery na pasku menu**

Menu domyślnie używają stylów litery tytułu. Wyczyść tę opcję, aby użyć wszystkich stylów wielkich liter.

::: moniker range=">=vs-2019"

**Optymalizacja renderowania dla ekranów o różnej gęstości pikseli (wymaga ponownego uruchomienia)**

Ta opcja włącza lub wyłącza świadomość punktów na cal (DPI) (DPI) (lub *PMA).* Gdy pma jest włączona, interfejs użytkownika programu Visual Studio jest wyraźny w dowolnym współczynniku skali wyświetlania monitora i konfiguracji DPI, w tym na wielu monitorach. Aby włączyć pma, potrzebujesz systemu Windows 10 April 2018 Update lub nowszej i .NET Framework 4.8 lub nowszego. (Ta opcja jest wyszarzona, jeśli te dwa wymagania wstępne nie są spełnione).

> [!TIP]
> - Windows 10 ma ustawienie, które mówi **Niech system Windows spróbuje naprawić aplikacje, aby nie były rozmyte**. Włączenie tego **ustawienia** systemu Windows ma nieznaczny wpływ, jeśli zaznaczono opcję **Optymalizuj renderowanie dla ekranów z różnymi gęstościami pikseli.**
> - System Windows 10 zawiera również **narzędzie do rozwiązywania problemów ze zgodnością programów**. Nie zaleca się próby naprawienia wyglądu programu Visual Studio przy użyciu tego narzędzia do rozwiązywania problemów.

::: moniker-end

**Automatyczne dostosowywanie środowiska wizualnego w oparciu o wydajność klienta**

Określa, czy program Visual Studio automatycznie ustawia dopasowanie do środowiska wizualnego, czy też korekta jest jawnie ustawiona. To dostosowanie może zmienić wyświetlanie kolorów z gradientów na płaskie kolory lub może ograniczyć użycie animacji w menu lub oknach podręcznych.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10 ma ustawienie, które mówi **Niech system Windows spróbuje naprawić aplikacje, aby nie były rozmyte**. Włączenie tego **ustawienia** jest zalecane, jeśli program Visual Studio jest rozmyty na monitorze. Należy rozważyć uaktualnienie do [programu Visual Studio 2019](https://visualstudio.microsoft.com/downloads), który znacznie poprawił przejrzystość wyświetlania, ponieważ jest to aplikacja obsługujących na monitor.

::: moniker-end

**Włącz bogate środowisko klienta**

Umożliwia pełne środowisko wizualne programu Visual Studio, w tym gradienty i animacje. Wyczyść tę opcję podczas korzystania z połączeń pulpitu zdalnego lub starszych kart graficznych, ponieważ te funkcje mogą mieć niską wydajność w tych przypadkach. Ta opcja jest dostępna tylko wtedy, gdy **wyczyszczenie opcji Automatycznie dostosuj środowisko wizualne na podstawie** opcji klienta.

**Użyj sprzętowej akceleracji grafiki, jeśli jest dostępna**

Używa sprzętowej akceleracji grafiki, jeśli jest ona dostępna, a nie przyspieszenia oprogramowania.

## <a name="other"></a>Inne

**Elementy do wyświetlenia w menu Okno**

Dostosowuje liczbę okien wyświetlanych na liście systemu Windows w menu **Okno.** Wprowadź liczbę z 1 do 24. Wartość domyślna to 10.

**Elementy wyświetlane na ostatnio używanych listach**

Dostosowuje liczbę ostatnio używanych projektów i plików wyświetlanych w menu **Plik.** Wprowadź liczbę z 1 do 24. Wartość domyślna to 10. Jest to łatwy sposób na pobranie ostatnio używanych projektów i plików.

**Pokaż pasek stanu**

Wyświetla pasek stanu. Pasek stanu znajduje się w dolnej części okna IDE i wyświetla informacje o postępie trwających operacji.

**Przycisk Zamknij wpływa tylko na aktywne okno narzędzia**

Określa, że po kliknięciu przycisku **Zamknij** zamknięte jest tylko okno narzędzia, które ma fokus, a nie wszystkie okna narzędzia w zestawie zadokowanym. Ta opcja jest wybrana domyślnie.

**Przycisk Automatyczne ukrywanie wpływa tylko na aktywne okno narzędzia**

Określa, że po kliknięciu przycisku **Automatyczne ukrywanie** tylko okno narzędzia, które ma fokus, jest automatycznie ukryte, a nie wszystkie okna narzędzia w zadokowanym zestawie. Domyślnie ta opcja nie jest zaznaczona.

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)
