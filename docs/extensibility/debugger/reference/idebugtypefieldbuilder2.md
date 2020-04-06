---
title: IDebugTypeFieldBuilder2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed34284e373a7d96761aabe5a7f179367649bc0f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718304"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Rozszerza **IDebugTypeFieldBuilder,** aby móc tworzyć typy tablic.

## <a name="syntax"></a>Składnia

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs można uzyskać od dostawcy symbolu.

## <a name="methods"></a>Metody
 Oprócz metod w interfejsie [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Tworzy tablicę określonego typu i rozmiaru.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
