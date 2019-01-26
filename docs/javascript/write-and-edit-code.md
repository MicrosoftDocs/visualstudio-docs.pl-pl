---
title: Wprowadzenie do edycji dla deweloperów języka JavaScript
description: To wprowadzenie do edytora kodu w programie Visual Studio zawiera kilka sposobów, że program Visual Studio sprawia, że pisania, nawigowania i zrozumienie kodu JavaScript jest łatwiejsze.
ms.date: 12/13/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 4c272ba3009f3a9e947563cfa8c65843eab57067
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034132"
---
# <a name="learn-to-use-the-code-editor"></a>Dowiedz się, jak za pomocą edytora kodu

W tym krótkie wprowadzenie do edytora kodu w programie Visual Studio omówimy kilka sposobów, że program Visual Studio sprawia, że pisania, nawigowania i zrozumienie kodu łatwiej.

> [!TIP]
> Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo. W zależności od typu tworzenia aplikacji, które wykonujesz, użytkownik może być konieczne zainstalowanie **pakiet roboczy programowania Node.js** z programem Visual Studio.

W tym artykule przyjęto założenie, że już znasz za pomocą języka JavaScript. Jeśli nie masz, Sugerujemy, zobacz samouczek takich jak [utworzyć aplikację Node.js lub Express](../javascript/tutorial-nodejs.md) pierwszy.

## <a name="add-a-new-project-file"></a>Dodaj nowy plik projektu

Aby dodać nowe pliki do projektu, można użyć środowiska IDE.

1. Za pomocą projektu Otwórz w programie Visual Studio, kliknij prawym przyciskiem myszy folder lub węzeł projektu w Eksploratorze rozwiązań (w okienku po prawej stronie), a następnie wybierz **Dodaj** > **nowy element**.

1. W **nowy plik** okno dialogowe, w obszarze **ogólne** kategorii, wybierz typ pliku, który chcesz dodać, takich jak **plik JavaScript**, a następnie wybierz **Otwórz** .

    Nowy plik zostanie dodany do projektu, a zostanie on otwarty w edytorze.

## <a name="use-intellisense-to-complete-words"></a>Funkcja IntelliSense są używane do realizowania słów

Funkcja IntelliSense jest zasób nieocenione, gdy jesteś kodowania. Jego można wyświetlić informacje o dostępne elementy członkowskie typu lub szczegóły parametrów dla innego przeciążenia metody. W poniższym kodzie podczas wpisywania tekstu `Router()`, zobacz typy argumentów, które można przekazywać. Jest to nazywane pomocy dotyczącej sygnatur.

![Korzystanie z funkcji IntelliSense](../javascript/media/write-code-signature-checking.png)

Funkcja IntelliSense umożliwia również Dokończ wyraz, po wpisaniu małej liczby znaków, aby odróżnić go. Jeśli umieścisz kursor po `data` ciągu w następujący kod i wpisz `get`, IntelliSense opisano funkcje zdefiniowane wcześniej w kodzie lub zdefiniowane w bibliotece innych firm, które zostały dodane do projektu.

![Korzystanie z funkcji IntelliSense](../javascript/media/write-code-intellisense.png)

Technologia IntelliSense można również wyświetlić informacji na temat typów po najechaniu kursorem na element programistyczny.

Aby zapewnić informacje IntelliSense, usługa językowa służy TypeScript *d.ts* plików i komentarzy JSDoc. W przypadku typowych bibliotek JavaScript *d.ts* automatycznie pobieranych plików. Aby uzyskać więcej szczegółów na temat sposobu nabywa się informacje IntelliSense, zobacz [JavaScript IntelliSense](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json)

## <a name="check-syntax"></a>Sprawdź składnię

Usługa językowa używa ESLint sprawdzanie składni i Zaznaczanie błędów. Jeśli chcesz ustawić opcje dla składni sprawdzanie w edytorze wybierz **narzędzia** > **opcje** > **JavaScript/TypeScript**  >  **Zaznaczanie błędów**. Opcje Zaznaczanie błędów wskaż plik konfiguracyjny ESLint globalnego.

W poniższym kodzie zobaczysz zielony składni Wyróżnienie (zielone symbole) w wyrażeniu. Umieść kursor nad wyróżniania składni.

![Błąd składni w widoku](../javascript/media/write-code-syntax-checking.png)

Ostatni wiersz ten komunikat informuje, że usługa językowa oczekiwany przecinek (`,`). Zielony wężyk wyświetla ostrzeżenie. Czerwone faliste linie wskazują błędu.

W dolnym okienku można kliknąć opcje **lista błędów** kartę, aby zobaczyć ostrzeżenie i opis oraz nazwę pliku i numer wiersza.

![Wyświetl listę błędów](../javascript/media/write-code-error-list.png)

Ten kod można naprawić poprzez dodanie przecinka (`,`) przed `"data"`.

## <a name="comment-out-code"></a>Komentarz do kodu

