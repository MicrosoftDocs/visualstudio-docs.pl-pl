---
title: Ports | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0da318ac0845cdfe074847eecadcfb12138e447
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925466"
---
# <a name="ports"></a>Porty
W architekturze debugera *portu*:

- Kontener dla zestawu procesów działa na serwerze. Na przykład port może reprezentować połączenie urządzenia z systemem Windows CE, za pomocą kabla szeregowego lub maszyną sieciowych bez DCOM. Jeden port specjalny port lokalny, nazywany zawiera wszystkie procesy, które są uruchomione na komputerze lokalnym.

- Można zidentyfikować sama nazwa lub identyfikator.

- Można wyliczyć wszystkie procesy uruchomione na porcie uruchomienie i zakończenie tych procesów.

- Jest reprezentowany przez [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfejs, który jest tworzony przez przekazanie [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argument [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostarcza domyślnego portu, obsługująca wszystkich oparte na Windows procesów, natywnych i zarządzanych. Port niestandardowy można ustawić dla połączeń przy użyciu urządzeń zewnętrznych, które nie są oparte na Windows. Podać takie niestandardowych portów, należy skonfigurować dostawcy niestandardowego portu.

## <a name="see-also"></a>Zobacz także
- [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Procesy](../../extensibility/debugger/processes.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)