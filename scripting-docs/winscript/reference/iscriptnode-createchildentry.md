---
title: 'IScriptNode:: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c58ff83c43a1418e6fb7bd8945afa181af60c68a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573615"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Dodaje wystąpienie podrzędne `IScriptEntry`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `isn`  
 podczas Indeks elementu podrzędnego w elemencie nadrzędnym.  
  
 `dwCookie`  
 podczas Zdefiniowana przez aplikację wartość służąca do kojarzenia wpisu podrzędnego z obiektem hosta.  
  
 `pszDelimiter`  
 podczas Adres ogranicznika bloku End-of-Script. W celu przeanalizowania Host zwykle używa ogranicznika (takiego jak dwa znaki pojedynczego cudzysłowu) w celu wykrycia końca bloku skryptu.  
  
 Ogranicznik umożliwia aparatowi tworzenia skryptów zapewnienie wstępnego przetwarzania. Na przykład aparat może zamienić pojedynczy cudzysłów z dwoma pojedynczymi cudzysłowami do użycia jako ogranicznik. Aparat określa sposób użycia ogranicznika.  
  
 Ustaw wartość NULL, jeśli ogranicznik nie oznacza końca bloku skryptu.  
  
 `ppse`  
 określoną Adres zmiennej, która otrzymuje wskaźnik do interfejsu `IScriptEntry` wystąpienia podrzędnego.  
  
 W przypadku `IScriptNode` obiektów reprezentujących stronę sieci Web ten parametr zwraca wystąpienie `IScriptEntry`, które określa blok skryptu.  
  
 Dla `IScriptEntry` obiektów, które reprezentują blok skryptu, ten parametr zwraca wystąpienie `IScriptEntry`, które określa obiekt funkcji.  
  
 W przypadku `IScriptEntry` obiektów, które reprezentują obiekt Function, ta metoda kończy się niepowodzeniem.  
  
 W przypadku obiektów `IScriptScriptlet` ta metoda kończy się niepowodzeniem.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `IScriptNode` reprezentuje stronę sieci Web lub jej elementy. Interfejs `IScriptEntry` (pochodzący z `IScriptNode`) reprezentuje blok skryptu lub obiekt funkcji. Interfejs `IScriptScriptlet` (pochodzący z `IScriptEntry`) reprezentuje procedurę obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptNode   interfejsu](../../winscript/reference/iscriptnode-interface.md)  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)