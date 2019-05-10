---
title: IDebugGenericFieldDefinition | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea197cf5b6207117007c5d6d95b742e3a892223b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919153"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Reprezentuje definicję pola dla kodu zarządzanego typu ogólnego.

## <a name="syntax"></a>Składnia

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>Metody
 Ten interfejs implementuje następujących metod:

|Metoda|Opis|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Tworzy wystąpienie pola, biorąc pod uwagę tablicę argumentów typu.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Pobiera parametry typu, biorąc pod uwagę liczbę parametrów.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Pobiera liczbę parametrów typu skojarzone z nim ogólne.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll