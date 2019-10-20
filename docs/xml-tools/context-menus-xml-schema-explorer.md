---
title: Menu kontekstowe w Eksploratorze schematu XML
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9310102177e19d2129dd620285d6c45df63ec78
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651202"
---
# <a name="context-menus-xml-schema-explorer"></a>Menu kontekstowe (Eksplorator schematu XML)

Menu kontekstowe jest menu wyświetlanym po kliknięciu prawym przyciskiem myszy elementu. Poniższe elementy menu kontekstowego są używane do wykonywania wyszukiwania specyficznego dla schematu i innych operacji.

## <a name="node-type-schema-set"></a>Typ węzła: zestaw schematów

W poniższej tabeli opisano opcje, które są dostępne dla węzła zestawu schematów.

|Opcja|Opis|
|-|-----------------|
|**Pokaż najprawdopodobniej elementy główne**|Znajduje i wyróżnia wszystkie elementy globalne, do których nie odwołują się elementy globalne inne niż same.|
|**Pokaż typy globalne**|Znajduje i wyróżnia wszystkie typy globalne w zestawie schematów.|
|**Pokaż elementy globalne**|Znajduje i wyróżnia wszystkie elementy globalne w zestawie schematów.|
|**Okno właściwości**|Otwiera okno **Właściwości** (jeśli nie jest jeszcze otwarte). To okno wyświetla informacje o węźle.|

## <a name="node-type-namespace"></a>Typ węzła: przestrzeń nazw
W poniższej tabeli opisano opcje, które są dostępne dla węzła przestrzeni nazw.

|Opcja|Opis|
|-|-----------------|
|**Pokaż wszystkie odwołania przychodzące**|Znajduje i podświetla pliki, które zaimportują wybraną przestrzeń nazw.|
|**Pokaż wszystkie odwołania wychodzące**|Dla każdego pliku w wybranej przestrzeni nazw znajduje i wyróżnia następujące elementy:<br /><br /> — Wszystkie przestrzenie nazw, do których odwołują się instrukcje importu bez atrybutu `schemaLocation`.<br />— Wszystkie pliki w przestrzeniach nazw innych niż wybrane w atrybucie `schemaLocation` w instrukcjach import i include.|
|**Pokaż typy globalne**|Znajduje i wyróżnia wszystkie typy globalne w wybranej przestrzeni nazw.|
|**Pokaż elementy globalne**|Znajduje i wyróżnia wszystkie elementy globalne w wybranej przestrzeni nazw.|
|**Okno właściwości**|Otwiera okno **Właściwości** (jeśli nie jest jeszcze otwarte). To okno wyświetla informacje o węźle.|

## <a name="node-type-file"></a>Typ węzła: plik
W poniższej tabeli opisano opcje, które są dostępne dla węzła plik.

|Opcja|Opis|
|-|-----------------|
|**Pokaż wszystkie odwołania przychodzące**|Znajduje i podświetla wszystkie pliki, które określają wybrany plik w `schemaLocation` atrybuty instrukcji INCLUDE i import.|
|**Pokaż wszystkie odwołania wychodzące**|Znajduje i wyróżnia następujące elementy:<br /><br /> — Wszystkie przestrzenie nazw określone w atrybutach przestrzeni nazw wszystkich instrukcji importu, które nie mają atrybutu `schemaLocation`.<br />-Wszystkie pliki określone w `schemaLocation` atrybuty wszystkich instrukcji import i include.|
|**Pokaż typy globalne**|Znajduje i wyróżnia wszystkie typy globalne w tym pliku.|
|**Pokaż elementy globalne**|Znajduje i wyróżnia wszystkie elementy globalne w tym pliku.|
|**Wyświetl kod**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element wybrany w Eksploratorze schematu XML również zostanie wybrany w edytorze XML.|
|**Okno właściwości**|Otwiera okno **Właściwości** (jeśli nie jest jeszcze otwarte). To okno wyświetla informacje o węźle.|

## <a name="all-global-node-types"></a>Wszystkie typy węzłów globalnych
W poniższej tabeli opisano opcje, które są dostępne dla wszystkich węzłów globalnych.

|Opcja|Opis|
|-|-----------------|
|**Pokaż w widoku wykresu**|Otwiera widok wykresu. Jeśli wybrany węzeł nie znajduje się w obszarze roboczym, program doda go do obszaru roboczego i wybierze węzeł.|
|**Pokaż w widoku modelu zawartości**|Otwiera widok modelu zawartości. Jeśli wybrany węzeł nie znajduje się w obszarze roboczym, program doda go do obszaru roboczego i wybierze węzeł.|
|**Wyświetl kod**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element wybrany w Eksploratorze schematu XML również zostanie wybrany w edytorze XML.|
|**Okno właściwości**|Otwiera okno **Właściwości** (jeśli nie jest jeszcze otwarte). To okno wyświetla informacje o węźle.|

