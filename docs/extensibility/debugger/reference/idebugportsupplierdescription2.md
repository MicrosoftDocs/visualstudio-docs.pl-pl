---
description: Włącza interfejs użytkownika programu Visual Studio do wyświetlania tekstu w sekcji Informacje o transporcie w oknie dialogowym Dołącz do procesu.
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c3cd8d6fbeaf020ea772c9bd5cae783b6e8d127
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150383"
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
