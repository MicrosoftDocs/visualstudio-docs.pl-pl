---
title: Funkcje IntelliSense w edytorze XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e4c2f9f47b8b47f0258a9cb90e8350549d91fe7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938361"
---
# <a name="xml-editor-intellisense-features"></a>Funkcje IntelliSense w edytorze XML

Edytor XML udostępnia pełne funkcje IntelliSense porównywalne do innych edytorów języka podany w programie Visual Studio. W tej sekcji opisano, jak za pomocą funkcji IntelliSense języka definicji schematu XML (XSD) i dokumentów XSLT.

## <a name="intellisense-in-an-xsd-document"></a>Funkcja IntelliSense w dokumencie XSD
 Po schemat jest powiązany z dokumentem, masz dostęp do listy rozwijanej listy elementów oczekiwanego dowolnej chwili możesz wpisać `"<"` lub kliknij przycisk **wyświetlania listy członków obiektu** na listwie narzędziowej edytora XML. Aby uzyskać informacje o sposobach kojarzenia schematów z dokumentami XML, zobacz [Walidacja dokumentów XML](../xml-tools/xml-document-validation.md).

 Podczas wpisywania tekstu ilość miejsca od wewnątrz tagu początkowego, możesz także uzyskać listy rozwijanej, przedstawiający wszystkie atrybuty, które mogą być dodawane do bieżącego elementu.

 Podczas wpisywania `"="` dla wartości atrybutu lub cudzysłów otwierający dla wartości, możesz również uzyskać listę możliwych wartości dla tego atrybutu. Wartości są podane tylko, jeśli schemat zawiera wyliczany wartości zwrotne za pośrednictwem `xsd:enumeration` aspektami, czy dany atrybut znajduje się `Boolean` typu. Lista IntelliSense kodów znanych języków znajduje się również do `xml:lang` lub dowolnego `simpleType` który pochodzi od klasy `xsd:language`. Funkcja IntelliSense listę znanych `targetNamespace` wartości towarzyszy deklaracje przestrzeni nazw.

 Technologia IntelliSense listę możliwych wartości jest również udostępniany, gdy wpiszesz `">"` zamknięcie tagu początkowego, jeśli element jest `simpleType`. Zachowanie elementów jest podobne do zachowania w przypadku atrybutów, które opisano w poprzednim akapicie.

 Etykietki narzędzi są również wyświetlane na listach tych technologii IntelliSense, na podstawie `xsd:annotation` i `xsd:documentation` informacje znaleźć skojarzonego schematu.

## <a name="intellisense-in-an-xslt-document"></a>Funkcja IntelliSense w dokumencie XSLT
 Po dodaniu szablonie o podanej nazwie lub atrybutu w dokumencie XSLT, można użyć funkcji IntelliSense do wstawienia następujące czynności:

-   Ustawić atrybutu nazwy.

-   Tryby szablonu.

-   Nazwy szablonu.

-   Nazwy parametrów w danym trybie.

-   Nazwy parametru dla danego szablonie o podanej nazwie.

Aby uzyskać więcej informacji, zobacz [instruktażu: Używanie XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md) tematu.

## <a name="auto-completion"></a>Automatyczne uzupełnianie
 Edytor XML sprawia, że łatwiej XML do edycji, wypełniając wymaganej składni XML dla Ciebie. Jeśli na przykład wpisz następujący tag początkowy:

 `<book>`

 Edytor XML wypełnia tagu końcowego i umieszcza kursor po tagu początkowego. Oto przykład ("&#124;" Uwagi dotyczące pozycja kursora):

 `<book>`&#124;`</book>`

 Ponieważ wartości atrybutów musi zawsze mieć cudzysłowów, to edytor XML wypełnia cudzysłowów. Na przykład, wpisz następujące polecenie:

 `<book title=`

 Edytor XML dodaje cudzysłowu i umieszcza kursor w cudzysłowie:

 `<book title="`&#124;`"`

 Podobnie w edytorze XML również wstawia następującą składnię XML automatycznie dla Ciebie:

-   Zakończenie instrukcji przetwarzania:  `?>`

-   Koniec bloku CDATA: `]]>`

-   Zakończenie komentarz: `-->`

-   Zakończenie deklaracja DTD: `>`

Edytor XML ma również możliwość wstawiania przestrzeń nazw deklaracji, jeśli zostanie wybrany element kwalifikowaną przestrzeń nazw lub atrybutu z listy technologii IntelliSense i przestrzeń nazw dla tego elementu lub atrybutu nie jest jeszcze w zakresie.

Na przykład w przypadku wybrania `e:Book` elementu z listy technologii IntelliSense, w którym powiązany jest prefiks `http://books` przestrzeni nazw, która nie została zadeklarowana w dokumencie, w edytorze XML wstawia deklaracja wymaganej przestrzeni nazw. Wynikowy tekstu XML jest następująca:

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Parowanie nawiasów klamrowych
 Edytor XML zawiera nawias klamrowy wyróżnianie umożliwiają natychmiastowe informacje zwrotne na elementy, które zostały zamknięte. Można również użyć skrótu klawiaturowego (**Ctrl**+**]**) aby przejść z jednego nawias klamrowy do pasującego nawiasu klamrowego.

 Edytor XML ma następujące efekty dla następujących elementów:

-   Dopasowywanie tagiem początkowym i końcowym.

-   Jakaś para "\<" lub ">" nawiasy.

-   Początek i koniec komentarzy.

-   Początek i koniec instrukcji przetwarzania.

-   Początek i koniec bloki CDATA.

-   Początek i koniec DTD deklaracji.

-   Otwieranie i zamykanie cudzysłowy atrybutów.

## <a name="modify-the-intellisense-options"></a>Modyfikowanie opcji IntelliSense
 Funkcje IntelliSense i automatycznego uzupełniania są domyślnie włączone. Jednak to zmienić, modyfikując swoje **narzędzia** > **opcje** ustawienia.

 **Automatyczne wstawianie** części **różne** kontrolki strony następujące zachowanie:

|Nazwa|Opis|
|-|-----------------|
|Zamknij tagów|Wstawia Zamknij tagów dla nowych elementów.|
|Cudzysłowy atrybutu|Wstawia cudzysłowy wartości atrybutów, gdy wprowadzasz nazwę nowego atrybutu.|
|Innych znaczników|Kończy komentarze, CDATA, elementu DOCTYPE, instrukcje przetwarzania i innych deklaracji znaczników.|

### <a name="to-change-the-auto-completion-behavior"></a>Aby zmienić zachowanie automatyczne uzupełnianie

1.  Wybierz **opcje** z **narzędzia** menu.

2.  Rozwiń **edytora tekstów**, rozwiń węzeł **XML**i wybierz **różne**.

3.  Wprowadzaj żadnych zmian w **automatyczne wstawianie** sekcji, a następnie kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Przewodnik: Używanie XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)