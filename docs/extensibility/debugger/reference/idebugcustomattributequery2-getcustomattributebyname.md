---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e6275f67e07c88cb337c77bc672394af539b8e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875951"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Pobiera atrybuty niestandardowe bajtów, biorąc pod uwagę nazwę atrybutu niestandardowego.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

#### <a name="parameters"></a>Parametry
 `pszCustomAttributeName`

 [in] Ciąg zawierający nazwę atrybutu niestandardowego do wyszukania.

 `ppBlob`

 [out w] Tablica, która jest wypełniane bajtów atrybutu niestandardowego.

 `pdwLen`

 [out w] Określa maksymalną liczbę bajtów do zwrócenia w `ppBlob` tablicy i zwraca liczbę bajtów rzeczywiście zapisanych na tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli nie ma atrybutu niestandardowego. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ustaw `ppBlob` parametr ma wartość null, aby zwrócić liczbę atrybutów dostępnych bajtów. Następnie przydzielić tablicy i przekażesz ten tablica w `ppBlob` parametru.

 Bajty atrybut reprezentują dane pierwotne atrybutu niestandardowego.

 Jeśli `ppBlob` i `pdwLen` parametry są ustawione na wartość null, Metoda ta może służyć do ustalenia, czy atrybut niestandardowy jedynie istnieje. Alternatywą łatwiej jest jednak wywołać [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)