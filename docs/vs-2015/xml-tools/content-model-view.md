---
title: Widok modelu zawartości | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e3834e22f67001e38096032037f33c5d184a5330
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668902"
---
# <a name="content-model-view"></a>Widok modelu zawartości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok modelu zawartości zapewnia graficzną reprezentację węzłów schematu lokalne i globalne oraz ich składników, w tym proste i złożone typy, elementy, grupy modeli, atrybuty i grupy atrybutów. Komentarze XML i instrukcje przetwarzania nie można wyświetlić w widoku modelu zawartości. Widok modelu zawartości zawiera dwa panele: **obszaru roboczego** panel, który zawiera listę węzłów w [obszar roboczy Projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md)i powierzchni projektowej tam, gdzie zobaczysz model zawartości schematu węzły, które są wybrane w **obszaru roboczego** panelu. Widok modelu zawartości zawiera również pasek narzędzi Projektanta schematu XML i na pasku nawigacji.  
  
 Na poniższej ilustracji panelu obszaru roboczego zawiera sześć węzłów schematu. `purchaseOrder` Węzeł wybrano w panelu obszaru i jest wyświetlany na powierzchni projektowej.  
  
 ![Widok modelu zawartości projektanta schematu XML](../xml-tools/media/xsddesigner-contentmodelview.gif "XSDDesigner_ContentModelView")  
  
## <a name="workspace-panel"></a>Panelu obszaru roboczego  
 Po dodaniu węzłów do obszaru roboczego listy węzłów pojawi się w **obszaru roboczego** panel widoku modelu zawartości. Po wybraniu węzłów w **obszaru roboczego** panelu pojawiają się na powierzchni projektowej widoku modelu zawartości. Aby usunąć węzły z obszar roboczy, użyj narzędzi Projektant XSD **obszaru roboczego** panel menu kontekstowego lub klawisz DELETE.  
  
 Aby uzyskać informacje dotyczące dodawania węzłów, zobacz sekcję "Dodawanie węzłów do obszaru roboczego, w [obszar roboczy Projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md).  
  
## <a name="design-surface"></a>Powierzchni projektowej  
 Wybranie węzła w panelu obszaru roboczego jest dodawany do powierzchni projektowej widoku modelu zawartości, której można wyświetlić szczegóły węzła.  
  
 Model zawartości węzła jest reprezentowany przez drzewo graficzny rozwijane z elementów i atrybutów, które pojawiają się jako węzły drzewa. Domyślnie tylko jeden poziom jest rozwinięty. Inne informacje, takie jak kompozytory, nazwy typów, grup i innych kontenerów są umieszczane w pionowy pasek (po rozwinięciu) elementy i atrybuty, które one ująć. Po dwukrotnym kliknięciu pionowy pasek staje się poziome i zwija drzewa. Po dwukrotnym kliknięciu poziomy pasek pionowy staje się i drzewo jest rozwijane. Wybieranie pionowy pasek zaznaczyć wszystkie węzły w kontenerze. Ekspanderów znajdujących pojawia się po prawej stronie węzła, gdy element może być rozwijane czy zwijane.  
  
 W przypadku pustej powierzchni projektowania edytora XML, Eksplorator schematu XML i znak wodny są wyświetlane. *Znaku wodnego* znajduje się lista łączy do wszystkich widoków Projektant XSD. Jeśli zestaw schemat zawiera błędy, następujący tekst jest wyświetlany na końcu listy: "Użyj listy błędów możesz wyświetlać i naprawiać błędy w zestawie".  
  
## <a name="breadcrumb-bar"></a>Pasek nawigacji  
 W dolnej części widoku modelu zawartości za pomocą paska nawigacji pokazuje, gdzie wybrany węzeł znajduje się w zestawie schematów.  
  
## <a name="context-menus"></a>Menu kontekstowe  
 Po kliknięciu prawym przyciskiem myszy element na powierzchnię projektową lub panelu obszaru roboczego, zostanie wyświetlone menu kontekstowe. W poniższej tabeli opisano opcje, które są dostępne dla powierzchni projektowej widoku modelu zawartości.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Pokaż w Eksplorator schematu XML**|Przełącza fokus na Eksploratora schematu i wyróżnienie węzeł zestawu schematu.|  
