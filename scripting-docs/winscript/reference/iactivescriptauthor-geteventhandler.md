---
title: IActiveScriptAuthor::GetEventHandler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7bba60df6485ddaac0363a3416739efd7be69389
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58145645"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Zwraca scriptlet, który ma określone atrybuty.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdisp`  
 [in] `IDispatch` Obiekt, który odpowiada `NamedItem` do której jest dołączona scriptlet.  
  
 `pszItem`  
 [in] Adres buforu identyfikator najwyższego poziomu o nazwie FQDN scriptlet na hoście.  
  
 `pszSubItem`  
 [in] Adres buforu identyfikator drugiego poziomu, nazwy FQDN scriptlet na hoście. Ustaw na wartość NULL, jeśli nazwa zawiera tylko jeden poziom.  
  
 `pszEvent`  
 [in] Adres buforu, który zawiera nazwę zdarzenia. Scriptlet ma program obsługi zdarzeń dla tego zdarzenia.  
  
 `ppse`  
 [out] Adres zmiennej, która otrzymuje wskaźnik `IScriptEntry` interfejsu scriptlet, który ma określone atrybuty.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)