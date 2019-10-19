---
title: 'IScriptEntry:: GetSignature | Microsoft Docs'
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
ms.openlocfilehash: e7b07ac64ce7e427a793f0af0db9a7905441d39b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575422"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Zwraca informacje o typie dla obiektu funkcji `IScriptEntry`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppti`  
 określoną Informacje o typie skojarzone z tym obiektem funkcji `IScriptEntry`.  
  
 `piMethod`  
 określoną Indeks metody w obiekcie `ITypeInfo`.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Informacje o typie są ustawiane za pomocą [IScriptEntry:: SetSignature](../../winscript/reference/iscriptentry-setsignature.md) lub [IScriptNode:: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informacje o typie mogą być również generowane przez wpis w oparciu o reprezentację funkcji wewnętrznej.  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)