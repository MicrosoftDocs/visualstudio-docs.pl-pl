---
title: IDebugTypeFieldBuilder | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 165bbf6326bee67718c4c2ae44933d1b21b8252c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319794"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Reprezentuje zdolność do tworzenia pola, które reprezentuje typ.

## <a name="syntax"></a>Składnia

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest uzyskiwana z dostawca symboli.

## <a name="methods"></a>Metody
 Ten interfejs implementuje następujących metod:

|Metoda|Opis|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Tworzy obiekt, który reprezentuje typ pierwotny.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Tworzy wskaźnik do określonego typu.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll