---
title: 'IDebugProperty3:: setobjectid | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0035faad9078acd70886d597f039c0d8de5ee12f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788328"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana, gdy Menedżer debugowania sesji chce, aby upewnić się, że ta właściwość jednoznacznie identyfikuje wszystkie inne właściwości. Aparat debugowania (DE) obsługuje tę metodę, chyba że właściwości, których dotyczy, są już jednoznacznie zidentyfikowane. Jeśli DE nie obsługuje tej metody, zwraca `E_NOTIMPL` .  
  
 Każdy unikatowy identyfikator utworzony za pomocą `CreateObjectID` jest niszczony, gdy wywoływana jest metoda [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) ; to również sygnalizuje koniec potrzeby unikatowego identyfikowania tej właściwości.  
  
> [!NOTE]
> Nie ma metody do pobrania tego unikatowego identyfikatora, w związku z czym w przypadku wywołania metody DE może to zrobić `CreateObjectID` .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
