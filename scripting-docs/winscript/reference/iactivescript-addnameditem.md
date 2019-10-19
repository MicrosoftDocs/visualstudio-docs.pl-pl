---
title: 'IActiveScript:: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a343e38b944ca36da221da39832046c19b332230
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575826"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Dodaje nazwę elementu poziomu głównego do obszaru nazw aparatu skryptów. Element poziomu głównego to obiekt z właściwościami i metodami, źródłem zdarzenia lub wszystkimi trzema.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrName`  
 podczas Adres buforu, który zawiera nazwę elementu wyświetlanego ze skryptu. Nazwa musi być unikatowa i trwała.  
  
 `dwFlags`  
 podczas Flagi skojarzone z elementem. Może być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Wskazuje, że nazwany element reprezentuje obiekt tylko kod i że host nie ma `IUnknown` do skojarzenia z tym obiektem tylko kod. Host ma tylko nazwę dla tego obiektu. W językach zorientowanych obiektowo, takich C++jak, ta flaga utworzy klasę. Nie wszystkie języki obsługują tę flagę.|  
|SCRIPTITEM_GLOBALMEMBERS|Wskazuje, że element jest kolekcją właściwości globalnych i metod skojarzonych ze skryptem. Zwykle aparat skryptów ignoruje nazwę obiektu (inną niż w celu użycia go jako plik cookie dla metody [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) lub do rozpoznawania jawnego określania zakresu) i uwidacznia jego składowe jako zmienne globalne i metody. Umożliwia to hostowi rozszerzone biblioteki (funkcje czasu wykonywania itd.), które są dostępne dla skryptu. Pozostało do aparatu skryptów, aby rozwiązać konflikty nazw (na przykład gdy dwa elementy SCRIPTITEM_GLOBALMEMBERS mają metody o tej samej nazwie), chociaż błąd nie powinien być zwracany z powodu takiej sytuacji.|  
|SCRIPTITEM_ISPERSISTENT|Wskazuje, że element powinien być zapisany w przypadku zapisania aparatu skryptów. Analogicznie, ustawienie tej flagi wskazuje, że przejście z powrotem do stanu zainicjowania powinno zachować nazwę i informacje o typie elementu (aparat obsługi skryptów musi jednak wydać wszystkie wskaźniki do interfejsów na rzeczywistym obiekcie).|  
|SCRIPTITEM_ISSOURCE|Wskazuje, że element jest źródłem zdarzeń, które skrypt może ujścia. Obiekty podrzędne (właściwości obiektu, które znajdują się w samych obiektach) mogą również być źródłem zdarzeń do skryptu. Nie jest to cykliczne, ale zapewnia wygodny mechanizm dla typowego przypadku, na przykład tworzenie kontenera i wszystkich jego elementów członkowskich.|  
|SCRIPTITEM_ISVISIBLE|Wskazuje, że nazwa elementu jest dostępna w przestrzeni nazw skryptu, co umożliwia dostęp do właściwości, metod i zdarzeń elementu. Według Konwencji właściwości elementu obejmują elementy podrzędne elementu. w związku z tym wszystkie właściwości i metody obiektu podrzędnego (i ich elementy podrzędne, rekursywnie) będą dostępne.|  
|SCRIPTITEM_NOCODE|Wskazuje, że element jest po prostu dodawany do obszaru nazw skryptu i nie powinien być traktowany jako element, dla którego należy skojarzyć kod. Na przykład bez ustawienia tej flagi skrypt VBScript utworzy oddzielny moduł dla nazwanego elementu i C++ może utworzyć oddzielną klasę otoki dla nazwanego elementu.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_INVALIDARG`|Nieprawidłowy argument.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów nie został jeszcze załadowany lub zainicjowany).|  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript](../../winscript/reference/iactivescript.md)