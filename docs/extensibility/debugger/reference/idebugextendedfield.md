---
description: Rozszerza typy pól, które są dostępne do obsługi typów ogólnych w kodzie zarządzanym.
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8214703fb1ffc05d3f58f8348870a8505cc8f59
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077190"
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
