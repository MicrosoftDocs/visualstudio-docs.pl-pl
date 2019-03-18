---
title: IScriptEntry::GetSignature | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70cc1939ae4eb1e3c58d31b3d42b7f1b4603ce9e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58145307"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Zwraca typ informacji dla `IScriptEntry` obiektu funkcyjnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppti`  
 [out] Wpisz informacje skojarzone z tym `IScriptEntry` obiektu funkcyjnego.  
  
 `piMethod`  
 [out] Metoda indeksu w `ITypeInfo` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Należy określić przy użyciu informacji o typie [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) lub [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informacje o typie można również wygenerować we wpisie oparte na funkcji wewnętrznej reprezentacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)