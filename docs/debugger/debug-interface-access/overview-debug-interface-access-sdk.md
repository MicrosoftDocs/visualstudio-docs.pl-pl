---
title: Przegląd (dostępu do interfejsu debugowania zestawu SDK) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e459d4429d712a9ca4c245d581c6be3578711cd6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855111"
---
# <a name="overview-debug-interface-access-sdk"></a>Przegląd (Zestaw SDK dostępu do interfejsu debugowania)
Umożliwia dostęp do informacji debugowania programu Microsoft DIA SDK. DIA SDK zapewnia oparte na modelu COM zestawu interfejsów API, które eliminuje potrzebę ponownego wpisywania kodu zawsze, gdy Microsoft zmienia format informacji debugowania. DIA SDK umożliwia także odczytywać wybrany zestaw poprzednie wersje informacje o debugowaniu, znajduje się w plikach .pdb i .dbg, które są generowane przez [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] wersji 5.0 lub nowszy.

 Każdego interfejsu w DIA SDK reprezentuje inny obiekt COM, z wyjątkiem sytuacji, w przypadku, gdy zaznaczono inaczej. Dodatkowe interfejsy, a w związku z tym dodatkowe obiekty są tworzone przez jawne kwerend, takich jak [idiadatasource::opensession —](../../debugger/debug-interface-access/idiadatasource-opensession.md) lub [idiasession::findchildren —](../../debugger/debug-interface-access/idiasession-findchildren.md), a nie przez wywoływanie `QueryInterface` na istniejące wskaźniki interfejsu.

## <a name="see-also"></a>Zobacz też
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)