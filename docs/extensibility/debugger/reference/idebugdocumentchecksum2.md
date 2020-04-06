---
title: IDebugDocumentChecksum2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03cfb29cc54a2f0ab18bce3ec0761cfab62e20df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731894"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Reprezentuje sumę kontrolną dla dokumentu debugowania i umożliwia przekazywanie sumy kontrolnej między składnikami.

## <a name="syntax"></a>Składnia

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs może być zaimplementowany przez dowolny składnik, który udostępnia interfejs [IDebugDocumentContext2.](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Jednak jest on implementowany głównie przez aparaty debugowania, dzięki czemu suma kontrolna osadzona w pliku symbolu (*.pdb) może być przekazywana z powrotem do IDE i używana podczas znajdowania źródła.

## <a name="methods"></a>Metody
 W poniższej tabeli `IDebugDocumentChecksum2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Pobiera sumę kontrolną dokumentu i identyfikator algorytmu, biorąc pod uwagę maksymalną liczbę bajtów do użycia.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
