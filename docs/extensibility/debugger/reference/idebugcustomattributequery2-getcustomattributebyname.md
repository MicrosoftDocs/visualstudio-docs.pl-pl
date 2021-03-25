---
description: Uzyskuje bajty atrybutów niestandardowych, używając nazwy atrybutu niestandardowego.
title: 'IDebugCustomAttributeQuery2:: GetCustomAttributeByName — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd8b1793bad585dd808ebd812b610cd68aabc129
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077606"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Uzyskuje bajty atrybutów niestandardowych, używając nazwy atrybutu niestandardowego.

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

## <a name="parameters"></a>Parametry
`pszCustomAttributeName`\
podczas Ciąg zawierający nazwę atrybutu niestandardowego do wyszukania.

`ppBlob`\
[in. out] Tablica, która jest uzupełniona o bajty atrybutów niestandardowych.

`pdwLen`\
[in. out] Określa maksymalną liczbę bajtów zwracanych w `ppBlob` tablicy i zwraca liczbę bajtów rzeczywiście zapisaną do tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli atrybut niestandardowy nie istnieje. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ustaw `ppBlob` parametr na wartość null, aby zwrócić liczbę dostępnych bajtów atrybutów. Następnie przydziel tablicę i przekaż tę tablicę do `ppBlob` parametru.

 Atrybut bajty reprezentuje pierwotne dane atrybutu niestandardowego.

 Jeśli `ppBlob` Parametry i `pdwLen` są ustawione na wartość null, ta metoda może służyć do określenia, czy atrybut niestandardowy już istnieje. Jednak łatwiejszym rozwiązaniem jest wywołanie metody [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
