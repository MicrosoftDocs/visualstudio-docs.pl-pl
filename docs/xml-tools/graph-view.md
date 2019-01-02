---
title: Widok wykresu projektanta schematu XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7623198cc31e8ee955f00cd06b7ca91f8d32a31
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826997"
---
# <a name="graph-view"></a>Widok wykresu

Widok wykresu zawiera graficzną reprezentację globalnego schematu węzły i relacje między węzłami. Należy pamiętać, że w widoku wykresu nie zezwala na można zmieniać układ schematu ustawiony na powierzchni projektowej. Widok wykresu zawiera również pasek narzędzi Projektanta schematu XML i na pasku nawigacji.

 Na poniższej ilustracji przedstawiono widok wykresu za pomocą sześciu węzłów globalnego na jego powierzchni projektowej.

 ![Widok wykresu projektanta schematu XML](../xml-tools/media/xsddesigner_graphview.gif)

## <a name="design-surface"></a>Powierzchni projektowej

 Obszar projektu w widoku wykresu wyświetla zawartość [obszar roboczy Projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md). Jeśli obszar roboczy zawiera wszystkie globalne węzły z zestawu schematów, węzły są wyświetlane na powierzchni projektowej widoku wykresu i strzałki są rysowane między węzłami, które mają relacje.

 Dwukrotne kliknięcie węzła w widoku wykresu zostanie wyświetlone się Edytor XML.

 Aby usunąć wybrane węzły z obszaru roboczego, użyj narzędzi Projektanta XSD lub **Usuń** klucza.

 Jeśli pole pozostanie puste, powierzchni projektowej edytora XML **Eksploratora schematu XML**, i znak wodny nie są wyświetlane. *Znaku wodnego* znajduje się lista łączy do wszystkich widoków Projektant XSD.

 ![Projektant XSD; Widok wykresu](../xml-tools/media/xsdgraphviewwatermark.gif)

 Jeśli zestaw schemat zawiera błędy, następujący tekst jest wyświetlany na końcu listy: "Użyj listy błędów możesz wyświetlać i naprawiać błędy w zestawie".

## <a name="breadcrumb-bar"></a>Pasek nawigacji

 W dolnej części widoku wykresu za pomocą paska nawigacji pokazuje, gdzie wybrany węzeł znajduje się w zestawie schematów. Jeśli zaznaczono wiele elementów paska nawigacji jest puste.

## <a name="context-menu"></a>Menu kontekstowe

 W poniższej tabeli opisano opcje, które są dostępne dla wszystkich węzłów na powierzchni projektowej widoku wykresu.

