---
description: Włącza interfejs użytkownika programu Visual Studio do wyświetlania tekstu w sekcji Informacje o transporcie w oknie dialogowym Dołącz do procesu.
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dba3cd07bb84843ff4d2531cdde63ab9e671f961
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071925"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Włącza [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejs użytkownika do wyświetlania tekstu w sekcji **Informacje o transporcie** okna dialogowego **Dołącz do procesu** .

## <a name="syntax"></a>Składnia

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawców portów.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugPortSupplierDescription2` .

|Metoda|Opis|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Pobiera metadane opisu i opisu dostawcy portów.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
