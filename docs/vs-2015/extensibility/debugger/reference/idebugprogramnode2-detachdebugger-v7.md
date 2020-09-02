---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c60bc42895a0527f1638dada5a28a1631314e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64806613"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Przestarzałe. NIE NALEŻY UŻYWAĆ.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja powinna zawsze zwrócić `E_NOTIMPL` .  
  
## <a name="remarks"></a>Uwagi  
  
> [!WARNING]
> Począwszy od programu [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] , ta metoda nie jest już używana i zawsze powinna zwracać `E_NOTIMPL` .  
  
 Ta metoda jest wywoływana, gdy debuger nieoczekiwanie kończy pracę. Po wywołaniu tej metody DE powinien wznowić program tak, jakby został odłączony przez użytkownika. Nie należy wysyłać więcej zdarzeń debugowania. Program powinien znajdować się w stanie, w którym jest możliwy do dołączenia z innego wystąpienia debugera.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
