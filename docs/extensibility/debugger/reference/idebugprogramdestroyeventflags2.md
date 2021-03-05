---
description: Umożliwia aparatowi debugowania przesłonięcie domyślnego zachowania interfejsu użytkownika programu Visual Studio po zakończeniu sesji debugowania.
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02b2d934c2a556d3556d494368145e52a8c97394
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168195"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Umożliwia aparatowi debugowania przesłonięcie domyślnego zachowania [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika po zakończeniu sesji debugowania.

## <a name="syntax"></a>Składnia

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez aparaty debugowania. Jest to przydatne w przypadku hostów, które mogą tworzyć i zniszczyć wiele programów w okresie istnienia procesu.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugProgramDestroyEventFlags2` .

|Metoda|Opis|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Pobiera flagi niszczenia programów.|

## <a name="remarks"></a>Uwagi
 Domyślnym zachowaniem [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika jest powrót do trybu projektowania po wysłaniu przez wszystkie programy zdarzenia zniszczenia programu. Ten interfejs umożliwia aparatowi debugowania zmianę tego zachowania.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
