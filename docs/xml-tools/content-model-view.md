---
title: Widok modelu zawartości projektanta schematu XML
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5f275683309d630f147940e97f924496af79179
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838591"
---
# <a name="content-model-view"></a>Widok modelu zawartości

Widok modelu zawartości zapewnia graficzną reprezentację węzłów schematu lokalne i globalne oraz ich składników, w tym proste i złożone typy, elementy, grupy modeli, atrybuty i grupy atrybutów. Komentarze XML i instrukcje przetwarzania nie można wyświetlić w widoku modelu zawartości. Widok modelu zawartości zawiera dwa panele: **obszaru roboczego** panel, który zawiera listę węzłów w [obszar roboczy Projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md)i powierzchni projektowej tam, gdzie zobaczysz model zawartości schematu węzły, które są wybrane w **obszaru roboczego** panelu. Widok modelu zawartości zawiera również pasek narzędzi Projektanta schematu XML i na pasku nawigacji.

Na poniższej ilustracji **obszaru roboczego** panel zawiera sześć węzłów schematu. `purchaseOrder` Wybrano węzeł **obszaru roboczego** panelu, a następnie są wyświetlane na powierzchni projektowej.

![Widok modelu zawartości projektanta schematu XML](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Panelu obszaru roboczego

Po dodaniu węzłów do obszaru roboczego listy węzłów pojawi się w **obszaru roboczego** panel widoku modelu zawartości. Po wybraniu węzłów w **obszaru roboczego** panelu pojawiają się na powierzchni projektowej widoku modelu zawartości. Aby usunąć węzły z obszaru roboczego, należy użyć narzędzi Projektant XSD **obszaru roboczego** panelu kliknij prawym przyciskiem myszy menu lub **Usuń** klucza.

Aby uzyskać informacje dotyczące dodawania węzłów, zobacz sekcję "Dodawanie węzłów do obszaru roboczego, w [obszar roboczy Projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Powierzchni projektowej

Po wybraniu węzła w **obszaru roboczego** panelu, dodać go do powierzchni projektowej widoku modelu zawartości, której można wyświetlić szczegóły węzła.

Model zawartości węzła jest reprezentowany przez drzewo graficzny rozwijane z elementów i atrybutów, które pojawiają się jako węzły drzewa. Domyślnie tylko jeden poziom jest rozwinięty. Inne informacje, takie jak kompozytory, nazwy typów, grup i innych kontenerów są umieszczane w pionowy pasek (po rozwinięciu) elementy i atrybuty, które one ująć. Po dwukrotnym kliknięciu pionowy pasek staje się poziome i zwija drzewa. Po dwukrotnym kliknięciu poziomy pasek pionowy staje się i drzewo jest rozwijane. Wybieranie pionowy pasek wybiera wszystkich węzłów w kontenerze. Ekspanderów znajdujących są wyświetlane po prawej stronie węzła, gdy element może być rozwijane czy zwijane.

Jeśli pole pozostanie puste, powierzchni projektowej edytora XML **Eksploratora schematu XML**, i znak wodny nie są wyświetlane. *Znaku wodnego* znajduje się lista łączy do wszystkich widoków Projektant XSD. Jeśli zestaw schemat zawiera błędy, następujący tekst jest wyświetlany na końcu listy: "Użyj listy błędów możesz wyświetlać i naprawiać błędy w zestawie".

## <a name="breadcrumb-bar"></a>Pasek nawigacji

W dolnej części widoku modelu zawartości za pomocą paska nawigacji pokazuje, gdzie wybrany węzeł znajduje się w zestawie schematów.

## <a name="context-menus"></a>Menu kontekstowe

Po kliknięciu prawym przyciskiem myszy element na powierzchni projektowej lub **obszaru roboczego** panelu, zostanie wyświetlone menu kontekstowe. W poniższej tabeli opisano opcje, które są dostępne dla powierzchni projektowej widoku modelu zawartości.

|Opcja|Opis|
|-|-----------------|
|**Pokaż w Eksplorator schematu XML**|Przełącza fokus na Eksploratora schematu i wyróżnienie węzeł zestawu schematu.|
|**Pokaż w widoku wykresu**|Przełącza do widoku wykresu.|
|**Generowanie przykładowy kod XML**|Dostępne tylko dla elementów globalnej. Generuje przykładowy plik XML dla elementu globalnego.|
|**Pokaż dokumentacji**|Pokazuje lub ukrywa zawartość węzła adnotacji/dokumentację.|
|**Eksportuj Diagram jako obraz**|Zapisuje plik XPS powierzchni projektowej.|
|**Wyświetl kod**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element, który wybrano w **Eksploratora schematu XML** zostanie również wybrane w edytorze XML.|
|**Okno właściwości**|Otwiera **właściwości** okna (o ile nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|

W poniższej tabeli opisano opcje, które są dostępne dla **obszaru roboczego** panelu.

|Opcja|Opis|
|-|-----------------|
|**Pokaż w Eksplorator schematu XML**|Przełącza fokus na Eksploratora schematu i wyróżnienie węzeł zestawu schematu.|
|**Pokaż w widoku wykresu**|Przełącza do widoku wykresu.|
|**Usuń obszar roboczy**|Usuwa obszar roboczy i powierzchni projektowej.|
|**Usuń z obszaru roboczego**|Usuwa wybrane węzły z obszaru roboczego i powierzchni projektowej.|
|**Usuń wszystkie oprócz zaznaczenia z obszaru roboczego**|Usuwa węzły, które nie są wybrane z obszaru roboczego i powierzchni projektowej.|
|**Generowanie przykładowy kod XML**|Dostępne tylko dla elementów globalnej. Generuje przykładowy plik XML dla elementu globalnego.|
|**Zaznacz wszystko**|Wybiera wszystkich węzłów w **obszaru roboczego** panelu.|
|**Wyświetl kod**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element, który wybrano w **Eksploratora schematu XML** zostanie również wybrane w edytorze XML.|
|**Okno właściwości**|Otwiera **właściwości** okna (o ile nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|

## <a name="properties-window"></a>Okno właściwości

Użyj menu kliknij prawym przyciskiem myszy (kontekstu), aby otworzyć początkowo **właściwości** okna. Domyślnie **właściwości** okno pojawia się w prawym dolnym rogu programu Visual Studio. Po kliknięciu węzła, który jest renderowany w widoku modelu zawartości, właściwości tym węźle są wyświetlane w **właściwości** okna.

## <a name="xsd-designer-toolbar"></a>Pasek narzędzi Projektanta XSD

Następujące przyciski narzędzi Projektanta XSD są włączone, gdy widok modelu zawartości jest aktywny.

![Pasek narzędzi Projektanta schematu XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Opcja|Opis|
|-|-----------------|
|**Pokaż widok startowy**|Przełącza do [widok startowy](../xml-tools/start-view.md). Ten widok jest możliwy za pomocą skrótów klawiaturowych: **Ctrl**+**1**.|
|**Pokaż widok modelu zawartości**|Przełącza do [widoku modelu zawartości](../xml-tools/content-model-view.md). Ten widok jest możliwy za pomocą skrótów klawiaturowych: **Ctrl**+**2**.|
|**Pokaż widok wykresu**|Przełącza do [widoku wykresu](../xml-tools/graph-view.md). Ten widok jest możliwy za pomocą skrótów klawiaturowych: **Ctrl**+**3**.|
|**Usuń obszar roboczy**|Usuwa obszar roboczy i powierzchni projektowej.|
|**Usuń z obszaru roboczego**|Usuwa wybrane węzły z obszaru roboczego i powierzchni projektowej.|
|**Usuń wszystkie oprócz zaznaczenia z obszaru roboczego**|Usuwa węzły, które nie są wybrane z obszaru roboczego i powierzchni projektowej.|
|**Pokaż dokumentacji**|Pokazuje lub ukrywa zawartość węzła adnotacji/dokumentację.|

## <a name="panscroll"></a>Pan/przewijania

Można Przesuń powierzchni projektowej, za pomocą pasków przewijania lub przytrzymanie **Ctrl** klucza podczas kliknij i przeciągnij myszą. Kiedy przesuwa powierzchni projektowej kliknij i przeciągnij przybiera cztery strzałki przecinające w czterech kierunkach.

## <a name="undoredo"></a>Cofnij/Ponów.

Możliwość Cofnij/Ponów jest włączona w widoku modelu zawartości następujące akcje:

- Dodanie jednego węzła przez przeciąganie i upuszczanie.

- Dodawanie wielu węzłów z okna wyniki wyszukiwania w Eksploratorze schematu.

- Dodawanie węzłów z widoku startowego.

- Usunięcie jednego lub wielu węzłów.

## <a name="zoom"></a>Powiększenie

Powiększenie jest dostępna w prawym dolnym rogu widoku modelu zawartości.

Powiększenie mogą być kontrolowane w następujący sposób:

- Poprzez posiadanie **Ctrl** klucza i wirowania myszy kółka, gdy wskaźnik myszy znajduje się na powierzchni widoku modelu zawartości.

- Za pomocą suwaka. Suwak pokazuje bieżący poziom powiększenia.

Suwak powiększenia jest nieprzezroczysta, zaznacz go, umieść kursor nad nim lub użyj **Ctrl** przy użyciu kółka myszy, aby powiększyć; w innym czasie, proces jest przezroczysty.

## <a name="xml-editor-integration"></a>Integracja z edytorem XML

Możesz przełączać się między programami **Projektant XSD** i edytorem XML za pomocą menu kliknij prawym przyciskiem myszy (kontekstu).

Jeśli wprowadzisz zmiany w schemacie ustawiane za pomocą edytora XML zmiany są synchronizowane w widoku modelu zawartości. Aby uzyskać więcej informacji, zobacz [Integracja z edytorem XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Zobacz także

- [Obszar roboczy projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md)