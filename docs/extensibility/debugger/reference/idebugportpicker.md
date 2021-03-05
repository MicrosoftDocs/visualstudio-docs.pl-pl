---
description: Reprezentuje dostosowany interfejs użytkownika do wybierania portu.
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 335a954603505d064f32e8f901ce428d6cb8dfa1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142639"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Reprezentuje dostosowany interfejs użytkownika do wybierania portu.

## <a name="syntax"></a>Składnia

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawców portów. Dostawca portu definiuje swój selektor portów przez udostępnienie go jako identyfikator CLSID i wskazanie `metricPortPickerCLSID` metryki na uwidocznionym identyfikatorze CLSID.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugPortPicker` .

|Metoda|Opis|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Wyświetla określone okno dialogowe, które umożliwia użytkownikowi wybranie portu.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Ustawia dostawcę usług.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
