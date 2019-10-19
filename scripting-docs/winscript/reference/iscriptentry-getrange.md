---
title: 'IScriptEntry:: GetRange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a6e1b1600c93aa05bbe9669fb57a23a8c9344a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575434"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Zwraca pozycję początkową i długość wpisu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pichMin`  
 określoną Dla `IScriptEntry` obiektów, które określają blok skryptu, zwraca wartość 0.  
  
 Dla `IScriptEntry` obiektów, które określają obiekt Function, zwraca pozycję początkową funkcji w bieżącym bloku skryptu.  
  
 W przypadku obiektów `IScriptScriptlet` zwraca wartość 0.  
  
 `pcch`  
 określoną Dla `IScriptEntry` obiektów, które określają blok skryptu, zwraca długość tekstu.  
  
 Dla `IScriptEntry` obiektów, które określają obiekt Function, zwraca długość definicji funkcji.  
  
 W przypadku obiektów `IScriptScriptlet` zwraca długość wpisu.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)