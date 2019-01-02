---
title: IDebugProperty3::CreateObjectID | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6fab6a75885dba8ddfd952ec3680e2c44b87312
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855825"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Tworzy unikatowy identyfikator dla tej właściwości, aby upewnić się, że jest ona unikatowa wśród wszystkich innych właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana, gdy Menedżer debugowania sesji chce mieć pewność, ta właściwość jest unikatowo identyfikowana przez inne właściwości. Aparat debugowania (DE) obsługuje tę metodę, chyba że właściwości, które zajmuje się on już unikatowo zidentyfikować. Jeśli DE nie obsługuje tej metody, zwraca `E_NOTIMPL`.  
  
 Wszelkie Unikatowy identyfikator utworzony za pomocą `CreateObjectID` jest niszczony, kiedy [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) wywoływana jest metoda; to również sygnalizuje koniec potrzebę unikatowo identyfikujący tę właściwość.  
  
> [!NOTE]
>  Nie istnieje metoda do pobrania to unikatowy identyfikator, więc DE można zrobić, niezależnie od rodzaju chce uzyskać unikatowe identyfikatory podczas `CreateObjectID` metoda jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)