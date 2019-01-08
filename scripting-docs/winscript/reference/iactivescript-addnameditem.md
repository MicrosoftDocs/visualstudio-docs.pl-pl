---
title: IActiveScript::AddNamedItem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4ae4a84821d0db226cbecb01e329e4f2941a675d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095098"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Dodaje nazwę elementu głównego poziomu do przestrzeni nazw aparatu skryptów. Element poziomu głównego jest obiektem, właściwości i metod, źródła zdarzeń lub wszystkich trzech środowiskach.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrName`  
 [in] Adres buforu, który zawiera nazwę elementu, tak jak to pokazano w skrypcie. Nazwa musi być unikatowa i stałe.  
  
 `dwFlags`  
 [in] Flagi skojarzone z elementem. Może być kombinacją tych wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Wskazuje, czy nazwany element reprezentuje obiekt tylko do kodu, nie ma hosta `IUnknown` ma zostać skojarzony z tym obiektem tylko do kodu. Host ma tylko nazwy dla tego obiektu. W językach obiektowych, takich jak C++ ta flaga utworzyć klasę. Nie wszystkie języki obsługują tę flagę.|  
|SCRIPTITEM_GLOBALMEMBERS|Wskazuje, że element jest kolekcją globalne właściwości i metody związane ze skryptem. Zazwyczaj aparat skryptów rozróżnia nazwę obiektu (inne niż na potrzeby korzystania z niego jako plik cookie dla [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) metody lub eliminowania jawnego określania zakresu) i uwidocznić jej członków jako globalne zmienne i metody. Dzięki temu hosta rozszerzyć biblioteki (funkcje środowiska uruchomieniowego i tak dalej) dla skryptu. Pozostawia się silnik wykonywania skryptów, aby poradzić sobie z nazwą powoduje konflikt (na przykład, gdy dwa elementy SCRIPTITEM_GLOBALMEMBERS metody o tej samej nazwie), mimo że błąd nie powinien być zwracany ze względu na tę sytuację.|  
|SCRIPTITEM_ISPERSISTENT|Wskazuje, czy element powinien być zapisany, jeśli silnik wykonywania skryptów jest zapisany. Podobnie, ustawienie tej flagi wskazuje, że przejścia z powrotem do stanu zainicjowania powinien zachować informacje nazwę i typ elementu (silnik wykonywania skryptów musi jednak zwalniać wszystkie wskaźniki prowadzące do interfejsów rzeczywistego obiektu).|  
|SCRIPTITEM_ISSOURCE|Wskazuje, że element źródła zdarzeń, które skrypt może ujścia. Obiektów podrzędnych (właściwości obiektu, które znajdują się w samych obiektach) można również źródła zdarzeń do skryptu. Nie jest cykliczna, ale na przykład zapewnia wygodny mechanizm często spotykana tworzenia kontrolki kontenera i wszystkie jego elementów członkowskich.|  
|SCRIPTITEM_ISVISIBLE|Wskazuje, że nazwa elementu jest dostępna w przestrzeni nazw skryptu, zezwalając na dostęp do właściwości, metod i zdarzeń elementu. Zgodnie z Konwencją właściwości elementu obejmują elementy podrzędne elementu; w związku z tym wszystkie podrzędne obiektu właściwości i metod (i ich elementy podrzędne, cyklicznie) będą dostępne.|  
|SCRIPTITEM_NOCODE|Wskazuje, że element jest po prostu nazwą, które są dodawane do przestrzeni nazw skryptu i nie powinny być traktowane jako element, dla którego powinien zostać zwrócony kod skojarzone. Na przykład bez ta flaga jest ustawiona, VBScript spowoduje utworzenie oddzielnego modułu o nazwie elementu i języka C++ utworzyć klasę otoki oddzielnych dla nazwanego elementu.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument ten był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jeszcze nie został załadowany lub zainicjowany).|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)