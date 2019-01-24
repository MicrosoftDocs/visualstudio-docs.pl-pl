---
title: Przegląd (dostępu do interfejsu debugowania zestawu SDK) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7374b03da42e34e8ac3be8c7cc570769d9cfd1ff
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761066"
---
# <a name="overview-debug-interface-access-sdk"></a>Przegląd (Zestaw SDK dostępu do interfejsu debugowania)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Umożliwia dostęp do informacji debugowania programu Microsoft DIA SDK. DIA SDK zapewnia oparte na modelu COM zestawu interfejsów API, które eliminuje potrzebę ponownego wpisywania kodu zawsze, gdy Microsoft zmienia format informacji debugowania. DIA SDK umożliwia także odczytywać wybrany zestaw poprzednie wersje informacje o debugowaniu, znajduje się w plikach .pdb i .dbg, które są generowane przez [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] wersji 5.0 lub nowszy.  
  
 Każdego interfejsu w DIA SDK reprezentuje inny obiekt COM, z wyjątkiem sytuacji, w przypadku, gdy zaznaczono inaczej. Dodatkowe interfejsy, a w związku z tym dodatkowe obiekty są tworzone przez jawne kwerend, takich jak [idiadatasource::opensession —](../../debugger/debug-interface-access/idiadatasource-opensession.md) lub [idiasession::findchildren —](../../debugger/debug-interface-access/idiasession-findchildren.md), a nie przez wywoływanie `QueryInterface` na istniejące wskaźniki interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiadatasource::opensession —](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
