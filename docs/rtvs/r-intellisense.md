---
title: IntelliSense dla kodu R
description: Visual Studio IntelliSense wyświetla informacje o funkcjach, elementy członkowskie obiektu, fragmenty kodu i uzupełnienia podczas wpisywać kod R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 854f7d410e327ca92d0c5156d89bc21765e13cc7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999137"
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense wyświetla informacje o funkcjach, które można wywołać, członków obiektów, argumenty funkcji i [fragmenty kodu](code-snippets-for-r.md) bezpośrednio w widoku podczas pisania kodu. Wyświetla również możliwe uzupełnienia podczas pisania i kończy się po naciśnięciu **klawiszy Tab** lub **Enter** (zobacz [Opcje edytora](editing-r-code-in-visual-studio.md#editor-options) karty **Zaawansowane).** IntelliSense jest dostępny zarówno w edytorze, jak i [w oknie interaktywnym.](interactive-repl-for-r-in-visual-studio.md)

![IntelliSense z podpisem funkcji](media/intellisense-function-signature.png)

Podczas wpisywania funkcji lub innej instrukcji intelliSense udostępnia menu automatycznego uzupełniania filtrowane (z uwzględnieniem wielkości liter) według tego, co już wprowadzono:

![Menu automatycznego uzupełniania intellisense](media/intellisense-auto-complete-menu.png)

Naciśnięcie **klawisza Tab** (lub **Enter**, lub **Spacja**, w zależności od sposobu ustawiania opcji) powoduje wstawienie elementu wybranego z listy rozwijanej. Zaznaczenie można zmieniać za pomocą klawiszy strzałek.

IntelliSense zawiera również sugestie dla członków obiektów R:

![Sugestie intellisense dla elementów członkowskich obiektów](media/intellisense-auto-complete-r-objects.png)

Naciśnięcie **klawisza ESC** powoduje całkowite odrzucenie menu. Możesz go przywrócić za pomocą **klawisza Ctrl**+**Space**.

Wpisanie otworu `(` dla wywołania funkcji `)` powoduje wstawienie zamknięcia i wyświetlenie pomocy podpisu, jak pokazano wcześniej:

![Pomoc dotycząca podpisu IntelliSense dla funkcji](media/intellisense-function-signature.png)

Ponownie **ESC** odrzuca wyskakujące okienko; dla podpisów funkcji, można go ponownie przywołać za pomocą **klawisza Ctrl**+**Shift**+**Space**.

> [!Tip]
> Jeśli pomoc w parametrach zasłania tekst pod nim, naciśnij i przytrzymaj klawisz **Ctrl,** aby tekst pomocy parametru był przezroczysty.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense dla funkcji i zmiennych zdefiniowanych przez użytkownika

IntelliSense ma zastosowanie do funkcji zdefiniowanych przez użytkownika w tym samym pliku, w tym uzupełniania parametrów nazwy:

![IntelliSense dla funkcji zdefiniowanych przez użytkownika](media/intellisense-same-file-functions.png)

![Uzupełnianie parametrów IntelliSense dla funkcji zdefiniowanych przez użytkownika](media/intellisense-parameter-completion.png)

IntelliSense ma również zastosowanie do zmiennych w tym samym pliku i bieżącej sesji:

![Zakończenie zmiennej IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> W oknie interaktywnym intellisense uwzględnia tylko nazwy w bieżącej sesji języka R i ignoruje pliki w projekcie.

## <a name="code-suggestions"></a>Sugestie dotyczące kodu

Gdy żarówka (nazywana tagiem inteligentnym) pojawia się na marginesie, program Visual Studio sugeruje, że istnieje skrót dostępny dla często używanej akcji. Na przykład umieść wskaźnik myszy `library` na wierszu zawierającym instrukcję w edytorze, aby wyświetlić żarówkę. Wybór dostępnych opcji wyświetlania żarówki:

![Tagi inteligentne dla R w edytorze](media/intellisense-smart-tags.png)