|Opcja|Opis|
|-|-----------------|
|**Pokaż w Eksplorator schematu XML**|Przełącza fokus na Eksploratora schematu i wyróżnienie węzeł zestawu schematu.|
|**Pokaż w widoku wykresu**|Przełącza do widoku wykresu (wyszarzony).|
|**Generowanie przykładowy kod XML**|Dostępne tylko dla elementów globalnej. Generuje przykładowy plik XML dla elementu globalnego.|
|**Usuń obszar roboczy**|Usuwa obszar roboczy i powierzchni projektowej.|
|**Usuń z obszaru roboczego**|Usuwa wybrane węzły z obszaru roboczego i powierzchni projektowej.|
|**Usuń wszystkie oprócz zaznaczenia z obszaru roboczego**|Usuwa węzły, które nie są wybrane z obszaru roboczego i powierzchni projektowej.|
|**Eksportuj Diagram jako obraz**|Zapisuje plik XPS powierzchni projektowej.|
|**Zaznacz wszystko**|Wybiera wszystkich węzłów na powierzchni projektowej.|
|**Wyświetl kod**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element, który wybrano w **Eksploratora schematu XML** zostanie również wybrane w edytorze XML.|
|**Okno właściwości**|Otwiera **właściwości** okna (o ile nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|

 Oprócz typowych opcji opisanych powyżej menu kontekstowe dla elementy globalne ma następujące opcje:

|Opcja|Opis|
|-|-----------------|
|**Dodawanie definicji typu**|Dodaje typ bazowy do diagramu.|
|**Dodaj wszystkie odwołania**|Dodaje wszystkie węzły, które odnoszą się do elementu i rysuje strzałki wskazują relacje między nimi.|
|**Dodaj składowe grupy podstawienia**|Dodaje wszystkich członków grupy podstawienia. Ta opcja jest wyświetlana w widoku, jeśli element jest węzłem głównym lub składową grupy podstawienia.|
|**Generowanie przykładowy kod XML**|Generuje przykładowy plik XML dla elementu globalnego.|

 Oprócz typowych opcji opisanych powyżej menu kontekstowe dla globalne proste i globalne typy złożone ma następujące opcje:

|Opcja|Opis|
|-|-----------------|
|**Dodaj typ podstawowy**|Jeśli wybrany typ pochodzi od typu globalnego, dodaje typ podstawowy elementu wybranego typu.|
|**Dodaj wszystkie odwołania**|Dodaje wszystkie odwołania do wybranego typu. Obejmuje to elementy i atrybuty wybranego typu, a typy pochodzące od wybranego typu.|
|**Dodaj wszystkie typy pochodne**|Dodaje wszystkie typy, które bezpośredniego lub pośredniego pochodzą od wybranego typu.|
|**Dodaj wszystkie elementy nadrzędne**|Dodaje wszystkie typy (podstawowe) nadrzędnego.|

 Oprócz typowych opcji opisanych powyżej menu kontekstowe dla grup globalnych i grup atrybutów ma następujące opcje:

|Opcja|Opis|
|-|-----------------|
|**Dodaj wszystkie odwołania**|Dodaje wszystkie węzły, które odnoszą się do grupy i rysuje strzałki wskazują relacje między nimi.|
|**Dodaj wszystkie elementy członkowskie**|Dodaje wszystkich członków grupy i rysuje strzałki wskazują relacje między nimi.|

 Oprócz typowych opcji opisanych powyżej menu kontekstowe dla atrybutami globalnymi ma następujące opcje:

|Opcja|Opis|
|-|-----------------|
|**Dodaj wszystkie odwołania**|Dodaje wszystkie węzły, które odnoszą się do grupy i rysuje strzałki wskazują relacje między nimi.|

## <a name="properties-window"></a>Okno właściwości

 Użyj menu kontekstowego, aby otworzyć początkowo **właściwości** okna. Domyślnie **właściwości** okno pojawia się w prawym dolnym rogu programu Visual Studio. Po kliknięciu węzła, który jest renderowany w widoku modelu zawartości, będzie można wyświetlić właściwości tego węzła w **właściwości** okna.

## <a name="xsd-toolbar"></a>Pasek narzędzi XSD

 Następujące przyciski paska narzędzi XSD są włączone, gdy widok wykresu jest aktywny.

 ![Pasek narzędzi Projektanta schematu XML](../xml-tools/media/xsdgraphviewtoolbar.gif)

|Opcja|Opis|
|-|-----------------|
|**Pokaż widok startowy**|Przełącza do [widok startowy](../xml-tools/start-view.md). Ten widok jest możliwy za pomocą skrótów klawiaturowych: **CTRL**+**1**.|
|**Pokaż widok modelu zawartości**|Przełącza do [widoku modelu zawartości](../xml-tools/content-model-view.md). Ten widok jest możliwy za pomocą skrótów klawiaturowych: **CTRL**+**2**.|
|**Pokaż widok wykresu**|Przełącza do [widoku wykresu](../xml-tools/graph-view.md). Ten widok jest możliwy za pomocą skrótów klawiaturowych: **CTRL**+**3**.|
|**Usuń obszar roboczy**|Usuwa obszar roboczy i powierzchni projektowej.|
|**Usuń z obszaru roboczego**|Usuwa wybrane węzły z obszaru roboczego i powierzchni projektowej.|
|**Usuń wszystkie oprócz zaznaczenia z obszaru roboczego**|Usuwa węzły, które nie są wybrane z obszaru roboczego i powierzchni projektowej. Ta opcja jest włączona, w widoku modelu zawartości i w widoku wykresu.|
|**Od lewej do prawej**|Zmienia układ w widoku wykresu od lewej do prawej hierarchiczną reprezentację węzłów. Ta opcja jest możliwy za pomocą skrótów klawiaturowych: **ALT**+**strzałkę w prawo**.|
|**Od prawej do lewej**|Zmienia układ w widoku wykresu od prawej do lewej hierarchiczną reprezentację węzłów. Ta opcja jest możliwy za pomocą skrótów klawiaturowych: **ALT**+**Strzałka w lewo**.|
|**Od góry do dołu**|Zmienia układ w widoku wykresu od góry do dołu hierarchiczną reprezentację węzłów. Ta opcja jest możliwy za pomocą skrótów klawiaturowych: **ALT**+**Strzałka w dół**.|
|**Od dołu do góry**|Zmienia układ w widoku wykresu do dołu do góry hierarchiczną reprezentację węzłów. Ta opcja jest możliwy za pomocą skrótów klawiaturowych: **ALT**+**Strzałka w górę**.|

## <a name="panscroll"></a>Pan/przewijania

 Można Przesuń powierzchni projektowej, za pomocą pasków przewijania lub przytrzymanie **Ctrl** klucza podczas kliknij i przeciągnij myszą. Gdy przesuwa powierzchni projektowej kliknij i przeciągnij kursor zmieni się na cztery strzałki przecinające w czterech kierunkach.

## <a name="undoredo"></a>Cofnij/Ponów.

 Możliwość Cofnij/Ponów jest włączona w widoku wykresu następujące akcje:

-   Dodanie jednego węzła przez przeciąganie i upuszczanie.

-   Dodawanie wielu węzłów w oknie wyników wyszukiwania zapytań Eksploratora schematu lub uruchomić widoku.

-   Usunięcie jednego lub wielu węzłów.

## <a name="zoom"></a>Powiększenie

 Powiększenie jest dostępna w prawym dolnym rogu widoku wykresu.

 Powiększenie mogą być kontrolowane w następujący sposób:

-   Poprzez posiadanie **Ctrl** klucza i wirowania myszy kółka, gdy wskaźnik myszy znajduje się na powierzchni widoku wykresu.

-   Za pomocą suwaka. Suwak pokazuje bieżący poziom powiększenia.

Suwak powiększenia jest nieprzezroczysta, zaznacz go, umieść kursor nad nim lub użyj **Ctrl** przy użyciu kółka myszy, aby powiększyć; w innym czasie, proces jest przezroczysty.

## <a name="xml-editor-integration"></a>Integracja z edytorem XML

 Możesz przełączać się i z powrotem między widoku wykresu i edytorem XML, klikając węzeł i przy użyciu menu kontekstowe widoku kodu.

 Jeśli wprowadzisz zmiany w schemacie zestawu w edytorze XML, zmiany zostaną zsynchronizowane w widoku wykresu. Aby uzyskać więcej informacji, zobacz [Integracja z edytorem XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Zobacz także

- [Powierzchni projektowej](../xml-tools/xml-schema-designer-workspace.md)