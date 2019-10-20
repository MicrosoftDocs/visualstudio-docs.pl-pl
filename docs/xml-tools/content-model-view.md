---
title: Widok modelu zawartości projektanta schematu XML
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67453571963ae22910842be0021e008632942de5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661526"
---
# <a name="content-model-view"></a>Widok modelu zawartości

Widok model zawartości zawiera graficzną reprezentację lokalnych i globalnych węzłów schematu oraz ich składników, w tym prostych i złożonych typów, elementów, grup modeli, atrybutów i grup atrybutów. Nie można wyświetlić komentarzy i instrukcji przetwarzania XML w widoku modelu zawartości. Widok modelu zawartości zawiera dwa panele: Panel **obszaru roboczego** zawierający listę węzłów w [obszarze roboczym Projektant schematu XML](../xml-tools/xml-schema-designer-workspace.md)oraz powierzchnię projektu, w której można zobaczyć model zawartości węzłów schematu, które są wybrane w **obszarze roboczym** panel. Widok modelu zawartości obejmuje również pasek narzędzi projektanta schematu XML i pasek nawigacyjny.

Na poniższej ilustracji panel **obszary robocze** zawiera sześć węzłów schematu. Węzeł `purchaseOrder` jest wybierany w panelu **obszaru roboczego** i wyświetlany na powierzchni projektowej.

