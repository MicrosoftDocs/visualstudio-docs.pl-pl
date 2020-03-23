---
title: Szybkie uruchamianie, środowisko, opcje — okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 706b54e3ee925b1833f860da2f84c8d28af9617e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565672"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Szybkie uruchamianie, środowisko, opcje — okno dialogowe

Za pomocą **funkcji Szybkie uruchamianie** można szybko wyszukiwać i wykonywać akcje dotyczące zasobów IDE, takich jak opcje, szablony, menu. Za pomocą **funkcji Szybkie uruchamianie** nie można wyszukiwać kodu i symboli. Pole wyszukiwania **Szybkie uruchamianie** znajduje się w prawym górnym rogu paska menu i jest dostępne po naciśnięciu **klawisza Ctrl**+**Q**. Wpisz ciąg wyszukiwania w polu. Aby wyszukać ciągi zawierające @, użyj '@@'.

**Szybkie uruchamianie** jest domyślnie włączone podczas instalowania programu Visual Studio. Na pasku menu można wyświetlić lub ukryć **szybkie uruchamianie,** wybierając pozycję**Opcje** **narzędzi** > . Rozwiń węzeł **Środowiska,** a następnie wybierz pozycję **Szybkie uruchamianie**. Zaznacz lub wyczyść pole wyboru **Włącz szybkie uruchamianie.** Można również włączyć lub wyłączyć kategorie wyszukiwania na tej stronie.

## <a name="category-list"></a>Lista kategorii

Wyniki wyszukiwania szybkiego uruchamiania są wyświetlane w czterech kategoriach: **Ostatnio używane**, **Menu**, **Opcje**i **Otwórz dokumenty**, wraz z liczbą elementów w kategorii. Aby przeglądać wyniki wyszukiwania według kategorii, wybierz klawisze **Ctrl**+**Q,** aby wyświetlić wszystkie wyniki z następnej kategorii. Po wyświetleniu ostatniej kategorii **ctrl**+**Q** pokazuje kilka wyników z każdej kategorii. Naciśnij **klawisze Ctrl**+**Shift**+**Q,** aby poruszać się po kategoriach w odwrotnej kolejności. Aby wyświetlić wszystkie wyniki wyszukiwania w kategorii, wybierz nazwę kategorii.

Możesz użyć następujących skrótów, aby ograniczyć wyszukiwanie do określonych kategorii.

|Kategoria|Skrót|Opis skrótu|
|--------------|--------------| - |
|Ostatnio używane|@mru<br /><br /> Na przykład: `@mru font`|Wyświetla maksymalnie pięć ostatnio **używanych**elementów .|
|Menu|@menu<br /><br /> Na przykład: `@menu project`|Ogranicza wyszukiwanie do elementów menu.|
|Opcje|@opt<br /><br /> Na przykład: `@opt font`|Ogranicza wyszukiwanie do ustawień w oknie dialogowym **Opcje.**|
|Dokumenty|@doc<br /><br /> Na przykład: `@doc program.cs`|Ogranicza wyszukiwanie do nazw plików i ścieżek otwartych dokumentów dla kryteriów wyszukiwania, ale nie przeszukuje tekstu wewnątrz samych plików.|

> [!NOTE]
> Klawisze skrótów można zmienić na stronie**Klawiatura** **ogólna** > w oknie dialogowym **Opcje.**

## <a name="show-previous-results"></a>Pokaż poprzednie wyniki

Domyślnie wyszukiwany termin, który należy wprowadzić, nie jest zachowywany między sesjami wyszukiwania. Ciąg wyszukiwania jest czyszczony, jeśli szukasz terminu, przesuniesz kursor poza obszar **Szybkie uruchamianie,** a następnie cofniesz. Aby zachować wyniki wyszukiwania, przejdź do okna dialogowego **Opcje,** wybierz pozycję **Szybkie uruchamianie**, a następnie wybierz **pozycję Pokaż wyniki wyszukiwania z poprzedniego wyszukiwania po aktywowaniu funkcji Szybkie uruchamianie.** . Przy następnym wyszukiwaniu, opuszczeniu obszaru Szybkie uruchamianie i powrocie szybkie uruchamianie zachowa ostatnio użyte hasło wyszukiwania, a także wyświetli wyniki wyszukiwania.
