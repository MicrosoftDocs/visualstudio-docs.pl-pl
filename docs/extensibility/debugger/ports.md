---
title: Porty | Microsoft Docs
description: W tym artykule opisano definicję i rolę portu w architekturze debugera w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e53b2b804433f7e9450f34dac5b21e45710cd71c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900775"
---
# <a name="ports"></a>Porty
W architekturze debugera *port*:

- Jest kontenerem dla zestawu procesów uruchomionych na serwerze. Na przykład port może reprezentować połączenie z urządzeniem opartym na Windows CE za pomocą kabla szeregowego lub z sieciowym urządzeniem niepowiązywistym z systemem DCOM. Jeden specjalny port, nazywany portem lokalnym, zawiera wszystkie procesy uruchomione na maszynie lokalnej.

- Może identyfikować się według nazwy lub identyfikatora.

- Może wyliczać wszystkie procesy uruchomione na porcie oraz uruchamiać i kończyć te procesy.

- Jest reprezentowany przez [interfejs IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) który jest tworzony przez przekazanie argumentu [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) do [funkcji AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostarcza domyślny port obsługujący wszystkie procesy oparte na systemie Windows, zarówno natywne, jak i zarządzane. Dla połączeń z urządzeniami zewnętrznymi, które nie są oparte na systemie Windows, należy skonfigurować port niestandardowy. Aby dostarczyć takie porty niestandardowe, należy również skonfigurować niestandardowego dostawcę portów.

## <a name="see-also"></a>Zobacz też
- [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Procesy](../../extensibility/debugger/processes.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
