---
title: 'IActiveScriptAuthor:: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d2f08a49fdc768e87152bf486ce48687c79e68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577258"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Dodaje nazwę elementu poziomu głównego do przestrzeni nazw aparatu tworzenia skryptów. *Element poziomu głównego* jest obiektem, który może zawierać właściwości i metody, a także może zawierać Źródło zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 podczas Nazwa elementu wyświetlanego ze skryptu. Nazwa musi być unikatowa i trwała.  
  
 `dwFlags`  
 podczas Flagi, które są skojarzone z nazwanym elementem. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Wskazuje, że nazwa elementu jest dostępna w przestrzeni nazw skryptu. Pozwala to na dostęp do właściwości, metod i zdarzeń elementu.<br /><br /> Zgodnie z Konwencją właściwości elementu zawierają podrzędne elementy członkowskie elementu. W związku z tym wszystkie właściwości i metody obiektu podrzędnego (i ich elementy podrzędne, cyklicznie) są dostępne.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Wskazuje zdarzenia źródła elementu, które skrypt może mieć procedury obsługi zdarzeń skryptu.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Wskazuje, że element jest kolekcją właściwości globalnych i metod, które są skojarzone ze skryptem. Jego składowe są tworzone jako zmienne i metody globalne.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Wskazuje, że element powinien być zapisany, gdy jest zapisywany aparat tworzenia skryptów.|  
|SCRIPTITEM_CODEONLY|0x00000200|Wskazuje, że nazwany element reprezentuje obiekt tylko kod i nie ma elementu członkowskiego do utworzenia.|  
|SCRIPTITEM_NOCODE|0x00000400|Wskazuje, że nazwany element jest tylko dodawaną nazwą i nie ma nic do autora.|  
  
 `pdisp`  
 podczas @No__t_0 obiektu `NamedItem`, który jest używany do zbierania metod, właściwości lub źródła zdarzenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptAuthor   interfejsu](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)