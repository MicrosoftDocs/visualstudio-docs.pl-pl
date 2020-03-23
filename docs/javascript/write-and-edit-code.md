---
title: Wprowadzenie do edycji dla programistów JavaScript
description: To wprowadzenie do edytora kodu w programie Visual Studio pokazuje niektóre ze sposobów, że visual studio sprawia, że pisanie, nawigacja i zrozumienie kodu JavaScript łatwiejsze.
ms.date: 12/13/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 111100038817d16d4655271f648aeb076bf1e9af
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62840835"
---
# <a name="learn-to-use-the-code-editor"></a>Dowiedz się, jak korzystać z edytora kodu

W tym krótkim wstępie do edytora kodu w programie Visual Studio przyjrzymy się niektórym sposobom, w jakie program Visual Studio ułatwia pisanie, nawigowanie i rozumienie kodu.

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads/) aby zainstalować ją bezpłatnie. W zależności od typu tworzenia aplikacji, które robisz, może być konieczne **zainstalowanie obciążenia deweloperskie Node.js** w programie Visual Studio.

W tym artykule założono, że jesteś już zaznajomiony z rozwojem JavaScript. Jeśli nie, sugerujemy, aby spojrzeć na samouczek, takich jak [Tworzenie Node.js i express aplikacji](../javascript/tutorial-nodejs.md) pierwszy.

## <a name="add-a-new-project-file"></a>Dodawanie nowego pliku projektu

Ide można użyć, aby dodać nowe pliki do projektu.

1. Po otwarciu projektu w programie Visual Studio kliknij prawym przyciskiem myszy folder lub węzeł projektu w Eksploratorze rozwiązań (prawe okienko) i wybierz pozycję **Dodaj** > **nowy element**.

1. W oknie dialogowym **Nowy plik** w kategorii **Ogólne** wybierz typ pliku, który chcesz dodać, na przykład **Plik JavaScript**, a następnie wybierz polecenie **Otwórz**.

    Nowy plik zostanie dodany do projektu i zostanie otwarty w edytorze.

## <a name="use-intellisense-to-complete-words"></a>Uzupełnianie wyrazów za pomocą funkcji IntelliSense

IntelliSense jest nieocenionym zasobem podczas kodowania. Może pokazać informacje o dostępnych elementów członkowskich typu lub szczegóły parametru dla różnych przeciążeń metody. W poniższym kodzie `Router()`po wpisaniu zobaczysz typy argumentów, które można przekazać. Jest to tak zwana pomoc dotycząca podpisu.

![Korzystanie z funkcji IntelliSense](../javascript/media/write-code-signature-checking.png)

Za pomocą programu IntelliSense można również ukończyć słowo po wpisaniu wystarczającej liczby znaków, aby je rozróżnić. Jeśli umieścisz kursor po `data` ciągu w następującym `get`kodzie i wpisz, IntelliSense wyświetli funkcje zdefiniowane wcześniej w kodzie lub zdefiniowane w bibliotece innej firmy, które zostały dodane do projektu.

![Korzystanie z funkcji IntelliSense](../javascript/media/write-code-intellisense.png)

IntelliSense może również wyświetlać informacje o typach po umieszczeniu wskaźnika myszy na elementach programowania.

Aby dostarczać informacje intellisense, usługa językowa może używać plików *d.ts* TypeScript i komentarzy JSDoc. W przypadku większości popularnych bibliotek JavaScript pliki *d.ts* są nabywane automatycznie. Aby uzyskać więcej informacji o tym, jak informacje intellisense jest pobierana, zobacz [JavaScript IntelliSense](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json)

## <a name="check-syntax"></a>Sprawdzanie składni

Usługa języka używa ESLint do sprawdzania składni i linting. Jeśli chcesz ustawić opcje sprawdzania składni w edytorze, wybierz opcję**Opcje** >  **narzędzi** > **JavaScript/TypeScript** > **Linting**. Opcje lintingu wskazują na globalny plik konfiguracyjny ESLint.

W poniższym kodzie zobaczysz zielone podświetlanie składni (zielone squiggles) na wyrażenie. Umieść wskaźnik myszy na podświetlaniu składni.

![Błąd składni widoku](../javascript/media/write-code-syntax-checking.png)

Ostatni wiersz tego komunikatu informuje, że usługa językowa oczekuje przecinka (`,`). Zielona falimista oznacza ostrzeżenie. Czerwone falisze wskazują na błąd.

W dolnym okienku możesz kliknąć kartę **Lista błędów,** aby wyświetlić ostrzeżenie i opis wraz z numerem pliku i wiersza.

![Wyświetl listę błędów](../javascript/media/write-code-error-list.png)

Ten kod można naprawić, dodając`,`przecinek `"data"`( ) przed .

## <a name="comment-out-code"></a>Skomentuj kod