## <a name="node-type-element"></a>Typ węzła: element
Oprócz opcji węzła globalnego opisanych powyżej, menu kontekstowe dla węzłów elementu ma następujące opcje:

|Opcja|Opis|
|-|-----------------|
|**Przejdź do definicji typu**|Przechodzi do definicji typu wybranego elementu. Ma to zastosowanie, gdy typ, który jest używany dla elementu jest typem globalnym.|
|**Przejdź do oryginalnego elementu**|W przypadku odwołań do elementów przejdź do rzeczywistej definicji elementu.|
|**Pokaż wszystkie odwołania**|Dla elementów globalnych Znajdź i podświetla wszystkie odwołania (elementy, które mają `ref="selectedElement"`) do wybranego elementu.|
|**Pokaż elementy członkowskie grupy podstawienia**|W przypadku głowic grupy podstawienia Znajdź i podświetla Wszystkie elementy, które są członkami grupy podstawienia, której wybrany element jest członkiem. Spowoduje to wyświetlenie bezpośrednich i pośrednich uczestników.|
|**Pokaż nagłówki podstawiania**|Dla elementów globalnych, które są elementami członkowskimi grupy podstawienia, znajduje i wyróżnia wszystkie głowice bezpośrednie i pośrednie dla wybranego elementu, takie jak:<br /><br /> -Nagłówek grupy podstawienia określony w wybranym elemencie.<br />-Nagłówek grupy podstawienia określony w jego elemencie nagłówkowym.|
|**Generuj przykładowy kod XML**|Dostępne tylko dla elementów globalnych. Generuje przykładowy plik XML dla elementu globalnego.|

## <a name="node-type-global-types"></a>Typ węzła: typy globalne
Oprócz opcji węzła globalnego opisanych powyżej, menu kontekstowe dla węzłów typu globalnego ma następujące opcje:

|Opcja|Opis|
|-|-----------------|
|**Pokaż typ podstawowy**|Jeśli wybrany typ jest pochodną typu globalnego, nawiguje do typu podstawowego wybranego typu.|
|**Pokaż wszystkie odwołania**|Znajduje i wyróżnia wszystkie odwołania do wybranego typu. Obejmuje to elementy i atrybuty wybranego typu i typy pochodne od wybranego typu.|
|**Pokaż wszystkie typy pochodne**|Znajduje i wyróżnia wszystkie typy, które są bezpośrednio i pośrednio wyprowadzane z wybranego typu.|
|**Pokaż wszystkie elementy nadrzędne**|Pokaż wszystkie typy nadrzędne (podstawowe).|

## <a name="node-type-attribute"></a>Typ węzła: atrybut
Oprócz opcji węzła globalnego opisanych powyżej, menu kontekstowe dla węzłów atrybutów ma następujące opcje:

|Opcja|Opis|
|-|-----------------|
|**Przejdź do definicji typu**|Gdy typ, który jest używany dla atrybutu jest typem globalnym, nawiguje do definicji typu wybranego atrybutu.|
|**Przejdź do oryginalnego atrybutu**|W przypadku odwołań do atrybutów, przejdź do rzeczywistej definicji atrybutu.|
|**Pokaż wszystkie odwołania**|W przypadku atrybutów globalnych Znajdź i podświetla wszystkie odwołania (inne atrybuty, które mają `ref="selectedAttribute"`) do wybranego atrybutu.|

## <a name="node-type-attribute-group"></a>Typ węzła: Grupa atrybutów
Oprócz opcji węzła globalnego opisanych powyżej, menu kontekstowe dla węzłów grupy atrybutów ma następujące opcje:

|Opcja|Opis|
|-|-----------------|
|**Przejdź do definicji**|W przypadku odwołań przejdź do rzeczywistej definicji atrybutu.|
|**Pokaż wszystkie elementy członkowskie**|Znajduje i wyróżnia wszystkie elementy członkowskie grupy atrybutów.|
|**Pokaż wszystkie odwołania**|Znajduje i wyróżnia wszystkie odwołania (grupy atrybutów, które mają `ref="selectedAttributeGroup"`) do wybranej grupy atrybutów.|

## <a name="node-type-named-group"></a>Typ węzła: nazwana grupa
Oprócz opcji węzła globalnego opisanych powyżej, menu kontekstowe dla nazwanych węzłów grupy ma następujące opcje:

|Opcja|Opis|
|-|-----------------|
|**Przejdź do definicji**|W przypadku odwołań przejdź do rzeczywistej definicji atrybutu.|
|**Pokaż wszystkie elementy członkowskie**|Znajduje i wyróżnia wszystkie elementy członkowskie nazwanej grupy.|
|**Pokaż wszystkie odwołania**|Znajduje i wyróżnia wszystkie odwołania (grupy, które mają `ref="selectedGroup"`) do wybranej grupy.|

## <a name="see-also"></a>Zobacz także

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)
- [Wyszukiwanie zestawu schematów](../xml-tools/searching-the-schema-set.md)