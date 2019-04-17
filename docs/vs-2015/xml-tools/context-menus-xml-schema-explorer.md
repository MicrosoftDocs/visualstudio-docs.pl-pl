---
title: Menu kontekstowe (Eksplorator schematu XML) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d6c14a268ef58dec31f65fe73e176eac8f690d9c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653961"
---
# <a name="context-menus-xml-schema-explorer"></a>Menu kontekstowe (Eksplorator schematu XML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Następujące elementy menu kontekstowego są używane do wykonywania wyszukiwania specyficznego dla schematu i inne operacje.  
  
## <a name="node-type-schema-set"></a>Typ węzła: Zestaw schematów  
 W poniższej tabeli opisano opcje, które są dostępne dla schematu zestawu węzłów.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Pokaż najbardziej prawdopodobne elementy główne**|Umożliwia znalezienie i wyróżnia wszystkie elementy globalne, które nie są wywoływane z elementy globalne innego niż on sam.|  
|**Pokaż typy globalne**|Umożliwia znalezienie i wyróżnia wszystkie typy globalne w zestawie schematów.|  
|**Pokaż elementy globalne**|Umożliwia znalezienie i wyróżnia wszystkie elementy globalne w zestawie schematów.|  
|**Okno właściwości**|Otwiera **właściwości** okna (o ile nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|  
  
## <a name="node-type-namespace"></a>Typ węzła: Przestrzeń nazw  
 W poniższej tabeli opisano opcje, które są dostępne dla węzła obszaru nazw.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Pokaż wszystkie odwołania dla ruchu przychodzącego**|Umożliwia znalezienie i wyróżnienie pliki, które importują wybranej przestrzeni nazw.|  
|**Pokaż wszystkie odwołania wychodzące**|Dla każdego pliku w wybranej przestrzeni nazw znajduje i wyróżnia następujące czynności:<br /><br /> — Wszystkie przestrzenie nazw, do którego odwołuje się zaimportować instrukcji bez `schemaLocation` atrybutu.<br />— Wszystkie pliki w przestrzeniach nazw, innym niż wybrana, które są określone w `schemaLocation` atrybutu podczas importowania i instrukcji #include.|  
|**Pokaż typy globalne**|Umożliwia znalezienie i wyróżnia wszystkie typy globalne w wybranej przestrzeni nazw.|  
|**Pokaż elementy globalne**|Umożliwia znalezienie i wyróżnia wszystkie elementy globalne w wybranej przestrzeni nazw.|  
|**Okno właściwości**|Otwiera **właściwości** okna (o ile nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|  
  
## <a name="node-type-file"></a>Typ węzła: Plik  
 W poniższej tabeli opisano opcje, które są dostępne dla węzła pliku.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Pokaż wszystkie odwołania dla ruchu przychodzącego**|Wyszukuje i wyróżnia wszystkie pliki, które określają wybranego pliku w `schemaLocation` atrybuty im instrukcje dołączania, a następnie zaimportować.|  
|**Pokaż wszystkie odwołania wychodzące**|Wyszukuje i wyróżnione są następujące:<br /><br /> — Wszystkie przestrzenie nazw określony w atrybucie przestrzeni nazw wszystkich zaimportuj instrukcje, które nie mają `schemaLocation` atrybutu.<br />— Wszystkie pliki określone w `schemaLocation` wszystkie atrybuty importowania i instrukcji #include.|  
|**Pokaż typy globalne**|Umożliwia znalezienie i wyróżnia wszystkie typy globalne w tym pliku.|  
|**Pokaż elementy globalne**|Umożliwia znalezienie i wyróżnia wszystkie elementy globalne w tym pliku.|  
|**Wyświetl kod**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element, który wybrano w Eksplorator schematu XML zostanie również wybrana w edytorze XML.|  
|**Okno właściwości**|Otwiera **właściwości** okna (o ile nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|  
  
## <a name="all-global-node-types"></a>Wszystkie typy węzłów globalne  
 W poniższej tabeli opisano opcje, które są dostępne dla wszystkich węzłów globalnego.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Pokaż w widoku wykresu**|Zostanie otwarty w widoku wykresu. Jeśli wybrany węzeł nie jest w obszarze roboczym, dodaje go do obszaru roboczego, a następnie wybiera węzeł.|  
|**Pokaż w widoku modelu zawartości**|Zostanie otwarty widok modelu zawartości. Jeśli wybrany węzeł nie jest w obszarze roboczym, dodaje go do obszaru roboczego, a następnie wybiera węzeł.|  
|**Wyświetl kod**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element, który wybrano w Eksplorator schematu XML zostanie również wybrana w edytorze XML.|  
|**Okno właściwości**|Otwiera **właściwości** okna (o ile nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|  
  
## <a name="node-type-element"></a>Typ węzła: Element  
 Oprócz opcji do globalnego węzłów opisanych powyżej menu kontekstowe dla węzłów elementów ma następujące opcje:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Przejdź do definicji typu**|Powoduje przejście do definicji typu wybranego elementu. Ma to zastosowanie, gdy typ, który jest używany dla elementu jest typ globalny.|  
|**Przejdź do oryginalnego elementu.**|Dla odwołania do elementu przechodzi do rzeczywistego definicji elementu.|  
|**Pokaż wszystkie odwołania**|Globalne elementów znajduje i wyróżnia wszystkie odwołania (elementy, które mają `ref="selectedElement"`) do wybranego elementu.|  
|**Pokaż składowe grupy podstawienia**|Dla kierowników grupy podstawienia, wyszukuje i zaznacza wszystkie elementy, które są elementami członkowskimi grupy podstawienia wybrany element jest elementem członkowskim. Spowoduje to pokazanie bezpośrednie i pośrednie uczestników.|  
|**Grupa podstawienia show głowic**|Dla elementów globalne, które są elementami członkowskimi grupy podstawienia, znajdzie i wyróżnia wszystkie nagłówki bezpośrednie i pośrednie dla wybranego elementu, takich jak następujące:<br /><br /> -Określonego dla wybranego elementu head grupy podstawienia.<br />-Określony w jej głównego elementu head grupy podstawienia.|  
|**Generowanie przykładowy kod XML**|Dostępne tylko dla elementów globalnej. Generuje przykładowy plik XML dla elementu globalnego.|  
  
## <a name="node-type-global-types"></a>Typ węzła: Typy globalne  
 Oprócz opcji do globalnego węzłów opisanych powyżej menu kontekstowe dla węzłów typu globalnego ma następujące opcje:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Pokaż typy podstawowe**|Jeśli wybrany typ pochodzi od typu globalnego, przechodzi do typu podstawowego wybranego typu.|  
|**Pokaż wszystkie odwołania**|Umożliwia znalezienie i wyróżnia wszystkie odwołania do wybranego typu. Obejmuje to elementy i atrybuty wybranego typu i typy pochodzące od wybranego typu.|  
|**Pokaż wszystkie typy pochodne**|Umożliwia znalezienie i wyróżnia wszystkie typy, które bezpośredniego lub pośredniego pochodzą od wybranego typu.|  
|**Wyświetlanie wszystkich elementów nadrzędnych**|Pokaż wszystkie typy nadrzędnego (podstawowa).|  
  
## <a name="node-type-attribute"></a>Typ węzła: Atrybut  
 Oprócz opcji do globalnego węzłów opisanych powyżej menu kontekstowe dla węzłów atrybutu ma następujące opcje:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Przejdź do definicji typu**|Jeśli typ, który jest używany dla atrybutu jest typu globalnego, przechodzi do definicji typu wybranego atrybutu.|  
|**Przejdź do oryginalnego atrybutu**|Atrybut odwołania przechodzi do rzeczywistego definicję atrybutu.|  
|**Pokaż wszystkie odwołania**|Dla atrybutami globalnymi, wyszukuje i wyróżnia wszystkie odwołania (inne atrybuty, które mają `ref="selectedAttribute"`) do wybranego atrybutu.|  
  
## <a name="node-type-attribute-group"></a>Typ węzła: Grupa atrybutów  
 Oprócz opcji do globalnego węzłów opisanych powyżej menu kontekstowe dla węzłów grupy atrybutu ma następujące opcje:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Przejdź do definicji**|Odwołania przechodzi do rzeczywistego definicję atrybutu.|  
|**Pokaż wszystkie elementy członkowskie**|Umożliwia znalezienie i wyróżnienie wszyscy członkowie grupy atrybutów.|  
|**Pokaż wszystkie odwołania**|Wyszukuje i wyróżnia wszystkie odwołania (grupy, które mają atrybut `ref="selectedAttributeGroup"`) do wybranej grupy atrybutów.|  
  
## <a name="node-type-named-group"></a>Typ węzła: Nazwanej grupy  
 Oprócz opcji do globalnego węzłów opisanych powyżej menu kontekstowe dla nazwanej grupy węzłów ma następujące opcje:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Przejdź do definicji**|Odwołania przechodzi do rzeczywistego definicję atrybutu.|  
|**Pokaż wszystkie elementy członkowskie**|Umożliwia znalezienie i wyróżnienie wszystkich członków grupy o nazwie.|  
|**Pokaż wszystkie odwołania**|Wyszukuje i wyróżnia wszystkie odwołania (grupy, które mają `ref="selectedGroup"`) do wybranej grupy.|  
  
## <a name="see-also"></a>Zobacz też  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)   
 [Wyszukiwanie zestawu schematów](../xml-tools/searching-the-schema-set.md)
