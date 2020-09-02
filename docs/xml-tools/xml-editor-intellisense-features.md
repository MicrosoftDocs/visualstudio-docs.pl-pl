---
title: Funkcje IntelliSense edytora XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 609684452190bf7471f90fee75f66dbb2fcbec8e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592389"
---
# <a name="xml-editor-intellisense-features"></a>Funkcje IntelliSense w edytorze XML

Edytor XML zapewnia pełne funkcje IntelliSense porównywalne do innych edytorów języka dostępnych w programie Visual Studio. W tej sekcji wyjaśniono, jak można używać technologii IntelliSense z dokumentami XML i XSLT (Schema Definition Language).

## <a name="intellisense-in-an-xsd-document"></a>Technologia IntelliSense w dokumencie XSD

Po skojarzeniu schematu z dokumentem otrzymujesz listę rozwijaną oczekiwanych elementów za każdym razem, gdy wpiszesz, `"<"` lub kliknij przycisk **Wyświetl listę elementów członkowskich obiektu** na pasku narzędzi edytora XML.

![Przycisk wyświetlania listy elementów członkowskich obiektów](media/display-object-member-list-xml.png)

Aby uzyskać informacje na temat kojarzenia schematów z dokumentami XML, zobacz [Walidacja dokumentu XML](../xml-tools/xml-document-validation.md).

Gdy wpiszesz miejsce z wewnątrz tagu początkowego, uzyskasz także listę rozwijaną zawierającą wszystkie atrybuty, które można dodać do bieżącego elementu.

Podczas wpisywania `"="` wartości atrybutu lub cudzysłowu otwierającego dla wartości można również uzyskać listę możliwych wartości dla tego atrybutu. Wartości są dostępne tylko wtedy, gdy schemat zawiera wartości wyliczane za pośrednictwem `xsd:enumeration` aspektów lub jeśli atrybut jest `Boolean` typem. Dostępna jest również lista funkcji IntelliSense znanych kodów języka dla `xml:lang` lub wszelkich `simpleType` , które pochodzą z programu `xsd:language` . Lista funkcji IntelliSense o znanych `targetNamespace` wartościach jest dostarczana dla deklaracji przestrzeni nazw.

Lista funkcji IntelliSense możliwych wartości jest również podana podczas wpisywania, `">"` Aby zamknąć tag początkowy, jeśli element jest `simpleType` . Zachowanie dla elementów jest podobne do zachowania dla atrybutów opisanych w poprzednim akapicie.

Etykietki narzędzi są również wyświetlane na tych listach IntelliSense na podstawie informacji znajdujących `xsd:annotation` `xsd:documentation` się w skojarzonym schemacie.

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

Edytor XML wypełnia tag końcowy i umieszcza kursor po tagu początkowym. Poniżej znajduje się przykład ("&#124;" — uwagi dotyczące położenia kursora):

`<book>`&#124;`</book>`

Ponieważ wartości atrybutów muszą zawsze mieć cudzysłowy, Edytor XML wypełnia cudzysłowy. Na przykład, jeśli wpiszesz następujące polecenie:

`<book title=`

Edytor XML dodaje cudzysłowy i położenie kursora między cudzysłowami:

`<book title="`&#124;`"`

Podobnie Edytor XML automatycznie wstawia również następującą składnię XML:

- Zakończ instrukcję przetwarzania:  `?>`

- Zakończ blok CDATA: `]]>`

- Zakończ komentarz: `-->`

- Zakończenie deklaracji DTD: `>`

Edytor XML ma także możliwość wstawiania deklaracji przestrzeni nazw w przypadku wybrania z listy funkcji IntelliSense elementu lub atrybutu z przestrzeni nazw, a przestrzeń nazw dla tego elementu lub atrybutu nie należy jeszcze do zakresu.

Na przykład, jeśli wybierzesz `e:Book` element z listy IntelliSense, gdzie prefiks jest powiązany z `http://books` przestrzenią nazw, która nie została zadeklarowana w dokumencie, Edytor XML wstawia wymaganą deklarację przestrzeni nazw. Poniżej znajduje się otrzymany tekst XML:

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Dopasowywanie nawiasów klamrowych

Edytor XML zawiera wyróżnione nawiasy klamrowe w celu uzyskania natychmiastowej opinii na temat elementów, które właśnie zostały zamknięte. Możesz również użyć skrótu klawiaturowego (**Ctrl** + **]**), aby przeskoczyć z jednego nawiasu klamrowego do pasującego nawiasu klamrowego.

Edytor XML wykonuje tę czynności dla następujących elementów:

- Dopasowanie tagów początkowych i końcowych.

- Dowolna para \<" or "> nawiasów kątowych.

- Początek i koniec komentarzy.

- Początek i koniec instrukcji przetwarzania.

- Początek i koniec bloków CDATA.

- Początek i koniec deklaracji DTD.

- Otwieranie i zamykanie cudzysłowu dla atrybutów.

## <a name="modify-the-intellisense-options"></a>Modyfikowanie opcji IntelliSense

Funkcje IntelliSense i automatycznego uzupełniania są domyślnie włączone. Można jednak zmienić to ustawienie, modyfikując **Tools**  >  **Opcje** narzędzi.

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

## <a name="see-also"></a>Zobacz też

- [Edytor XML](../xml-tools/xml-editor.md)
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Przewodnik: Używanie XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)
