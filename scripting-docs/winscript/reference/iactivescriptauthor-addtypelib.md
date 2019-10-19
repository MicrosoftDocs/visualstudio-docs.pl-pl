---
title: 'IActiveScriptAuthor:: AddTypeLib | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddTypeLib
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bd96732a905d3fc0732ccfeaf2b65ada82957f4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577230"
---
# <a name="iactivescriptauthoraddtypelib"></a>IActiveScriptAuthor::AddTypeLib
Dodaje bibliotekę typów do przestrzeni nazw dla skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rguidTypeLib`  
 podczas Identyfikator CLSID (Identyfikator klasy) biblioteki typów, która ma zostać dodana.  
  
 `dwMajor`  
 podczas Główny numer wersji.  
  
 `dwMinor`  
 podczas Pomocniczy numer wersji.  
  
 `dwFlags`  
 podczas Nieużywane.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje `LoadTypeLib`, aby załadować bibliotekę typów. Po pomyślnym wykonaniu tej metody wywołania `IActiveScriptAuthor::AddNamedItem` w celu dodania informacji o typie.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptAuthor   interfejsu](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor:: AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)    
 [LoadTypeLib](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelib)