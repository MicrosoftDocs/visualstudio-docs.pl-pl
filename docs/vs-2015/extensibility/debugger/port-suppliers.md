---
title: Dostawcy portów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e90871927c30399dea4691381baa749db2b3e8bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153706"
---
# <a name="port-suppliers"></a>Dostawcy portów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W odniesieniu do architektury debugera **dostawca portu**:  
  
- Jest zawarty na serwerze i udostępnia porty na żądanie do tego serwera.  
  
- Może dodawać i usuwać porty z serwera zawierającego.  
  
- Program może wyliczyć wszystkie porty dostarczone do serwera.  
  
- Jest reprezentowany przez interfejs [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , który jest zarejestrowany w programie Visual Studio za pomocą rejestru. Ten interfejs można uzyskać, wywołując [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zapewnia domyślnego dostawcę portu i domyślny port. Jeśli należy zaimplementować port niestandardowy, należy również zaimplementować niestandardowego dostawcę portu w celu dostarczenia tych portów niestandardowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Serwerem](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Np](../../extensibility/debugger/ports.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
