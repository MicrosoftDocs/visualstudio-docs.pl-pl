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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62a53d29e7d72c10b3b7b9f295cb5b7adebab45e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55949164"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Szybkie uruchamianie, środowisko, opcje — okno dialogowe

Możesz użyć **Szybkie uruchamianie** do szybkiego wyszukiwania i wykonywanie akcji dla zasobów IDE, takich jak opcje, szablony menu. Nie można użyć **Szybkie uruchamianie** wyszukiwania kodu i symbole. **Szybkie uruchamianie** pole wyszukiwania znajduje się w prawym górnym rogu paska menu i jest dostępny, wybierając klawisze Ctrl + Q. Po prostu wprowadź wyszukiwany ciąg w polu. Do wyszukiwania ciągów zawierających @, użyj ”@@”. 

**Szybkie uruchamianie** jest włączona domyślnie po zainstalowaniu programu Visual Studio. Na pasku menu, można wyświetlić lub ukryć **Szybkie uruchamianie** , wybierając **narzędzia**, **opcje**. Rozwiń **środowisk** węzła, a następnie wybierz **Szybkie uruchamianie**. Zaznacz lub wyczyść **Włącz pasek Szybkie uruchamianie** pole wyboru. Można również włączyć lub wyłączyć kategorie wyszukiwania na tej stronie.

## <a name="category-list"></a>Lista kategorii

Szybkie uruchomieni wyszukiwania są wyświetlane w czterech kategorii: **Większość ostatnio używane**, **menu**, **opcje**, i **otwarte dokumenty**, wraz z liczbą elementów w kategorii. Przechodzenie za pośrednictwem wyników wyszukiwania według kategorii, wybierz klawisze Ctrl + Q, aby Pokaż wszystkie wyniki z kategorii dalej. Po ostatnim kategoria zostanie wyświetlona, Ctrl + Q pokazuje kilka wyniki z każdej kategorii. Ctrl + Shift + Q służy do nawigowania do kategorii w odwrotnej kolejności. Aby wyświetlić wszystkie wyniki wyszukiwania w kategorii, wybierz nazwę kategorii.

Można użyć następujących skrótów, aby ograniczyć wyszukiwanie do określonej kategorii.

|Kategoria|Skrót|Opis skrótów|
|--------------|--------------| - |
|Ostatnio używane|@mru<br /><br /> Na przykład:`@mru font`|Wyświetla maksymalnie pięć elementów, które **ostatnio używane**.|
|Menu|@menu<br /><br /> Na przykład:`@menu font`|Ogranicza wyszukiwanie do elementów menu.|
|Opcje|@opt<br /><br /> Na przykład:`@opt font`|Ogranicza wyszukiwanie do ustawienia w **opcje** okno dialogowe.|
|Dokumenty|@doc<br /><br /> Na przykład:`@doc font`|Ogranicza wyszukiwanie do nazw plików oraz ścieżek otwarte dokumenty kryteriów wyszukiwania, ale nie wyszukuje tekst wewnątrz same pliki.|

> [!NOTE]
> Klawisze skrótów można zmienić na **ogólne**, **klawiatury** strony w **opcje** okno dialogowe.

## <a name="show-previous-results"></a>Pokaż poprzednie wyniki

Domyślnie termin wyszukiwania, które można wprowadzić nie są utrwalane między sesjami wyszukiwania. Ciąg wyszukiwania jest wyczyszczone, jeśli wyszukasz termin, przesuń kursor poza **Szybkie uruchamianie** obszaru, a następnie przejdź kopii. Do przechowywania wyników wyszukiwania, przejdź do **opcje** okna dialogowego wybierz **Szybkie uruchamianie**, a następnie wybierz pozycję **Pokaż wyniki poprzedniego wyszukiwania gdy pasek Szybkie uruchamianie jest aktywny.** Pole wyboru. Następnym razem, przeprowadź wyszukiwanie lub pozostaw obszaru szybkiego uruchamiania, a wrócić, szybkiego uruchamiania będzie zachowują wyszukiwany termin, ostatnio używane i również wyświetlanie wyników wyszukiwania.

Aby uzyskać najnowsze porady i wskazówki dotyczące korzystania z **Szybkie uruchamianie**, zobacz [Blog dotyczący programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=236054).

## <a name="see-also"></a>Zobacz też

- [Środowisko, Opcje — okno dialogowe](../../ide/reference/environment-options-dialog-box.md)