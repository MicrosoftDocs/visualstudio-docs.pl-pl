---
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81532e2616eefb9cb584eae1a70371fd2f963be1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718397"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Reprezentuje możliwość utworzenia pola, które reprezentuje typ.

## <a name="syntax"></a>Składnia

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest uzyskiwany od dostawcy symboli.

## <a name="methods"></a>Metody
 Ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Tworzy obiekt, który reprezentuje typ pierwotny.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Tworzy wskaźnik do określonego typu.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
