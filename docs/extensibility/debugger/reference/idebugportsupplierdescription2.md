---
title: IDebugPortSupplierDescription2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae6491628888f682d61c94ae618bfad72837c845
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339881"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Włącza [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika, aby wyświetlić tekst wewnątrz **transportowania informacji** części **dołączyć do procesu** okno dialogowe.

## <a name="syntax"></a>Składnia

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawców portu.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugPortSupplierDescription2`.

|Metoda|Opis|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Pobiera opis i metadane opisu dla dostawcy portu.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll