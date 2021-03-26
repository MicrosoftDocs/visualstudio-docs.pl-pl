---
description: Reprezentuje możliwość utworzenia pola, które reprezentuje typ.
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8bf2199766cd0e78940c38e8441fe9fb0ab3c320
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083495"
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
