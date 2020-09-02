---
title: Kod IntelliSense dla języka R
description: Program Visual Studio IntelliSense wyświetla informacje o funkcjach, elementach członkowskich obiektów, fragmentach kodu i uzupełnianiu podczas wpisywania kodu języka R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 854f7d410e327ca92d0c5156d89bc21765e13cc7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62999137"
---
# <a name="intellisense"></a>IntelliSense

Program Visual Studio IntelliSense wyświetla informacje o funkcjach, które można wywołać, składowe obiektów, argumenty funkcji i [fragmenty kodu](code-snippets-for-r.md) bezpośrednio w widoku podczas pisania kodu. Wyświetla również możliwe zakończenia podczas pisania i kończy się po naciśnięciu klawisza **Tab** lub **wprowadź** klucze (zobacz [Opcje edytora](editing-r-code-in-visual-studio.md#editor-options) na karcie **Zaawansowane** ). Technologia IntelliSense jest dostępna zarówno w edytorze, jak i w [oknie interaktywnym](interactive-repl-for-r-in-visual-studio.md).

![Technologia IntelliSense pokazująca sygnaturę funkcji](media/intellisense-function-signature.png)

Podczas wpisywania funkcji lub innej instrukcji funkcja IntelliSense udostępnia menu autouzupełniania (z uwzględnieniem wielkości liter), które zostało już wprowadzone:

![Menu funkcji IntelliSense Autouzupełnianie](media/intellisense-auto-complete-menu.png)

Naciskając klawisz **Tab** (lub **Enter**lub **spację**, w zależności od sposobu ustawiania opcji) wstawia element wybrany na liście rozwijanej. Zaznaczenie można zmienić za pomocą klawiszy strzałek.

Technologia IntelliSense oferuje również sugestie dotyczące elementów członkowskich obiektów języka R:

![Sugestie funkcji IntelliSense dotyczące elementów członkowskich obiektów](media/intellisense-auto-complete-r-objects.png)

Naciśnięcie klawisza **ESC** całkowicie odrzuci menu. Można je przywrócić za pomocą **klawisza Ctrl** + **Space**.

Wpisanie otwarcia `(` dla wywołania funkcji spowoduje wstawienie zamykania `)` i wyświetlenie pomocy dotyczącej sygnatur, jak pokazano wcześniej:

![Pomoc dotycząca podpisu IntelliSense dla funkcji](media/intellisense-function-signature.png)

Ponownie wyskakujące okienko **ESC** zostanie odrzucone. w przypadku podpisów funkcji można przywrócić ją ponownie, **naciskając**klawisz + **SHIFT** + **Space**.

> [!Tip]
> Jeśli parametr pomaga zasłaniać tekst znajdujący się poniżej, naciśnij i przytrzymaj klawisz **Ctrl** , aby uzyskać przezroczystość tekstu pomocy.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>Technologia IntelliSense dla funkcji i zmiennych zdefiniowanych przez użytkownika

Technologia IntelliSense stosuje się do funkcji zdefiniowanych przez użytkownika w tym samym pliku, łącznie z uzupełnianiem parametru name:

![Technologia IntelliSense dla funkcji zdefiniowanych przez użytkownika](media/intellisense-same-file-functions.png)

![Uzupełnianie parametrów IntelliSense dla funkcji zdefiniowanych przez użytkownika](media/intellisense-parameter-completion.png)

Technologia IntelliSense stosuje się również do zmiennych w tym samym pliku i bieżącej sesji:

![Uzupełnienie zmiennej IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> W oknie interaktywnym technologia IntelliSense traktuje tylko nazwy w bieżącej sesji R i ignoruje pliki w projekcie.

## <a name="code-suggestions"></a>Sugestie dotyczące kodu

Gdy na marginesie pojawi się żarówka (o nazwie tag inteligentny), program Visual Studio sugeruje, że jest dostępny skrót dla często używanej akcji. Na przykład Umieść kursor nad wierszem zawierającym `library` instrukcję w edytorze, aby wyświetlić żarówkę. Wybór żarówki wyświetla dostępne opcje:

![Tagi inteligentne dla języka R w edytorze](media/intellisense-smart-tags.png)
