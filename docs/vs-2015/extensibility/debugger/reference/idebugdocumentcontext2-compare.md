---
title: 'IDebugDocumentContext2:: Compare | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189414"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Porównuje ten kontekst dokumentu z daną tablicą kontekstów dokumentów.  
  
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
 podczas Wartość z wyliczenia [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) , która określa typ porównania.  
  
 `rgpDocContextSet`  
 podczas Tablica obiektów [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , które reprezentują konteksty dokumentu porównywane z.  
  
 `dwDocContextSetLen`  
 podczas Długość tablicy kontekstów dokumentu do porównania.  
  
 `pdwDocContext`  
 określoną Zwraca indeks do `rgpDocContextSet` tablicy pierwszego kontekstu dokumentu, który spełnia porównanie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` Czy znaleziono dopasowanie. Zwraca wartość, `S_FALSE` Jeśli nie znaleziono żadnego dopasowania. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Obiekty [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , które są przesyłane w tablicy, muszą być zaimplementowane przez ten sam aparat debugowania, który implementuje `IDebugDocumentContext2` obiekt wywoływany; w przeciwnym razie porównanie jest nieprawidłowe.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
