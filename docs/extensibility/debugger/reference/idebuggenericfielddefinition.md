---
title: IDebugGenericFieldDefinition | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2887333789a9a4eae89a9f3f7538cf5b29ba02e7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351249"
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