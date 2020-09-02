---
title: Porty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73003e00fef5c37db4a702e7a4a1121600673844
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153690"
---
# <a name="ports"></a>Porty
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W zakresie architektury debugera, **portu**:  
  
- Jest kontenerem zestawu procesów uruchomionych na serwerze. Na przykład port może reprezentować połączenie z urządzeniem opartym na Windows CE przez kabel szeregowy lub komputer sieciowy niebędący modelem DCOM. Jeden port specjalny, zwany portem lokalnym, zawiera wszystkie procesy uruchomione na komputerze lokalnym.  
  
- Może identyfikować siebie według nazwy lub identyfikatora.  
  
- Program może wyliczyć wszystkie procesy działające na porcie i uruchamiać i kończyć te procesy.  
  
- Jest reprezentowany przez interfejs [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , który jest tworzony przez przekazanie argumentu [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) do [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dostarcza domyślny port, który obsługuje wszystkie procesy oparte na systemie Windows, natywne i zarządzane. Należy zaimplementować port niestandardowy dla połączeń z urządzeniami zewnętrznymi, które nie są oparte na systemie Windows. Aby określić takie porty niestandardowe, należy również zaimplementować niestandardowego dostawcę portu.  
  
## <a name="see-also"></a>Zobacz też  
 [Serwerem](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Przetwarzające](../../extensibility/debugger/processes.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
