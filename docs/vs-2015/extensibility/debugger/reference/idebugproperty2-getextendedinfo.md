---
title: 'IDebugProperty2:: GetExtendedInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74810aab2f47a36c716891fd45b7424eb737b142
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164973"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera rozszerzone informacje dla właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametry  
 `guidExtendedInfo`  
 podczas Identyfikator GUID, który określa typ rozszerzonych informacji do pobrania. Aby uzyskać szczegółowe informacje, zobacz uwagi.  
  
 `pExtendedInfo`  
 określoną Zwraca `VARIANT` (C++) lub obiekt (C#), którego można użyć do pobrania informacji o właściwości rozszerzonej. Na przykład ten parametr może zwrócić `IUnknown` interfejs, który może być badany dla interfejsu [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) . Aby uzyskać szczegółowe informacje, zobacz uwagi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` informację o tym, czy nie ma informacji rozszerzonych do pobrania.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda istnieje na potrzeby pobierania informacji, które nie dają się do pobrania przez wywołanie metody [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .  
  
 Następujące identyfikatory GUID są zwykle rozpoznawane przez tę metodę (wartości identyfikatora GUID są określone dla języka C#, ponieważ nazwa nie jest dostępna w żadnym zestawie). Dodatkowe identyfikatory GUID można utworzyć do użytku wewnętrznego.  
  
|Nazwa|GUID|Opis|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Zwraca `IUnknown` interfejs do dokumentu. Zazwyczaj Interfejs [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) można uzyskać z tego `IUnknown` interfejsu.|  
|guidCodeContext|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Zwraca `IUnknown` interfejs do kontekstu dokumentu. Zazwyczaj Interfejs [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) można uzyskać z tego `IUnknown` interfejsu.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Zwraca ciąg zawierający identyfikator CLSID niestandardowej przeglądarki, zazwyczaj zaimplementowany przez ewaluatora wyrażeń.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Zwraca 32-bitową liczbę reprezentującą żądany numer gniazda, jeśli ta właściwość reprezentuje adres lokalny w kodzie zarządzanym.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Zwraca ciąg zawierający sygnaturę zmiennej skojarzonej z obiektem właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
