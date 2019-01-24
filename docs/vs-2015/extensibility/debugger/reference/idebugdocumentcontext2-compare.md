---
title: IDebugDocumentContext2::Compare | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f09684c5e9587c6e3bb631674e009d0b36f4fc5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767696"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Porównuje ten kontekst dokumentu do danej tablicy kontekstów dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
