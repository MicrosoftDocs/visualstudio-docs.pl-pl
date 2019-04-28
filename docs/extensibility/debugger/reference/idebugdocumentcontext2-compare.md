---
title: IDebugDocumentContext2::Compare | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1416092661ee26bff773ea1a439c241a0f5c5fc6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62921518"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Porównuje ten kontekst dokumentu do danej tablicy kontekstów dokumentu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

#### <a name="parameters"></a>Parametry
 `compare`

 [in] Wartość z zakresu od [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) wyliczenie, który określa typ porównania.

 `rgpDocContextSet`

 [in] Tablica [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) obiekty reprezentujące kontekstów dokumentu, którą jest porównywany.

 `dwDocContextSetLen`

 [in] Długość tablicy kontekstów dokumentu do porównania.

 `pdwDocContext`

 [out] Zwraca indeks do `rgpDocContextSet` tablicy pierwszy kontekst dokumentu, który spełnia porównanie.

## <a name="return-value"></a>Wartość zwracana
 Zwraca `S_OK` Jeśli znaleziono dopasowanie. Zwraca `S_FALSE` Jeżeli nie znaleziono dopasowania. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) obiekty, które są przekazywane w tablicy musi być implementowana przez tego samego aparatu debugowania, który implementuje `IDebugDocumentContext2` obiektu wywołanego w przeciwnym razie wynik porównania jest nieprawidłowy.

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)