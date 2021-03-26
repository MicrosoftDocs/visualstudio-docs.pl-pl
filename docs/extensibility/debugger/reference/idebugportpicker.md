---
description: Reprezentuje dostosowany interfejs użytkownika do wybierania portu.
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8390c8a055a9c919bb1a35d8f3288fc810e5329d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072250"
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
