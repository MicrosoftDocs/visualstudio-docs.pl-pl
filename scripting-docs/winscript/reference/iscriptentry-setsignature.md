---
title: 'IScriptEntry:: SetSignature | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e381e642462fe56e661de9da0d8974dc7bf18b18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575341"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Ustawia informacje o typie dla obiektu funkcji `IScriptEntry`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pti`  
 podczas Informacje o typie.  
  
 `iMethod`  
 podczas Indeks metody w obiekcie `ITypeInfo`.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Informacje o typie są ustawiane przy użyciu `IScriptEntry::SetSignature` lub [IScriptNode:: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informacje o typie mogą być również generowane przez wpis w oparciu o reprezentację funkcji wewnętrznej.  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)