|**Pokaż w widoku wykresu**|Przełącza do widoku wykresu.|  
|**Generowanie przykładowy kod XML**|Dostępne tylko dla elementów globalnej. Generuje przykładowy plik XML dla elementu globalnego.|  
|**Pokaż dokumentacji**|Pokazuje lub ukrywa zawartość węzła adnotacji/dokumentację.|  
|**Eksportuj Diagram jako obraz...**|Zapisuje plik XPS powierzchni projektowej.|  
|**Wyświetl kod**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element, który wybrano w Eksplorator schematu XML zostanie również wybrana w edytorze XML.|  
|**Okno właściwości**|Otwiera **właściwości** okna (o ile nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|  
  
 W poniższej tabeli opisano opcje, które są dostępne dla panelu obszaru roboczego.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Pokaż w Eksplorator schematu XML**|Przełącza fokus na Eksploratora schematu i wyróżnienie węzeł zestawu schematu.|  
|**Pokaż w widoku wykresu**|Przełącza do widoku wykresu.|  
|**Usuń obszar roboczy**|Usuwa obszar roboczy i powierzchni projektowej.|  
|**Usuń z obszaru roboczego**|Usuwa wybrane węzły z obszaru roboczego i powierzchni projektowej.|  
|**Usuń wszystkie oprócz zaznaczenia z obszaru roboczego**|Usuwa węzły, które nie są wybrane z obszaru roboczego i powierzchni projektowej.|  
|**Generowanie przykładowy kod XML**|Dostępne tylko dla elementów globalnej. Generuje przykładowy plik XML dla elementu globalnego.|  
|**Zaznacz wszystko**|Wybiera wszystkich węzłów w panelu obszaru roboczego.|  
|**Wyświetl kod**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element, który wybrano w Eksplorator schematu XML zostanie również wybrana w edytorze XML.|  
|**Okno właściwości**|Otwiera **właściwości** okna (o ile nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|  
  
## <a name="properties-window"></a>Okno Właściwości  
 Użyj menu kontekstowego, aby otworzyć początkowo **właściwości** okna. Domyślnie **właściwości** okno pojawia się w prawym dolnym rogu programu Visual Studio. Po kliknięciu węzła, który jest renderowany w widoku modelu zawartości, będzie można wyświetlić właściwości tego węzła w **właściwości** okna.  
  
## <a name="xsd-designer-toolbar"></a>Pasek narzędzi Projektanta XSD  
 Następujące przyciski narzędzi Projektanta XSD są włączone, gdy widok modelu zawartości jest aktywny.  
  
 ![XML Schema Designer Toolbar](../xml-tools/media/xsdcontentmodelviewtoolbar.gif "XSDContentModelViewToolbar")  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Pokaż widok startowy**|Przełącza do [widok startowy](../xml-tools/start-view.md). Ten widok jest możliwy za pomocą skrótów klawiaturowych: **CTRL + 1**.|  
|**Pokaż widok modelu zawartości**|Przełącza do [widoku modelu zawartości](../xml-tools/content-model-view.md). Ten widok jest możliwy za pomocą skrótów klawiaturowych: **CTRL + 2**.|  
|**Pokaż widok wykresu**|Przełącza do [widoku wykresu](../xml-tools/graph-view.md). Ten widok jest możliwy za pomocą skrótów klawiaturowych: **CTRL + 3**.|  
|**Usuń obszar roboczy**|Usuwa obszar roboczy i powierzchni projektowej.|  
|**Usuń z obszaru roboczego**|Usuwa wybrane węzły z obszaru roboczego i serface projektu.|  
|**Usuń wszystkie oprócz zaznaczenia z obszaru roboczego**|Usuwa węzły, które nie są wybrane z obszaru roboczego i serface projektu.|  
|**Pokaż dokumentacji**|Pokazuje lub ukrywa zawartość węzła adnotacji/dokumentację.|  
  
## <a name="panscroll"></a>Pan/przewijania  
 Za pomocą pasków przewijania lub przytrzymanie klawisza CTRL, gdy kliknij i przeciągnij myszą, można Przesuń powierzchni projektowej. Gdy przesuwa powierzchni projektowej kliknij i przeciągnij kursor zmieni się na cztery strzałki przecinające w czterech kierunkach.  
  
## <a name="undoredo"></a>Cofnij/Ponów.  
 Możliwość Cofnij/Ponów jest włączona w widoku modelu zawartości następujące akcje:  
  
-   Dodanie jednego węzła przez przeciąganie i upuszczanie.  
  
-   Dodawanie wielu węzłów z okna wyniki wyszukiwania w Eksploratorze schematu.  
  
-   Dodawanie węzłów z widoku startowego.  
  
-   Usunięcie jednego lub wielu węzłów.  
  
## <a name="zoom"></a>Powiększenie  
 Powiększenie jest dostępna w w prawym dolnym rogu widoku modelu zawartości.  
  
 Powiększenie mogą być kontrolowane w następujący sposób:  
  
- Przytrzymując klawisz CTRL i obracanie kółkiem myszy, gdy wskaźnik myszy znajduje się na powierzchni widoku modelu zawartości.  
  
- Za pomocą suwaka. Suwak pokazuje bieżący poziom powiększenia.  
  
  Suwak powiększenia jest nieprzezroczysta ją zaznaczyć, umieść kursor nad, lub użyj kombinacji klawisza CTRL kółkiem myszy, aby powiększyć; w pozostałych godzinach jest przezroczysty.  
  
## <a name="xml-editor-integration"></a>Integracja z edytorem XML  
 Możesz przełączać się i z powrotem między Projektant XSD i edytorem XML za pomocą menu kontekstowego.  
  
 W przypadku wprowadzenia zmian schematu w edytorze XML zestawu zmian zostaną zsynchronizowane w widoku modelu zawartości. Aby uzyskać więcej informacji, zobacz [integracja za pomocą edytora XML](../xml-tools/integration-with-xml-editor.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obszar roboczy projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md)
