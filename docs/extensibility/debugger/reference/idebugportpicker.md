---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 991480886c2c43c330ce37561d383ffdc420e214
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340366"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Reprezentuje dostosowanego interfejsu użytkownika dotyczące wybierania portu.

## <a name="syntax"></a>Składnia

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawców portu. Dostawcy portu definiuje ich selektora portu przez uwidaczniania go jako identyfikatora CLSID i wskazanie `metricPortPickerCLSID` metryki na narażonych CLSID.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugPortPicker`.

|Metoda|Opis|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Zostanie wyświetlone okno dialogowe określonego, który umożliwia użytkownikowi wybranie portu.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Ustawia dostawcę usług.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll