---
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b40129cb8623e6ea68babe2c480da4e4d4198f3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685589"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Reprezentuje sumy kontrolnej dla dokumentu debugowania i umożliwia przekazanie sumę kontrolną między składnikami.

## <a name="syntax"></a>Składnia

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs może być implementowany przez dowolny składnik, który udostępnia [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfejsu. Jednak go jest głównie implementowany przez aparaty debugowania sumy kontrolnej osadzone w pliku symboli (*.pdb) może być przekazywany z powrotem do środowiska IDE i używane przy wyszukiwaniu źródła.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugDocumentChecksum2`.

|Metoda|Opis|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Pobiera identyfikator sumy kontrolnej i algorytm dokumentu podana maksymalna liczba bajtów do użycia.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll