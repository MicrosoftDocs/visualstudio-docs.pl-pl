---
title: Widok wykresu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba58777700ba34de3dc3b7a842f26462daf08c89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656359"
---
# <a name="graph-view"></a>Widok wykresu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok wykresu zawiera graficzną reprezentację globalnych węzłów schematu i relacje między węzłami. Należy zauważyć, że widok wykresu nie pozwala na zmianę układu zestawu schematu na powierzchni projektowej. Widok wykresu zawiera również pasek narzędzi projektanta schematu XML i pasek nawigacyjny.

 Na poniższej ilustracji przedstawiono widok wykresu z sześcioma węzłami globalnymi na jego powierzchni projektowej.

 ![Widok wykresu projektanta schematu XML](../xml-tools/media/xsddesigner-graphview.gif "XSDDesigner_GraphView")

## <a name="design-surface"></a>Powierzchnia projektowa
 Na powierzchni projektowej widoku wykresu jest wyświetlana zawartość [obszaru roboczego projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md). Jeśli obszar roboczy zawiera wszystkie węzły globalne z zestawu schematów, węzły są wyświetlane na powierzchni projektowej widoku wykresu, a strzałki są rysowane między węzłami z relacjami.

 Dwukrotne kliknięcie węzła w widoku wykresu spowoduje wyświetlenie edytora XML.

 Aby usunąć wybrane węzły z obszaru roboczego, użyj paska narzędzi projektanta XSD lub klawisza DELETE.

 Jeśli powierzchnia projektowa jest pusta, Edytor XML, Eksplorator schematu XML i znak wodny są wyświetlane. *Znak wodny* jest listą linków do wszystkich widoków projektanta XSD.

 ![Projektant XSD; Widok wykresu](../xml-tools/media/xsdgraphviewwatermark.gif "XSDGraphViewWatermark")

 Jeśli zestaw schematu zawiera błędy, na końcu listy zostanie wyświetlony następujący tekst: "Użyj Lista błędów, aby wyświetlić i naprawić błędy w zestawie".

## <a name="breadcrumb-bar"></a>Pasek nawigacyjny
 Pasek nawigacyjny u dołu widoku wykresu pokazuje, gdzie wybrany węzeł znajduje się w zestawie schematów. W przypadku wybrania wielu elementów pasek nawigacyjny będzie pusty.

## <a name="context-menu"></a>Menu kontekstowe
 W poniższej tabeli opisano opcje, które są dostępne dla wszystkich węzłów na powierzchni projektowej widoku wykresu.

|Opcja|Opis|
|------------|-----------------|
|**Pokaż w Eksploratorze schematu XML**|Umieszcza fokus w Eksploratorze schematu i podświetla węzeł zestawu schematów.|
|**Pokaż w widoku wykresu**|Przełącza do widoku wykresu (wyszarzony).|
|**Generuj przykładowy kod XML**|Dostępne tylko dla elementów globalnych. Generuje przykładowy plik XML dla elementu globalnego.|
|**Wyczyść obszar roboczy**|Czyści obszar roboczy i powierzchnię projektu.|
|**Usuń z obszaru roboczego**|Usuwa wybrane węzły z obszaru roboczego i powierzchni projektowej.|
|**Usuń wszystko oprócz zaznaczenia z obszaru roboczego**|Usuwa węzły, które nie są wybrane z obszaru roboczego i powierzchni projektowej.|
|**Eksportuj diagram jako obraz...**|Zapisuje powierzchnię projektu do pliku XPS.|
|**Zaznacz wszystko**|Wybiera wszystkie węzły na powierzchni projektowej.|
|**Wyświetl kod**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element wybrany w Eksploratorze schematu XML również zostanie wybrany w edytorze XML.|
|**Okno właściwości**|Otwiera okno **Właściwości** (jeśli nie jest jeszcze otwarte). To okno wyświetla informacje o węźle.|

 Oprócz typowych opcji opisanych powyżej, menu kontekstowe dla elementów globalnych ma również następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Dodaj definicję typu**|Dodaje typ podstawowy do diagramu.|
|**Dodaj wszystkie odwołania**|Dodaje wszystkie węzły odwołujące się do elementu i rysuje strzałki, aby wskazać relacje między nimi.|
|**Dodaj składowe grupy podstawienia**|Dodaje wszystkie elementy członkowskie grupy podstawienia. Ta opcja jest wyświetlana w widoku, jeśli element jest elementem nagłówkowym lub członkiem grupy podstawienia.|
|**Generuj przykładowy kod XML**|Generuje przykładowy plik XML dla elementu globalnego.|

 Oprócz typowych opcji opisanych powyżej, menu kontekstowe globalnego prostego i globalnego typu złożonego ma również następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Dodaj typ podstawowy**|Jeśli wybrany typ jest pochodną typu globalnego, program dodaje typ podstawowy wybranego typu.|
|**Dodaj wszystkie odwołania**|Dodaje wszystkie odwołania wybranego typu. Obejmuje to elementy i atrybuty wybranego typu oraz typy pochodne od wybranego typu.|
|**Dodaj wszystkie typy pochodne**|Dodaje wszystkie typy, które są bezpośrednio i pośrednio wyprowadzane z wybranego typu.|
|**Dodaj wszystkie elementy nadrzędne**|Dodaje wszystkie typy nadrzędne (podstawowe).|

 Oprócz typowych opcji opisanych powyżej, menu kontekstowe grup globalnych i grup atrybutów ma również następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Dodaj wszystkie odwołania**|Dodaje wszystkie węzły, które odwołują się do grupy, i rysuje strzałki, aby wskazać relacje między nimi.|
|**Dodaj wszystkie elementy członkowskie**|Dodaje wszystkie elementy członkowskie grupy i rysuje strzałki, aby wskazać relacje między nimi.|

 W funkcji do typowych opcji opisanych powyżej, menu kontekstowe dla atrybutów globalnych ma również następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Dodaj wszystkie odwołania**|Dodaje wszystkie węzły, które odwołują się do grupy, i rysuje strzałki, aby wskazać relacje między nimi.|

## <a name="properties-window"></a>Okno Właściwości
 Użyj menu kontekstowego, aby wstępnie otworzyć okno **Właściwości** . Domyślnie okno **Właściwości** jest wyświetlane w prawym dolnym rogu programu Visual Studio. Po kliknięciu węzła, który jest renderowany w widoku modelu zawartości, właściwości tego węzła będą wyświetlane w oknie **Właściwości** .

## <a name="xsd-toolbar"></a>XSD — pasek narzędzi
 Następujące przyciski paska narzędzi XSD są włączone, gdy widok wykresu jest aktywny.

 ![Pasek narzędzi projektanta schematu XML](../xml-tools/media/xsdgraphviewtoolbar.gif "XSDGraphViewToolbar")

|Opcja|Opis|
|------------|-----------------|
|**Pokaż widok startowy**|Przełącza do [widoku Start](../xml-tools/start-view.md). Dostęp do tego widoku można uzyskać za pomocą skrótu klawiaturowego: **Ctrl + 1**.|
|**Pokaż widok modelu zawartości**|Przełącza do [widoku modelu zawartości](../xml-tools/content-model-view.md). Dostęp do tego widoku można uzyskać za pomocą skrótu klawiaturowego: **Ctrl + 2**.|
|**Pokaż widok wykresu**|Przełącza do [widoku wykresu](../xml-tools/graph-view.md). Dostęp do tego widoku można uzyskać za pomocą skrótu klawiaturowego: **Ctrl + 3**.|
|**Wyczyść obszar roboczy**|Czyści obszar roboczy i powierzchnię projektu.|
|**Usuń z obszaru roboczego**|Usuwa wybrane węzły z obszaru roboczego i projektu serface.|
|**Usuń wszystko oprócz zaznaczenia z obszaru roboczego**|Usuwa węzły, które nie są wybrane z obszaru roboczego i projektu serface. Ta opcja jest włączona w widoku modelu zawartości i w widoku wykresu.|
|**Od lewej do prawej**|Zmienia układ w widoku wykresu na hierarchiczną reprezentację węzłów od lewej do prawej. Dostęp do tej opcji można uzyskać za pomocą skrótu klawiaturowego: **Alt + Strzałka w prawo**.|
|**Od prawej do lewej**|Zmienia układ w widoku wykresu na hierarchiczną reprezentację węzłów w kierunku od prawej do lewej. Dostęp do tej opcji można uzyskać za pomocą skrótu klawiaturowego: **Alt + Strzałka w lewo**.|
|**Od góry do dołu**|Zmienia układ w widoku wykresu na górną, hierarchiczną reprezentację węzłów. Dostęp do tej opcji można uzyskać za pomocą skrótu klawiaturowego: **Alt + Strzałka w dół**.|
|**Od dołu do góry**|Zmienia układ w widoku wykresu na hierarchiczną reprezentację węzłów w dół do góry. Dostęp do tej opcji można uzyskać za pomocą skrótu klawiaturowego: **Alt + Strzałka w górę**.|

## <a name="panscroll"></a>Przesuń/Przewiń
 Powierzchnię projektu można przesuwać przy użyciu pasków przewijania lub przez przytrzymanie klawisza CTRL podczas klikania i przeciągania myszy. Po przeniesieniu powierzchni projektowej przy użyciu funkcji kliknij i przeciągnij kursor zmieni się na cztery przecinające się strzałki, wskazując cztery kierunki.

## <a name="undoredo"></a>Cofnij/ponów
 Funkcja Cofnij/ponów jest włączona w widoku wykresu dla następujących akcji:

- Dodawanie jednego węzła przez przeciąganie i upuszczanie.

- Dodawanie wielu węzłów z okna wyników wyszukiwania w Eksploratorze schematu lub w kwerendach widoku startowego.

- Usuwanie jednego lub wielu węzłów.

## <a name="zoom"></a>Powiększenie
 Powiększenie jest dostępne w prawym dolnym rogu widoku wykresu.

 Powiększenie można kontrolować w następujący sposób:

- Trzymając wciśnięty klawisz CTRL i obracając kółkiem myszy, gdy wskaźnik myszy znajduje się nad powierzchnią widoku wykresu.

- Za pomocą kontrolki suwak. Suwak pokazuje bieżący poziom powiększenia.

  Suwak powiększenia jest nieprzezroczysty po zaznaczeniu, umieszczeniu na nim wskaźnika myszy lub użyj klawisza CTRL, aby powiększyć; we wszystkich innych przypadkach jest to niewidoczne.

## <a name="xml-editor-integration"></a>Integracja edytora XML
 Można przełączać się między widokiem wykresu i edytorem XML, klikając węzeł i korzystając z menu kontekstowego widoku.

 W przypadku wprowadzenia zmian w zestawie schematu w edytorze XML zmiany zostaną zsynchronizowane w widoku wykresu. Aby uzyskać więcej informacji, zobacz [integracja z edytorem XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Zobacz też
 [Powierzchnia projektowa](../xml-tools/xml-schema-designer-workspace.md)
