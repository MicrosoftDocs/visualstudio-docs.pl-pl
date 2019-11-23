---
title: 'IScriptNode:: CreateChildHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e024bb7d6a81b35994edddfe9e71666b0ee8df0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573601"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Dodaje Scriptlet jako wystąpienie podrzędne `IScriptNode`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszDefaultName`  
 podczas Adres nazwy domyślnej, która ma zostać skojarzona z Scriptlet.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] Lista identyfikatorów z w pełni kwalifikowanej nazwy hosta.  
  
 `cpszNames`  
 podczas Liczba identyfikatorów w parametrze `prgpszNames`.  
  
 `pszEvent`  
 podczas Adres buforu identyfikujący nazwę zdarzenia skojarzoną z Scriptlet.  
  
 `pszDelimiter`  
 podczas Adres ogranicznika bloku End-of-Script. W celu przeanalizowania Host zwykle używa ogranicznika (takiego jak dwa znaki pojedynczego cudzysłowu) w celu wykrycia końca bloku skryptu.  
  
 Ogranicznik włącza przetwarzanie wstępne przez aparat tworzenia skryptów. Na przykład aparat może zamienić pojedynczy cudzysłów z dwoma pojedynczymi cudzysłowami do użycia jako ogranicznik. Aparat określa sposób użycia ogranicznika.  
  
 Ustaw wartość NULL, jeśli żaden ogranicznik nie zostanie użyty do zidentyfikowania końca bloku skryptu.  
  
 `ptiSignature`  
 podczas Informacje o typie dla obiektu funkcji.  
  
 `iMethodSignature`  
 podczas Indeks funkcji w parametrze `ITypeInfo``ptiSignature`.  
  
 `isn`  
 podczas Indeks elementu podrzędnego w elemencie nadrzędnym.  
  
 `dwCookie`  
 podczas Zdefiniowana przez aplikację wartość, która jest używana do kojarzenia wpisu z obiektem hosta.  
  
 `ppse`  
 określoną Adres zmiennej, która otrzymuje wskaźnik do interfejsu `IScriptEntry` wystąpienia podrzędnego.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Scriptlet określa procedurę obsługi zdarzeń. Ta metoda tworzy element Scriptlet, jeśli jest wywoływany przez obiekt `IScriptNode`, który reprezentuje stronę sieci Web. Ta metoda nie powiedzie się, jeśli jest wywoływana przez inne interfejsy.  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptNode  interfejsu](../../winscript/reference/iscriptnode-interface.md)  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)