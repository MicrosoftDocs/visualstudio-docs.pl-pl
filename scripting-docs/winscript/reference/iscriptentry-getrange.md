---
title: IScriptEntry::GetRange | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6a4e053817ed4c503ebb41e2f3828da421e69ec7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088741"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Zwraca pozycji początkowej i długości hasła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pichMin`  
 [out] Aby uzyskać `IScriptEntry` zwraca wartość 0, obiekty, które określają blok skryptu.  
  
 Aby uzyskać `IScriptEntry` obiekty, które określają obiekt funkcji zwraca pozycja początkowa funkcji w bieżącym bloku skryptu.  
  
 Aby uzyskać `IScriptScriptlet` obiektów, funkcja zwraca 0.  
  
 `pcch`  
 [out] Aby uzyskać `IScriptEntry` obiekty, które określają blok skryptu zwraca długość tekstu.  
  
 Aby uzyskać `IScriptEntry` obiekty, które określają obiekt funkcji zwraca długość definicji funkcji.  
  
 Aby uzyskać `IScriptScriptlet` obiektów, funkcja zwraca długość wpisu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)