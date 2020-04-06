---
title: IDebugPortPicker | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 554ac24d7148f0d5de07779f35376b28b7ff7b07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724846"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Reprezentuje dostosowany interfejs użytkownika do wybierania portu.

## <a name="syntax"></a>Składnia

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawców portów. Dostawca portu definiuje ich selektora portów, uwidaczniając go jako `metricPortPickerCLSID` identyfikator CLSID i wskazując metrykę na narażony identyfikator CLSID.

## <a name="methods"></a>Metody
 W poniższej tabeli `IDebugPortPicker`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Wyświetla określone okno dialogowe, które umożliwia użytkownikowi wybranie portu.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Ustawia dostawcę usług.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
