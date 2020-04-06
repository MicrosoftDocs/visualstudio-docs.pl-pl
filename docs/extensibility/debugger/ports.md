---
title: Porty | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b42e7fa97c12afa07923e99d8b084840ee7ccad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738300"
---
# <a name="ports"></a>Porty
W architekturze debugera *port:*

- Jest kontenerem dla zestawu procesów uruchomionych na serwerze. Na przykład port może reprezentować połączenie z urządzeniem z systemem Windows CE za pomocą kabla szeregowego lub do sieciowego komputera innego niż DCOM. Jeden specjalny port, zwany portem lokalnym, zawiera wszystkie procesy uruchomione na komputerze lokalnym.

- Może identyfikować się po nazwie lub identyfikatorze.

- Można wyliczyć wszystkie procesy uruchomione na porcie i uruchomić i zakończyć te procesy.

- Jest reprezentowany przez interfejs [IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) który jest tworzony przez przekazanie argumentu [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) do [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dostarcza domyślny port, który obsługuje wszystkie procesy oparte na systemie Windows, zarówno macierzyste, jak i zarządzane. Port niestandardowy musi być skonfigurowany dla połączeń z urządzeniami zewnętrznymi, które nie są oparte na systemie Windows. Aby dostarczyć takie porty niestandardowe, należy również skonfigurować niestandardowego dostawcę portów.

## <a name="see-also"></a>Zobacz też
- [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Procesów](../../extensibility/debugger/processes.md)
- [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
