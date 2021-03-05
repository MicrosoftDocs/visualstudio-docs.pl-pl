---
description: Rozszerza IDebugTypeFieldBuilder, aby można było tworzyć typy tablic.
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e73642024cb379e804559ba8dd55eb44722cf580
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223007"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Rozszerza **IDebugTypeFieldBuilder** , aby można było tworzyć typy tablic.

## <a name="syntax"></a>Składnia

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs można uzyskać od dostawcy symboli.

## <a name="methods"></a>Metody
 Oprócz metod w interfejsie [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Tworzy tablicę określonego typu i rozmiaru.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