Pasek narzędzi, który jest wiersz przycisków pod paskiem menu w programie Visual Studio, może pomóc zwiększyć produktywność podczas kodowania. Na przykład można przełączyć tryb ukończenia IntelliSense[(IntelliSense](../ide/using-intellisense.md) jest pomocą kodowania, która wyświetla listę pasujących metod, między innymi), zwiększyć lub zmniejszyć wcięcie wiersza lub skomentować kod, który nie ma być skompilowany. W tej sekcji pokomentujemy kod.

Zaznacz jeden lub więcej wierszy kodu w edytorze, a ![następnie](../javascript/media/write-code-comment-out.png) wybierz przycisk **Wykomentuj wybrane wiersze** Przycisk Wyjmij na pasku narzędzi. Jeśli wolisz używać klawiatury, naciśnij **klawisze Ctrl**+**K**, **Ctrl**+**C**.

Znaki komentarza JavaScript `//` są dodawane na początku każdego wybranego wiersza, aby skomentować kod.

## <a name="collapse-code-blocks"></a>Zwijanie bloków kodu

Jeśli chcesz uporządkować widok niektórych regionów kodu, możesz go zwinąć. Wybierz małe szare pole ze znakiem minus wewnątrz niego na marginesie pierwszego wiersza funkcji. Lub, jeśli jesteś użytkownikiem klawiatury, umieść kursor w dowolnym miejscu w kodzie konstruktora i naciśnij **klawisze Ctrl**+**M**, **Ctrl**+**M**.

![Przycisk zwijanie konspektów](../javascript/media/write-code-collapse-code.png)

Blok kodu zwija się tylko do pierwszego wiersza, po którym następuje wielokropek (`...`). Aby ponownie rozwinąć blok kodu, kliknij to samo szare pole, w które ma teraz znak plus, lub ponownie naciśnij **klawisze Ctrl**+**M**, **Ctrl**+**M.** Ta funkcja jest [nazywana tworzeniem przespekk i](../ide/outlining.md) jest szczególnie przydatna w przypadku zwijania długich funkcji lub całych klas.

## <a name="view-definitions"></a>Wyświetlanie definicji

Edytor programu Visual Studio ułatwia sprawdzanie definicji typu, funkcji itp. Jednym ze sposobów jest przejście do pliku, który zawiera definicję, na przykład wybierając **Przejdź do definicji** w dowolnym miejscu, do którego odwołuje się element programowania. Jeszcze szybszym sposobem, który nie odsunie fokus od pliku, w który pracujesz, jest użycie [funkcji Peek Definition](../ide/go-to-and-peek-definition.md#peek-definition). Zajrzyjmy do definicji `render` metody w poniższym przykładzie.

Kliknij prawym `render` przyciskiem myszy i wybierz z menu treści **opcję Peek Definition.** Lub naciśnij **klawisz Alt**+**F12**.

   Zostanie wyświetlonych okno podręczne z `render` definicją metody. Możesz przewijać w wyskakującym oknie, a nawet zajrzeć do definicji innego typu z zaglądanego kodu.

   ![Okno definicji wglądu](../javascript/media/write-code-peek-definition.png)

Zamknij okno definicji zaglądanego, wybierając małe pole z literą "x" w prawym górnym rogu okna podręcznego.

## <a name="use-code-snippets"></a>Używanie fragmentów kodu

Visual Studio zawiera przydatne *fragmenty kodu,* których można użyć do szybkiego i łatwego generowania często używanych bloków kodu. [Fragmenty kodu](../ide/code-snippets.md) są dostępne dla różnych języków programowania, w tym JavaScript. Dodajmy pętlę `for` do pliku kodu.

Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu, kliknij prawym przyciskiem myszy i wybierz polecenie > **Urywek wstawiania fragmentu kodu**. **Snippet**

![Fragment kodu w programie Visual Studio](../javascript/media/write-code-insert-snippet.png)

W edytorze pojawi się pole **Wstaw fragment** kodu. Wybierz **pozycję Ogólne,** a następnie kliknij dwukrotnie **element for** item na liście.

![Fragment kodu dla pętli for w programie Visual Studio](../javascript/media/write-code-insert-snippet-for-loop.png)

Spowoduje to `for` dodanie fragmentu kodu pętli do kodu:

```javascript
for (var i = 0; i < length; i++) {

}
```

Możesz sprawdzić dostępne fragmenty kodu dla swojego języka, wybierając **pozycję Edytuj** > **fragment kodu wstawiania****intellisense,** > a następnie wybierając folder języka.

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu](../ide/code-snippets.md)
- [Nawigowanie po kodzie](../ide/navigating-code.md)
- [Tworzenie konspektu](../ide/outlining.md)
- [Przejdź do definicji i Zobacz definicję](../ide/go-to-and-peek-definition.md)
- [Refaktoryzacja](../ide/refactoring-in-visual-studio.md)
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
