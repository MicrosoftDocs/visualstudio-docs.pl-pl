---
description: Pobiera adres debugowania, który następuje po danym adresie debugowania w metodzie.
title: 'IDebugSymbolProvider:: GetNextAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d177d03daef4f8d3344941658b85f71551af126b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168416"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Pobiera adres debugowania, który następuje po danym adresie debugowania w metodzie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetNextAddress( 
   IDebugAddress*  pAddress,
   BOOL            fStatementOnly,
   IDebugAddress** ppAddress
);
```

```csharp
int GetNextAddress( 
   IDebugAddress     pAddress,
   bool              fStatementOnly,
   out IDebugAddress ppAddress
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
podczas Podanym adresem debugowania.

`fStatementOnly`\
podczas W przypadku wartości TRUE program ogranicza adresy debugowania do pojedynczej instrukcji.

`ppAddress`\
określoną Zwraca następny adres debugowania.

## <a name="return-value"></a>Wartość zwracana
 Zwraca prawidłową `HRESULT` , zazwyczaj S_OK.

## <a name="see-also"></a>Zobacz też
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
