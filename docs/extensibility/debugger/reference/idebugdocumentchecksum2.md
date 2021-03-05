---
description: Reprezentuje sumę kontrolną dla dokumentu debugowania i umożliwia przekazywanie sum kontrolnych między składnikami.
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5b39f381817cd98fd94b1c746cbdccde31e0b1f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165569"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Reprezentuje sumę kontrolną dla dokumentu debugowania i umożliwia przekazywanie sum kontrolnych między składnikami.

## <a name="syntax"></a>Składnia

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs może być zaimplementowany przez dowolny składnik, który uwidacznia Interfejs [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) . Jest to jednak głównie zaimplementowane przez aparaty debugowania, aby suma kontrolna osadzona w pliku symboli (*. pdb) mogła zostać przeniesiona z powrotem do IDE i użyta podczas znajdowania źródła.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugDocumentChecksum2` .

|Metoda|Opis|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Pobiera sumę kontrolną dokumentu i identyfikator algorytmu z uwzględnieniem maksymalnej liczby bajtów do użycia.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
