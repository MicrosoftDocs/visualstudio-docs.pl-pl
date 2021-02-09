---
title: IDebugGenericFieldDefinition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ff7c28a30ccab43629636f7dcd9391a669a376ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884796"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Reprezentuje definicję pola dla ogólnego typu kodu zarządzanego.

## <a name="syntax"></a>Składnia

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>Metody
 Ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Tworzy wystąpienie pola z tablicą argumentów typu.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Pobiera parametry typu z określoną liczbą parametrów.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Pobiera liczbę parametrów typu skojarzonych z polem ogólnym.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
