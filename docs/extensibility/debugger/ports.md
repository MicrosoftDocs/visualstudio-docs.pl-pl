---
title: Porty | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738300"
---
# <a name="ports"></a>Porty
W architekturze debugera *port*:

- Jest kontenerem zestawu procesów uruchomionych na serwerze. Na przykład port może reprezentować połączenie z urządzeniem opartym na Windows CE przez kabel szeregowy lub komputer sieciowy niebędący modelem DCOM. Jeden port specjalny, zwany portem lokalnym, zawiera wszystkie procesy uruchomione na komputerze lokalnym.

- Może identyfikować siebie według nazwy lub identyfikatora.

- Program może wyliczyć wszystkie procesy działające na porcie i uruchamiać i kończyć te procesy.

- Jest reprezentowany przez interfejs [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , który jest tworzony przez przekazanie argumentu [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) do [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostarcza domyślny port obsługujący wszystkie procesy oparte na systemie Windows, zarówno natywne, jak i zarządzane. Port niestandardowy musi być skonfigurowany do połączeń z urządzeniami zewnętrznymi, które nie są oparte na systemie Windows. Aby określić takie porty niestandardowe, należy również skonfigurować niestandardowego dostawcę portu.

## <a name="see-also"></a>Zobacz też
- [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Procesy](../../extensibility/debugger/processes.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
