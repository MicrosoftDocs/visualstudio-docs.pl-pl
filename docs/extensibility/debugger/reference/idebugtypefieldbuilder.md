---
description: Reprezentuje możliwość utworzenia pola, które reprezentuje typ.
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1bc4f58470792cac8bdb68ede4ddf37567bac208
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223111"
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
