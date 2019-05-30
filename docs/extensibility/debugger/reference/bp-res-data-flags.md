---
title: BP_RES_DATA_FLAGS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RES_DATA_FLAGS
helpviewer_keywords:
- BP_RES_DATA_FLAGS enumeration
ms.assetid: d97611e2-def6-45a9-ad7d-eedf2ad4c82b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7573d9bde08f69a7c7e7707d7631dc71e2d8d5e6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350644"
---
# <a name="bpresdataflags"></a>BP_RES_DATA_FLAGS
Określa, czy punkt przerwania danych jest emulowane lub wdrożonych w sprzętu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BP_RES_DATA_FLAGS {
    BP_RES_DATA_EMULATED = 0x0001
};
typedef DWORD BP_RES_DATA_FLAGS;
```

```csharp
public enum enum_BP_RES_DATA_FLAGS {
    BP_RES_DATA_EMULATED = 0x0001
};
```

## <a name="fields"></a>Pola
`BP_RES_DATA_EMULATED`\
Określa, że punkt przerwania danych jest emulowane.

## <a name="remarks"></a>Uwagi
Używany do `dwFlags` członkiem [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) struktury.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
