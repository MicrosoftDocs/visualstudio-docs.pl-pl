---
title: IActiveScriptAuthor::AddNamedItem | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 95bc529db8129c4e9af1ed9f9dc3d91de9686223
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58145658"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Dodaje nazwę elementu głównego poziomu do skryptu tworzenia przestrzeni nazw aparatu. A *elementu poziomu głównego* jest obiektem, który może zawierać właściwości i metody, a, mogą również zawierać źródło zdarzeń.  
  
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
 [in] Nazwa elementu jak wyświetlać ze skryptu. Nazwa musi być unikatowa i stałe.  
  
 `dwFlags`  
 [in] Flagi, które są skojarzone z nazwanego elementu. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Wskazuje, że nazwa elementu jest dostępna w przestrzeni nazw skryptu. Dzięki temu dostęp do elementu właściwości, metody i zdarzenia.<br /><br /> Zgodnie z Konwencją właściwości elementu obejmują elementy podrzędne elementu. W związku z tym wszystkie właściwości obiektu podrzędnego i metod (i ich elementy podrzędne, cyklicznie) są dostępne.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Wskazuje źródło elementu zdarzenia, że skrypt może mieć procedury obsługi zdarzeń skryptu.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Wskazuje, że element jest kolekcją globalnych właściwości i metod, które są skojarzone ze skryptem. Jego członkowie są tworzone jako zmienne globalne i metody.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Wskazuje, czy element powinien być zapisany, jeśli skrypt tworzenia aparat są zapisywane.|  
|SCRIPTITEM_CODEONLY|0x00000200|Wskazuje, że nazwany element reprezentuje obiekt tylko do kodu i nie ma członka do autora.|  
|SCRIPTITEM_NOCODE|0x00000400|Wskazuje, że nazwany element jest tylko nazwy, które są dodawane i go nie ma nic do autora.|  
  
 `pdisp`  
 [in] `IDispatch` z `NamedItem` obiekt, który służy do zbierania, metody, właściwości lub źródło zdarzenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)