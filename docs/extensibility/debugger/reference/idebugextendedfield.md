---
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1287af4b1afb328e3b843bae0ae93284fe8386c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915511"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Rozszerza typy pól, które są dostępne do obsługi typów ogólnych w kodzie zarządzanym.

## <a name="syntax"></a>Składnia

```
IDebugExtendedField : IDebugField
```

## <a name="methods"></a>Metody
 Oprócz metod interfejsu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Pobiera określony rodzaj pola rozszerzonego.|
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Określa, czy pole reprezentuje typ zamknięty.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
