---
title: Funkcja IntelliSense dla kodu języka R
description: Funkcji IntelliSense Visual Studio Wyświetla informacje dotyczące funkcji, elementach członkowskich obiektu, fragmenty kodu i uzupełnień, podczas wpisywania kodu R.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 3ce62d81a3a6fce4e59d43f088d06f0af7385708
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024087"
---
# <a name="intellisense"></a>IntelliSense

Funkcji IntelliSense Visual Studio Wyświetla informacje na temat funkcji można wywołać elementy członkowskie obiektów, argumenty funkcji i [fragmenty kodu](code-snippets-for-r.md) bezpośrednio w widoku w taki sposób, jak napisać kod. Ponadto wyświetla możliwe uzupełnienia podczas wpisywania i uzupełnia, gdy użytkownik naciśnie klawisz **kartę** lub **Enter** kluczy (zobacz [opcji edytora](editing-r-code-in-visual-studio.md#editor-options) dla **zaawansowane** karty). Funkcja IntelliSense jest dostępna w edytorze programu i [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md).

![Funkcja IntelliSense, wyświetlanie sygnatura funkcji](media/intellisense-function-signature.png)

Podczas pisania funkcji lub innych instrukcji, technologia IntelliSense zawiera automatyczne uzupełnianie menu filtrowane (case-sensitively), co wprowadzono już:

![Menu automatycznego uzupełniania IntelliSense](media/intellisense-auto-complete-menu.png)

Naciśnięcie klawisza **kartę** (lub **Enter**, lub **miejsca**, w zależności od konfiguracji opcji), wstawia elementu wybranego na liście rozwijanej. Możesz zmienić wybór, za pomocą klawiszy strzałek.

Funkcja IntelliSense zawiera też propozycje dla uczestników programu R obiektów:

![Sugestie funkcji IntelliSense dla elementów członkowskich obiektu](media/intellisense-auto-complete-r-objects.png)

Naciśnięcie klawisza **ESC** całkowicie odrzuci menu. Połącz Utwórz kopię zapasową przy użyciu **Ctrl**+**miejsca**.

Wpisywanie otwarcia `(` dla funkcji wywołania wstawia zamykającym `)` i wyświetlenie pomocy dotyczącej sygnatur, jak pokazano wcześniej:

![Pomocy dotyczącej sygnatur funkcji IntelliSense dla funkcji](media/intellisense-function-signature.png)

Ponownie **ESC** odrzuci okno podręczne; dla sygnatury funkcji, można przenieść go ponownie przy użyciu **Ctrl**+**Shift**+**miejsca** .

> [!Tip]
> Jeśli parametr pomocy ukrycie tekstowe podrzędne, naciśnij i przytrzymaj **Ctrl** , aby parametr półprzezroczyste tekst pomocy.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>Funkcja IntelliSense dla zmiennych i funkcji zdefiniowanych przez użytkownika

Funkcja IntelliSense dotyczy funkcje zdefiniowane przez użytkownika, w tym samym pliku, uzupełnianie parametr name:

![Funkcja IntelliSense dla funkcji zdefiniowanych przez użytkownika](media/intellisense-same-file-functions.png)

![Uzupełnianie parametrów przez funkcję IntelliSense dla funkcji zdefiniowanych przez użytkownika](media/intellisense-parameter-completion.png)

Funkcja IntelliSense ma zastosowanie również w przypadku zmiennych, w tym samym pliku i bieżącej sesji:

![Zmienna uzupełnianie przez funkcję IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> W oknie interaktywnym IntelliSense uwzględnia tylko nazwy w bieżącej sesji języka R: i ignoruje pliki w projekcie.

## <a name="code-suggestions"></a>Sugestie dotyczące kodu

Gdy żarówka (nazywane tagu inteligentnego) pojawi się na marginesie, Visual Studio sugeruje dostępne dla często używanych akcji to skrót. Na przykład, umieść kursor nad wiersz, który zawiera `library` instrukcji w edytorze, aby zobaczyć żarówki. Wybranie ikony żarówki powoduje wyświetlenie dostępnych opcji:

![Tagi inteligentne dla języka R w edytorze](media/intellisense-smart-tags.png)
