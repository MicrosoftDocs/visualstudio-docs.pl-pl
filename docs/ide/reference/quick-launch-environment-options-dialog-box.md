---
title: Szybkie uruchamianie, środowisko, opcje — okno dialogowe
description: Dowiedz się, jak używać strony szybkiego uruchamiania w sekcji środowisko, aby szybko wyszukiwać i wykonywać akcje dla zasobów IDE, takich jak opcje, szablony i menu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e055906dd4cddabd16b39e3b2cad66d07dddd38d
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616749"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Szybkie uruchamianie, środowisko, opcje — okno dialogowe

Funkcja **szybkiego uruchamiania** umożliwia szybkie wyszukiwanie i wykonywanie akcji dla zasobów IDE, takich jak opcje, szablony i menu. Nie można użyć **szybkiego uruchamiania** do wyszukiwania kodu i symboli. Pole wyszukiwania **szybkiego uruchamiania** znajduje się w prawym górnym rogu paska menu i jest dostępne przez naciśnięcie **klawiszy CTRL** + **Q**. W polu wpisz ciąg wyszukiwania. Aby wyszukać ciągi zawierające ciąg @, użyj znaku "@ @".

**Szybkie uruchamianie** jest domyślnie włączone podczas instalowania programu Visual Studio. Na pasku menu można pokazać lub ukryć pasek **Szybkie uruchamianie** , wybierając pozycję **Narzędzia**  >  **Opcje**. Rozwiń węzeł **środowiska** , a następnie wybierz polecenie **Szybkie uruchamianie**. Zaznacz lub wyczyść pole wyboru **Włącz szybkie uruchamianie** . Możesz również włączyć lub wyłączyć kategorie wyszukiwania na tej stronie.

## <a name="category-list"></a>Lista kategorii

Wyniki wyszukiwania szybkiego uruchamiania są wyświetlane w czterech kategoriach: **ostatnio używane**, **menu**, **Opcje** i **otwarte dokumenty** wraz z liczbą elementów w kategorii. Aby przechodzić przez wyniki wyszukiwania według kategorii, wybierz klawisze **Ctrl** + **Q** , aby wyświetlić wszystkie wyniki z kolejnej kategorii. Po wyświetleniu ostatniej kategorii **Ctrl** + **Q** pokazuje kilka wyników z każdej kategorii. Naciśnij **klawisze CTRL** + **SHIFT** + **Q** , aby przejść przez kategorie w odwrotnej kolejności. Aby wyświetlić wszystkie wyniki wyszukiwania w kategorii, wybierz nazwę kategorii.

Możesz użyć następujących skrótów, aby ograniczyć wyszukiwanie do określonych kategorii.

|Kategoria|Skrót|Opis skrótu|
|--------------|--------------| - |
|Ostatnio używane|@mru<br /><br /> Na przykład `@mru font`|Wyświetla maksymalnie pięć elementów, które były **ostatnio używane**.|
|Menu|@menu<br /><br /> Na przykład `@menu project`|Ogranicza wyszukiwanie do elementów menu.|
|Opcje|@opt<br /><br /> Na przykład `@opt font`|Ogranicza wyszukiwanie do ustawień w oknie dialogowym **Opcje** .|
|Dokumenty|@doc<br /><br /> Na przykład `@doc program.cs`|Ogranicza wyszukiwanie do nazw plików i ścieżek otwartych dokumentów dla kryteriów wyszukiwania, ale nie przeszukuje tekstu wewnątrz samych plików.|

> [!NOTE]
> Skróty **General**  >  **klawiaturowe** można zmienić na stronie Ogólne w oknie dialogowym **Opcje** .

## <a name="show-previous-results"></a>Pokaż poprzednie wyniki

Wprowadzony termin wyszukiwania nie jest domyślnie utrwalany między sesjami wyszukiwania. Ciąg wyszukiwania jest wyczyszczony, jeśli szukasz terminu, Przenieś kursor poza obszar **szybkiego uruchamiania** , a następnie wróć. Aby zachować wyniki wyszukiwania, przejdź do okna dialogowego **Opcje** , wybierz pozycję **Szybkie uruchamianie**, a następnie wybierz pozycję **Pokaż wyniki wyszukiwania z poprzedniego wyszukiwania, gdy szybkie uruchamianie jest aktywowane.** . Przy następnym przeszukiwaniu pozostaw obszar szybkie uruchamianie i Wróć, szybkie uruchamianie spowoduje zachowanie ostatniego użytego terminu wyszukiwania, a także wyświetlenie wyników wyszukiwania.
