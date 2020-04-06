---
title: IDebugProperty2::GetExtendedInfo | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34d6cd880ccae520bf000ad01b52223857f4f10f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721491"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Pobiera rozszerzone informacje dla właściwości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetExtendedInfo ( 
   REFGUID* guidExtendedInfo,
   VARIANT* pExtendedInfo
);
```

```csharp
int GetExtendedInfo ( 
   ref Guid guidExtendedInfo,
   out object pExtendedInfo
);
```

## <a name="parameters"></a>Parametry
`guidExtendedInfo`\
[w] Identyfikator GUID określający typ rozszerzonych informacji do pobrania. Zobacz Uwagi, aby uzyskać szczegółowe informacje.

`pExtendedInfo`\
[na zewnątrz] Zwraca `VARIANT` (C++) lub obiekt (C#), który może służyć do pobierania informacji o właściwości rozszerzonej. Na przykład ten parametr `IUnknown` może zwrócić interfejs, który może być wyszukiwany dla interfejsu [IDebugDocumentText2.](../../../extensibility/debugger/reference/idebugdocumenttext2.md) Zobacz Uwagi, aby uzyskać szczegółowe informacje.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Zwraca, `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` jeśli nie ma żadnych rozszerzonych informacji do pobrania.

## <a name="remarks"></a>Uwagi
 Ta metoda istnieje w celu pobierania informacji, które nie nadają się do pobierania przez wywołanie [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody.

 Następujące identyfikatory GUID są zazwyczaj rozpoznawane przez tę metodę (wartości GUID są określone dla języka C#, ponieważ nazwa nie jest dostępna w żadnym zestawie). Dodatkowe identyfikatory GUID mogą być tworzone do użytku wewnętrznego.

|Nazwa|Identyfikator GUID|Opis|
|----------|----------|-----------------|
|guidDocument (GuidDocument)|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Zwraca `IUnknown` interfejs do dokumentu. Zazwyczaj interfejs [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) można uzyskać z `IUnknown` tego interfejsu.|
|guidCodeContext (guidCodeContext)|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Zwraca `IUnknown` interfejs do kontekstu dokumentu. Zazwyczaj interfejs [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) można uzyskać z `IUnknown` tego interfejsu.|
|guidCustomViewerSupportowane|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Zwraca ciąg zawierający CLSID przeglądarki niestandardowej, zazwyczaj implementowane przez oceniającego wyrażenie.|
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Zwraca numer 32-bitowy reprezentujący żądany numer gniazda, jeśli ta właściwość reprezentuje adres lokalny kodu zarządzanego.|
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Zwraca ciąg zawierający podpis zmiennej skojarzonej z obiektem właściwości.|

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
