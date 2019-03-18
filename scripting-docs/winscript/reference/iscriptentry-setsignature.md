---
title: IScriptEntry::SetSignature | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 42740a0e6261317443b8c9cc23559a2f92f66540
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58150611"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Ustawia typ informacji dla `IScriptEntry` obiektu funkcyjnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pti`  
 [in] Informacje o typie.  
  
 `iMethod`  
 [in] Indeks metody w `ITypeInfo` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Należy określić przy użyciu informacji o typie `IScriptEntry::SetSignature` lub [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informacje o typie można również wygenerować we wpisie oparte na funkcji wewnętrznej reprezentacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)