![Widok modelu zawartości projektanta schematu XML](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Panel obszary robocze

Po dodaniu węzłów do obszaru roboczego lista węzłów zostanie wyświetlona w panelu **obszaru roboczego** widoku modelu zawartości. Po wybraniu węzłów w panelu **obszaru roboczego** są one wyświetlane na powierzchni projektowej widok modelu zawartości. Aby usunąć węzły z obszaru roboczego, użyj paska narzędzi projektanta XSD, menu podręcznego kliknij prawym przyciskiem myszy lub klawisza **delete** .

Aby uzyskać informacje na temat dodawania węzłów, zobacz sekcję "Dodawanie węzłów do obszaru roboczego" w [obszarze roboczym Projektant schematu XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Powierzchnia projektowa

Po wybraniu węzła w panelu **obszaru roboczego** jest on dodawany do powierzchni projektowej widok modelu zawartości, w której można wyświetlić szczegóły węzła.

Model zawartości węzła jest reprezentowany przez rozszerzalne drzewo graficzne z elementami i atrybutami wyświetlanymi jako węzły drzewa. Domyślnie tylko jeden poziom jest rozwinięty. Inne informacje, takie jak kompozytory, nazwy typów, grupy i inne kontenery, są umieszczane na pionowym pasku (po rozwinięciu) wraz z elementami i atrybutami, które są otaczające. Dwukrotne kliknięcie paska pionowego zmieni się w poziomy i drzewo zwinięte. Dwukrotne kliknięcie poziomego paska zmieni się w pionie, a drzewo rozwinięte. Wybranie pionowego paska powoduje zaznaczenie wszystkich węzłów w kontenerze. Elementy rozszerzające pojawiają się po prawej stronie węzła, jeśli element może być rozwinięty lub zwinięty.

Jeśli powierzchnia projektowa jest pusta, Edytor XML, **Eksplorator schematu XML**i znak wodny są wyświetlane. *Znak wodny* jest listą linków do wszystkich widoków projektanta XSD. Jeśli zestaw schematu zawiera błędy, na końcu listy zostanie wyświetlony następujący tekst: "Użyj Lista błędów, aby wyświetlić i naprawić błędy w zestawie".

## <a name="breadcrumb-bar"></a>Pasek nawigacyjny

Pasek nawigacyjny w dolnej części widoku model zawartości pokazuje, gdzie wybrany węzeł znajduje się w zestawie schematów.

## <a name="context-menus"></a>Menu kontekstowe

Po kliknięciu prawym przyciskiem myszy elementu na powierzchni projektowej lub panelu **obszaru roboczego** pojawi się menu kontekstowe. W poniższej tabeli opisano opcje dostępne dla powierzchni projektowej widok modelu zawartości.

|Opcja|Opis|
|-|-----------------|
|**Pokaż w Eksploratorze schematu XML**|Umieszcza fokus w Eksploratorze schematu i podświetla węzeł zestawu schematów.|
|**Pokaż w widoku wykresu**|Przełącza do widoku wykresu.|
|**Generuj przykładowy kod XML**|Dostępne tylko dla elementów globalnych. Generuje przykładowy plik XML dla elementu globalnego.|
|**Pokaż dokumentację**|Pokazuje lub ukrywa zawartość węzła adnotacji/dokumentacji.|
|**Eksportuj diagram jako obraz**|Zapisuje powierzchnię projektu do pliku XPS.|
|**Wyświetl kod**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element wybrany w **Eksploratorze schematu XML** jest również wybierany w edytorze XML.|
|**Okno właściwości**|Otwiera okno **Właściwości** (jeśli nie jest jeszcze otwarte). To okno wyświetla informacje o węźle.|

W poniższej tabeli opisano opcje dostępne dla panelu **obszaru roboczego** .

|Opcja|Opis|
|-|-----------------|
|**Pokaż w Eksploratorze schematu XML**|Umieszcza fokus w Eksploratorze schematu i podświetla węzeł zestawu schematów.|
|**Pokaż w widoku wykresu**|Przełącza do widoku wykresu.|
|**Wyczyść obszar roboczy**|Czyści obszar roboczy i powierzchnię projektu.|
|**Usuń z obszaru roboczego**|Usuwa wybrane węzły z obszaru roboczego i powierzchni projektowej.|
|**Usuń wszystko oprócz zaznaczenia z obszaru roboczego**|Usuwa węzły, które nie są wybrane z obszaru roboczego i powierzchni projektowej.|
|**Generuj przykładowy kod XML**|Dostępne tylko dla elementów globalnych. Generuje przykładowy plik XML dla elementu globalnego.|
|**Zaznacz wszystko**|Wybiera wszystkie węzły w panelu **obszaru roboczego** .|
|**Wyświetl kod**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element wybrany w **Eksploratorze schematu XML** jest również wybierany w edytorze XML.|
|**Okno właściwości**|Otwiera okno **Właściwości** (jeśli nie jest jeszcze otwarte). To okno wyświetla informacje o węźle.|

## <a name="properties-window"></a>Okno właściwości

Użyj menu kontekstowego kliknij prawym przyciskiem myszy, aby otworzyć okno **Właściwości** . Domyślnie okno **Właściwości** jest wyświetlane w prawym dolnym rogu programu Visual Studio. Po kliknięciu węzła, który jest renderowany w widoku modelu zawartości, właściwości tego węzła są wyświetlane w oknie **Właściwości** .

## <a name="xsd-designer-toolbar"></a>Pasek narzędzi projektanta XSD

Poniższe przyciski paska narzędzi projektanta XSD są włączone, gdy aktywny jest widok modelu zawartości.

![Pasek narzędzi projektanta schematu XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Opcja|Opis|
|-|-----------------|
|**Pokaż widok startowy**|Przełącza do [widoku Start](../xml-tools/start-view.md). Dostęp do tego widoku można uzyskać za pomocą skrótu klawiaturowego: **Ctrl** +**1**.|
|**Pokaż widok modelu zawartości**|Przełącza do [widoku modelu zawartości](../xml-tools/content-model-view.md). Dostęp do tego widoku można uzyskać za pomocą skrótu klawiaturowego: **Ctrl** +**2**.|
|**Pokaż widok wykresu**|Przełącza do [widoku wykresu](../xml-tools/graph-view.md). Dostęp do tego widoku można uzyskać za pomocą skrótu klawiaturowego: **Ctrl** +**3**.|
|**Wyczyść obszar roboczy**|Czyści obszar roboczy i powierzchnię projektu.|
|**Usuń z obszaru roboczego**|Usuwa wybrane węzły z obszaru roboczego i powierzchni projektowej.|
|**Usuń wszystko oprócz zaznaczenia z obszaru roboczego**|Usuwa węzły, które nie są wybrane z obszaru roboczego i powierzchni projektowej.|
|**Pokaż dokumentację**|Pokazuje lub ukrywa zawartość węzła adnotacji/dokumentacji.|

## <a name="panscroll"></a>Przesuń/Przewiń

Powierzchnię projektu można przesuwać przy użyciu pasków przewijania lub przez przytrzymanie klawisza **Ctrl** podczas klikania i przeciągania myszy. Gdy przesuwasz powierzchnię projektu przy użyciu przycisku kliknij i przeciągnij, kursor zmieni się na cztery przecinające się strzałki, wskazując cztery kierunki.

## <a name="undoredo"></a>Cofnij/ponów

Funkcja Cofnij/ponów jest włączona w widoku modelu zawartości dla następujących akcji:

- Dodawanie jednego węzła przez przeciąganie i upuszczanie.

- Dodawanie wielu węzłów z okna wyników wyszukiwania w Eksploratorze schematu.

- Dodawanie węzłów z widoku startowego.

- Usuwanie jednego lub wielu węzłów.

## <a name="zoom"></a>Powiększenie

Powiększenie jest dostępne w prawym dolnym rogu widoku modelu zawartości.

Powiększenie można kontrolować w następujący sposób:

- Trzymając **wciśnięty klawisz Ctrl** i obracając kółkiem myszy, gdy wskaźnik myszy znajduje się nad powierzchnią widoku modelu zawartości.

- Za pomocą kontrolki suwak. Suwak pokazuje bieżący poziom powiększenia.

Suwak powiększenia jest nieprzezroczysty po zaznaczeniu, umieszczeniu na nim wskaźnika myszy lub Użyj **klawisza Ctrl** , aby powiększyć; we wszystkich innych przypadkach jest to niewidoczne.

## <a name="xml-editor-integration"></a>Integracja edytora XML

Można przełączać się między **projektantem XSD** a edytorem XML za pomocą menu kontekstowego kliknięcia prawym przyciskiem myszy.

W przypadku wprowadzenia zmian w zestawie schematu w edytorze XML zmiany są synchronizowane w widoku modelu zawartości. Aby uzyskać więcej informacji, zobacz [integracja z edytorem XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Zobacz także

- [Obszar roboczy projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md)