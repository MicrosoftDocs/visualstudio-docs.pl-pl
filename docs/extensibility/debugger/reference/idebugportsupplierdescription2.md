---
title: IDebugPortSupplierDescription2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69853e34788a2f24afe183dfbb7070e48f14aa46
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724357"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Umożliwia [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsowi użytkownika wyświetlanie tekstu w sekcji **Informacje o transporcie** w oknie dialogowym **Dołączanie do procesu.**

## <a name="syntax"></a>Składnia

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawców portów.

## <a name="methods"></a>Metody
 W poniższej tabeli `IDebugPortSupplierDescription2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Pobiera metadane opisu i opisu dla dostawcy portu.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
