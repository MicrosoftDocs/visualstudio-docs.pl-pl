---
title: Przegląd (zestaw SDK dostępu do interfejsu debugowania) | Microsoft Docs
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
ms.openlocfilehash: 1e4269c620247f256d2cfae2e84b76ff60fcf9ba
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738604"
---
# <a name="overview-debug-interface-access-sdk"></a>Przegląd (Zestaw SDK dostępu do interfejsu debugowania)
Użyj DIA SDK, aby uzyskać dostęp do informacji dotyczących debugowania firmy Microsoft. DIA SDK udostępnia zestaw interfejsów API opartych na modelu COM, który eliminuje konieczność ponownego pisania kodu, gdy firma Microsoft zmieni format informacji debugowania. DIA SDK umożliwia również odczytywanie z wyboru zestawu wcześniejszych wersji informacji debugowania, znajdujących się w plikach. pdb i. dbg generowanych przez [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] wersji 5,0 i nowszych.

 Każdy interfejs w DIA SDK reprezentuje inny obiekt COM, chyba że określono inaczej. Dodatkowe interfejsy, a tym samym dodatkowe obiekty, są tworzone za pomocą zapytań jawnych, takich jak [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) lub [IDiaSession:: findChildren —](../../debugger/debug-interface-access/idiasession-findchildren.md), a nie wywołując `QueryInterface` na istniejących wskaźnikach interfejsu.

## <a name="see-also"></a>Zobacz także
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)