---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732562"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Uzyskuje bajty atrybutów niestandardowych, biorąc pod uwagę nazwę atrybutu niestandardowego.

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
[w] Ciąg zawierający nazwę atrybutu niestandardowego, który ma być wyszukyny.

`ppBlob`\
[w, na zewnątrz] Tablica wypełniona bajtami atrybutów niestandardowych.

`pdwLen`\
[w, na zewnątrz] Określa maksymalną liczbę bajtów do `ppBlob` zwrócenia w tablicy i zwraca liczbę bajtów faktycznie zapisanych do tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli atrybut niestandardowy nie istnieje. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ustaw `ppBlob` parametr na wartość null, aby zwrócić liczbę dostępnych bajtów atrybutów. Następnie przydzielić tablicę i przekazać `ppBlob` tę tablicę dla parametru.

 Bajty atrybutu reprezentują nieprzetworzone dane atrybutu niestandardowego.

 Jeśli `ppBlob` parametry `pdwLen` i są ustawione na wartość null, ta metoda może służyć do określenia, czy atrybut niestandardowy tylko istnieje. Łatwiejszą alternatywą jest jednak wywołanie [Metody IsCustomAttributeDedefdefiniowana.](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)

## <a name="see-also"></a>Zobacz też
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
