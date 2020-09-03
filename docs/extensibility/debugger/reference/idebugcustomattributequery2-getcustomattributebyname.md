---
title: 'IDebugCustomAttributeQuery2:: GetCustomAttributeByName — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47471f2743e705b06fb9a1bda6752b24a7836d1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732562"
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
