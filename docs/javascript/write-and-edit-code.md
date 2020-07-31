---
title: Wprowadzenie do edytowania dla deweloperów języka JavaScript
description: Wprowadzenie do edytora kodu w programie Visual Studio pokazuje kilka sposobów, w których program Visual Studio ułatwia pisanie, nawigowanie i zrozumienie kodu JavaScript.
ms.date: 12/13/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f48e7a8be8d902a487ae4f7fdac9e6d85f7b5517
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2020
ms.locfileid: "87453758"
---
# <a name="learn-to-use-the-code-editor"></a>Dowiedz się, jak używać edytora kodu

W tym krótkim wprowadzeniu do edytora kodu w programie Visual Studio zapoznajemy się z innymi sposobami, w których program Visual Studio wykonuje pisanie, nawigowanie i zrozumienie kodu.

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie. W zależności od typu opracowywanej aplikacji może być konieczne zainstalowanie **Node.js obciążenia programistycznego** w programie Visual Studio. Aby uzyskać więcej informacji na temat pobierania usługi językowej dla języka TypeScript, zobacz [Obsługa TypeScript](../javascript/javascript-in-vs-2019.md#typescript-support).

W tym artykule założono, że znasz już programowanie JavaScript. Jeśli nie, zalecamy zaprezentowanie samouczka, takiego jak najpierw [utwórz Node.js i aplikację Express](../javascript/tutorial-nodejs.md) .

## <a name="add-a-new-project-file"></a>Dodaj nowy plik projektu

Aby dodać nowe pliki do projektu, można użyć IDE.

1. Gdy projekt jest otwarty w programie Visual Studio, kliknij prawym przyciskiem myszy folder lub węzeł projektu w Eksplorator rozwiązań (prawego okienka) i wybierz polecenie **Dodaj**  >  **nowy element**.

1. W oknie dialogowym **nowy plik** w obszarze Kategoria **ogólna** wybierz typ pliku, który chcesz dodać, taki jak **plik JavaScript**, a następnie wybierz polecenie **Otwórz**.

    Nowy plik zostanie dodany do projektu i otwarty w edytorze.

## <a name="use-intellisense-to-complete-words"></a>Korzystanie z funkcji IntelliSense do uzupełniania wyrazów

Technologia IntelliSense jest niecennym zasobem podczas kodowania. Można wyświetlić informacje o dostępnych elementach członkowskich typu lub szczegółach parametrów dla różnych przeciążeń metody. W poniższym kodzie, gdy wpiszesz `Router()` , zobaczysz typy argumentów, które można przekazać. Jest to tzw. Pomoc dotycząca podpisu.

![Korzystanie z funkcji IntelliSense](../javascript/media/write-code-signature-checking.png)

Możesz również użyć funkcji IntelliSense, aby zakończyć wyraz po wpisaniu wystarczającej liczby znaków, aby odróżnić go. Jeśli umieścisz kursor po `data` ciągu w poniższym kodzie i typie `get` , funkcja IntelliSense wyświetli funkcje zdefiniowane wcześniej w kodzie lub zdefiniowane w bibliotece innej firmy, która została dodana do projektu.

![Korzystanie z funkcji IntelliSense](../javascript/media/write-code-intellisense.png)

Funkcja IntelliSense może również wyświetlać informacje o typach po umieszczeniu wskaźnika myszy na elementach programistycznych.

Aby zapewnić informacje o technologii IntelliSense, usługa języka może używać plików TypeScript *d. TS* i komentarzy JSDoc. Dla najpopularniejszych bibliotek JavaScript są automatycznie uzyskiwane pliki *d. TS* . Aby uzyskać więcej informacji na temat sposobu uzyskiwania informacji IntelliSense, zobacz [JavaScript IntelliSense](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json)

## <a name="check-syntax"></a>Sprawdź składnię

Usługa języka używa ESLint, aby zapewnić sprawdzanie składni i zaznaczanie błędów. Jeśli musisz ustawić opcje sprawdzania składni w edytorze, wybierz pozycję **Narzędzia**  >  **Opcje**  >  **JavaScript/TypeScript**  >  **Zaznaczanie błędów**. Opcje Zaznaczanie błędów wskazują na globalny plik konfiguracyjny ESLint.

W poniższym kodzie zobaczysz wyrażenie z wyróżnioną zieloną składnią (zieloną formułą). Umieść kursor nad wyróżnioną składnią.

![Wyświetl błąd składniowy](../javascript/media/write-code-syntax-checking.png)

Ostatni wiersz tego komunikatu informuje, że usługa języka oczekuje przecinka ( `,` ). Zielona zygzakowata wskazuje na ostrzeżenie. Czerwona zygzakowata wskazuje na błąd.

W dolnym okienku możesz kliknąć kartę **Lista błędów** , aby wyświetlić ostrzeżenie i opis wraz z nazwą pliku i numerem wiersza.

![Wyświetl listę błędów](../javascript/media/write-code-error-list.png)

Możesz naprawić ten kod przez dodanie przecinka ( `,` ) przed `"data"` .

Aby uzyskać dodatkowe informacje na temat Zaznaczanie błędów, zobacz [Zaznaczanie błędów](https://github.com/microsoft/JSTSdocs/blob/master/articles/editor/linting.md).

## <a name="comment-out-code"></a>Dodawanie komentarza do kodu

Pasek narzędzi, który jest wierszem przycisków na pasku menu w programie Visual Studio, może pomóc zwiększyć produktywność podczas pisania kodu. Można na przykład przełączyć tryb uzupełniania IntelliSense ([IntelliSense](../ide/using-intellisense.md) to pomoc dla kodu, która wyświetla listę zgodnych metod, między innymi), zwiększyć lub zmniejszyć wcięcie linii albo dodać komentarz do kodu, który nie ma być kompilowany. W tej sekcji dodamy komentarz dotyczący kodu.

Wybierz co najmniej jeden wiersz kodu w edytorze, a następnie wybierz przycisk Dodaj **komentarz do zaznaczonego wiersza** ![ ](../javascript/media/write-code-comment-out.png) na pasku narzędzi. Jeśli wolisz korzystać z klawiatury, naciśnij **klawisze CTRL** + **K**, **Ctrl +** + **C**.

Znaki komentarza JavaScript `//` są dodawane na początku każdego zaznaczonego wiersza w celu dodania komentarza do kodu.

## <a name="collapse-code-blocks"></a>Zwijanie bloków kodu

Jeśli musisz odkodować swój widok niektórych regionów kodu, możesz go zwinąć. Wybierz Małe szare pole ze znakiem minus wewnątrz niego na marginesie pierwszego wiersza funkcji. Jeśli jesteś użytkownikiem klawiatury, umieść kursor w dowolnym miejscu w kodzie konstruktora i naciśnij klawisze **Ctrl** + **m**, **Ctrl** + **m**.

![Przycisk zwijania konspektu](../javascript/media/write-code-collapse-code.png)

Blok kodu jest zwijany tylko do pierwszego wiersza, a po nim wielokropek ( `...` ). Aby ponownie rozwinąć blok kodu, kliknij szare pole, które ma teraz znak plus, lub naciśnij klawisze **Ctrl** + **m**, **Ctrl** + **m** ponownie. Ta funkcja jest nazywana [tworzeniem konspektu](../ide/outlining.md) i jest szczególnie przydatna w przypadku zwijania długich funkcji lub całych klas.

## <a name="view-definitions"></a>Definicje widoków

Edytor programu Visual Studio ułatwia sprawdzanie definicji typu, funkcji itp. Jednym ze sposobów jest przechodzenie do pliku, który zawiera definicję, na przykład po wybraniu opcji **Przejdź do definicji** gdziekolwiek element programowania jest przywoływany. Jeszcze szybszym sposobem, aby nie przenieść fokusu z pliku, w którym pracujesz, jest użycie [definicji wglądu](../ide/go-to-and-peek-definition.md#peek-definition). Przejdźmy do definicji `render` metody w poniższym przykładzie.

Kliknij prawym przyciskiem myszy `render` , a następnie wybierz polecenie **Podgląd definicji** z menu zawartość. Lub naciśnij klawisze **Alt** + **F12**.

   Zostanie wyświetlone okno podręczne z definicją `render` metody. Można przewijać w oknie podręcznym, a nawet z dokładnością do definicji innego typu.

   ![Okno definicji wglądu](../javascript/media/write-code-peek-definition.png)

Zamknij okno Definicja wglądu, wybierając małe pole z symbolem "x" w prawym górnym rogu okna podręcznego.

## <a name="use-code-snippets"></a>Używanie fragmentów kodu

Program Visual Studio oferuje przydatne *fragmenty kodu* , za pomocą których można szybko i łatwo generować często używane bloki kodu. [Fragmenty kodu](../ide/code-snippets.md) są dostępne dla różnych języków programowania, w tym JavaScript. Dodajmy `for` pętlę do pliku z kodem.

Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu, kliknij prawym przyciskiem myszy **i wybierz Wstaw fragment kodu**  >  **Insert Snippet**.

![Fragment kodu w programie Visual Studio](../javascript/media/write-code-insert-snippet.png)

W edytorze pojawi się pole **Wstaw** wstawka. Wybierz pozycję **Ogólne** , a następnie kliknij dwukrotnie pozycję **dla** elementu na liście.

![Fragment kodu dla pętli for w programie Visual Studio](../javascript/media/write-code-insert-snippet-for-loop.png)

Spowoduje to dodanie `for` fragmentu pętli do kodu:

```javascript
for (var i = 0; i < length; i++) {

}
```

Możesz sprawdzić dostępne fragmenty kodu dla danego języka, wybierając pozycję **Edytuj**  >  **IntelliSense**  >  **wstawkę**IntelliSense, a następnie wybierając folder języka.

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu](../ide/code-snippets.md)
- [Nawiguj po kodzie](../ide/navigating-code.md)
- [Tworzenie konspektu](../ide/outlining.md)
- [Przejdź do definicji i Zobacz definicję](../ide/go-to-and-peek-definition.md)
- [Refaktoryzacja](../ide/refactoring-in-visual-studio.md)
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
