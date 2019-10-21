---
title: Funkcje IntelliSense edytora XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a44af076e8663e525e33727a24aa93f9391f4b5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603961"
---
# <a name="xml-editor-intellisense-features"></a>Funkcje IntelliSense w edytorze XML

Edytor XML zapewnia pełne funkcje IntelliSense porównywalne do innych edytorów języka dostępnych w programie Visual Studio. W tej sekcji wyjaśniono, jak można używać technologii IntelliSense z dokumentami XML i XSLT (Schema Definition Language).

## <a name="intellisense-in-an-xsd-document"></a>Technologia IntelliSense w dokumencie XSD

Po skojarzeniu schematu z Twoim dokumentem otrzymujesz listę rozwijaną oczekiwanych elementów przy każdym wpisaniu `"<"` lub kliknij przycisk **Wyświetl listę elementów członkowskich obiektu** na pasku narzędzi edytora XML.

![Przycisk wyświetlania listy elementów członkowskich obiektów](media/display-object-member-list-xml.png)

Aby uzyskać informacje na temat kojarzenia schematów z dokumentami XML, zobacz [Walidacja dokumentu XML](../xml-tools/xml-document-validation.md).

Gdy wpiszesz miejsce z wewnątrz tagu początkowego, uzyskasz także listę rozwijaną zawierającą wszystkie atrybuty, które można dodać do bieżącego elementu.

Po wpisaniu `"="` dla wartości atrybutu lub cudzysłowu otwierającego dla wartości można również uzyskać listę możliwych wartości dla tego atrybutu. Wartości są dostępne tylko wtedy, gdy schemat zawiera wartości wyliczane za pośrednictwem `xsd:enumeration` aspektów lub jeśli atrybut jest typem `Boolean`. Dostępna jest również lista funkcji IntelliSense znanych kodów języka dla `xml:lang` lub wszelkich `simpleType`, które pochodzą z `xsd:language`. Lista funkcji IntelliSense znanych `targetNamespace` wartości jest udostępniana dla deklaracji przestrzeni nazw.

Lista funkcji IntelliSense możliwych wartości jest również podana podczas wpisywania `">"`, aby zamknąć tag początkowy, jeśli element jest `simpleType`. Zachowanie dla elementów jest podobne do zachowania dla atrybutów opisanych w poprzednim akapicie.

Etykietki narzędzi są również wyświetlane na tych listach IntelliSense na podstawie `xsd:annotation` i `xsd:documentation` informacji znajdujących się w skojarzonym schemacie.

## <a name="intellisense-in-an-xslt-document"></a>Technologia IntelliSense w dokumencie XSLT

Po dodaniu nazwanego szablonu lub atrybutu do dokumentu XSLT możesz użyć funkcji IntelliSense, aby wstawić następujące elementy:

- Nazwy zestawów atrybutów.

- Tryby szablonów.

- Nazwy szablonów.

- Nazwy parametrów dla danego trybu.

- Nazwy parametrów dla danego szablonu o podanej nazwie.

Aby uzyskać więcej informacji, zobacz [Przewodnik: korzystanie z funkcji INTELLISENSE XSLT](../xml-tools/walkthrough-using-xslt-intellisense.md) .

## <a name="auto-completion"></a>Autouzupełnianie

Edytor XML ułatwia również edytowanie kodu XML przez wypełnienie wymaganej składni XML. Na przykład, jeśli wpiszesz następujący tag początkowy:

`<book>`

Edytor XML wypełnia tag końcowy i umieszcza kursor po tagu początkowym. Poniżej znajduje się przykład ("&#124;" uwagi dotyczące położenia kursora):

`<book>`&#124;`</book>`

Ponieważ wartości atrybutów muszą zawsze mieć cudzysłowy, Edytor XML wypełnia cudzysłowy. Na przykład, jeśli wpiszesz następujące polecenie:

`<book title=`

Edytor XML dodaje cudzysłowy i położenie kursora między cudzysłowami:

`<book title="`&#124;`"`

Podobnie Edytor XML automatycznie wstawia również następującą składnię XML:

- Zakończ instrukcję przetwarzania: `?>`

- Zakończ blok CDATA: `]]>`

- Zakończ Dodawanie komentarza: `-->`

- Zakończenie deklaracji DTD: `>`

Edytor XML ma także możliwość wstawiania deklaracji przestrzeni nazw w przypadku wybrania z listy funkcji IntelliSense elementu lub atrybutu z przestrzeni nazw, a przestrzeń nazw dla tego elementu lub atrybutu nie należy jeszcze do zakresu.

Jeśli na przykład wybierzesz element `e:Book` z listy IntelliSense, w której prefiks jest powiązany z przestrzenią nazw `http://books`, która nie została zadeklarowana w dokumencie, Edytor XML wstawia wymaganą deklarację przestrzeni nazw. Poniżej znajduje się otrzymany tekst XML:

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Dopasowywanie nawiasów klamrowych

Edytor XML zawiera wyróżnione nawiasy klamrowe w celu uzyskania natychmiastowej opinii na temat elementów, które właśnie zostały zamknięte. Możesz również użyć skrótu klawiaturowego (**Ctrl** + **]** ), aby przeskoczyć z jednego nawiasu klamrowego do pasującego nawiasu klamrowego.

Edytor XML wykonuje tę czynności dla następujących elementów:

- Dopasowanie tagów początkowych i końcowych.

- Dowolna para nawiasów ostrych "\<" lub ">".

- Początek i koniec komentarzy.

- Początek i koniec instrukcji przetwarzania.

- Początek i koniec bloków CDATA.

- Początek i koniec deklaracji DTD.

- Otwieranie i zamykanie cudzysłowu dla atrybutów.

## <a name="modify-the-intellisense-options"></a>Modyfikowanie opcji IntelliSense

Funkcje IntelliSense i automatycznego uzupełniania są domyślnie włączone. Można to jednak zmienić, modyfikując **narzędzia**  >  ustawienia**opcji** .

Sekcja **autoinsert** na stronie **różnej** kontroluje następujące zachowanie:

|Nazwa|Opis|
|-|-----------------|
|Zamknij Tagi|Wstawia tagi zamykające dla nowych elementów.|
|Cudzysłowy atrybutów|Wstawia cudzysłowy wartości atrybutów po wprowadzeniu nowej nazwy atrybutu.|
|Inne znaczniki|Uzupełnia komentarze, CDATA, DOCTYPE, instrukcje przetwarzania i inne deklaracje znaczników.|

### <a name="to-change-the-auto-completion-behavior"></a>Aby zmienić zachowanie automatycznego uzupełniania

1. Wybierz **Opcje** z menu **Narzędzia** .

2. Rozwiń węzeł **Edytor tekstu**, rozwiń pozycję **XML**i wybierz pozycję **różne**.

3. Wprowadź zmiany w sekcji **autoinsert** i kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Przewodnik: Używanie XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)