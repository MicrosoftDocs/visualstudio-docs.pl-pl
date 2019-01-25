---
title: Ports | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760797"
---
# <a name="ports"></a>Porty
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pod względem architektury debugera **portu**:  
  
- Kontener dla zestawu procesów działa na serwerze. Na przykład port może reprezentować połączenie urządzenia z systemem Windows CE, za pomocą kabla szeregowego lub na maszynie sieciowych bez DCOM. Jeden port specjalny port lokalny, nazywany zawiera wszystkie procesy, które są uruchomione na komputerze lokalnym.  
  
- Można zidentyfikować sama nazwa lub identyfikator.  
  
- Można wyliczyć wszystkie procesy uruchomione na porcie uruchomienie i zakończenie tych procesów.  
  
- Jest reprezentowany przez [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfejs, który jest tworzony przez przekazanie [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argument [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dostarcza domyślnego portu, obsługująca wszystkich oparte na Windows procesów, natywnych i zarządzanych. Port niestandardowy, należy zaimplementować dla połączeń przy użyciu urządzeń zewnętrznych, które nie są oparte na Windows. Podać takie niestandardowych portów, dostawca niestandardowy port musi również można zaimplementować.  
  
## <a name="see-also"></a>Zobacz też  
 [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Procesy](../../extensibility/debugger/processes.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