Pasek narzędzi, który jest wiersz przycisków poniżej paska menu w programie Visual Studio, może pomóc zwiększyć produktywność kodowania. Na przykład, można przełączać tryb uzupełniania IntelliSense ([IntelliSense](../ide/using-intellisense.md) jest pomoc kodowania, który zawiera listę metod, między innymi dopasowania), zwiększ lub Zmniejsz wcięcie wiersza lub kod, który chcesz przekształcić w komentarz skompilować. W tej sekcji firma Microsoft będzie komentarz kodu.

Wybierz jeden lub więcej wierszy kodu w edytorze, a następnie wybierz **komentarz zaznaczonych wierszach** przycisk ![komentarz przycisk](../javascript/media/write-code-comment-out.png) na pasku narzędzi. Jeśli wolisz użyć klawiatury, naciśnij klawisz **Ctrl**+**K**, **Ctrl**+**C**.

Znaki komentarza JavaScript `//` są dodawane na początku każdego wybranego wiersza, aby przekształcić w komentarz kod.

## <a name="collapse-code-blocks"></a>Zwiń bloki kodu

Jeśli trzeba zwiększyć przejrzystość widok niektóre regiony kodu, możesz go zwinąć. Wybierz małe pole szarego znakiem minus znajdującym się w nim na marginesie pierwszy wiersz w funkcji. Lub, jeśli jesteś użytkownikiem klawiatury, umieść kursor gdziekolwiek w Konstruktorze kod i naciśnij klawisz **Ctrl**+**M**, **Ctrl**+**M** .

![Przycisk Zwiń konspekt](../javascript/media/write-code-collapse-code.png)

Blok kodu jest ustawiana na tylko pierwszy wiersz, następuje wielokropek (`...`). Aby rozwinąć blok kodu ponownie, kliknij pole szarego tego samego, który ma teraz znakiem plus lub naciśnij klawisz **Ctrl**+**M**, **Ctrl**+**M**  ponownie. Ta funkcja jest nazywana [konspekt](../ide/outlining.md) i jest szczególnie przydatne, gdy masz zwijanie długie funkcje lub całej klasy.

## <a name="view-definitions"></a>Wyświetlanie definicji

Edytor programu Visual Studio można łatwo sprawdzić definicji typu, funkcja itp. Jednym ze sposobów jest przejdź do pliku, który zawiera definicję, na przykład wybierając **przejdź do definicji** dowolnym odwołuje się do elementu programistycznego. Jeszcze szybszy sposób, który nie zmienia się od pliku pracujesz w jest użycie [Peek Definition](../ide/go-to-and-peek-definition.md#peek-definition). Umożliwia wgląd w definicji `render` metody w poniższym przykładzie.

Kliknij prawym przyciskiem myszy `render` i wybierz polecenie **Peek Definition** menu zawartości. Lub naciśnij **Alt**+**F12**.

   Okno wyskakujące pojawia się przy użyciu definicji elementu `render` metody. Można przewijać w oknie podręcznym lub nawet rzut oka na definicję innego typu niż peeked kodu.

   ![Okna definicji wglądu](../javascript/media/write-code-peek-definition.png)

Zamknij okno definicji podejrzeć, wybierając pole małych znakiem "x" w prawym górnym rogu okna podręcznego.

## <a name="use-code-snippets"></a>Używanie fragmentów kodu

Program Visual Studio oferuje przydatne *fragmenty kodu* , umożliwia szybkie i łatwe generowanie najczęściej używane bloki kodu. [Fragmenty kodu](../ide/code-snippets.md) są dostępne dla różnych języków programowania, m.in. JavaScript. Dodajmy `for` pętli do pliku kodu.

Umieść kursor w miejscu gdzie chcesz wstawić fragment kodu, kliknij prawym przyciskiem myszy i wybierz **fragment** > **Wstaw fragment kodu**.

![Fragment kodu w programie Visual Studio](../javascript/media/write-code-insert-snippet.png)

**Wstaw fragment kodu** pojawi się okno w edytorze. Wybierz **ogólne** a następnie kliknij dwukrotnie **dla** element na liście.

![Fragment kodu dotyczący pętli w programie Visual Studio](../javascript/media/write-code-insert-snippet-for-loop.png)

Spowoduje to dodanie `for` pętli fragment kodu:

```javascript
for (var i = 0; i < length; i++) {

}
```

Można przyjrzeć się fragmentów kodu dostępne dla danego języka, wybierając **Edytuj** > **IntelliSense** > **Wstaw fragment kodu**, a następnie Wybieranie folderu danego języka.

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu](../ide/code-snippets.md)
- [Przechodzenie do kodu](../ide/navigating-code.md)
- [Obramowanie](../ide/outlining.md)
- [Polecenia Przejdź do definicji i Zobacz definicję](../ide/go-to-and-peek-definition.md)
- [Refaktoryzacja](../ide/refactoring-in-visual-studio.md)
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
