---
description: Użyj DIA SDK, aby uzyskać dostęp do informacji dotyczących debugowania firmy Microsoft.
title: Przegląd (zestaw SDK dostępu do interfejsu debugowania) | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c505216cd38b5321f291515794fc07ff58e8d698
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155363"
---
# <a name="overview-debug-interface-access-sdk"></a>Przegląd (Zestaw SDK dostępu do interfejsu debugowania)
Użyj DIA SDK, aby uzyskać dostęp do informacji dotyczących debugowania firmy Microsoft. DIA SDK udostępnia zestaw interfejsów API opartych na modelu COM, który eliminuje konieczność ponownego pisania kodu, gdy firma Microsoft zmieni format informacji debugowania. DIA SDK umożliwia również odczytywanie z wyboru zestawu poprzednich wersji informacji o debugowaniu znajdujących się w plikach. pdb i. dbg generowanych przez [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] wersje 5,0 i nowsze.

 Każdy interfejs w DIA SDK reprezentuje inny obiekt COM, chyba że określono inaczej. Dodatkowe interfejsy, a tym samym dodatkowe obiekty, są tworzone za pomocą jawnych zapytań, takich jak [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) lub [IDiaSession:: findChildren —](../../debugger/debug-interface-access/idiasession-findchildren.md), a nie poprzez wywoływanie `QueryInterface` istniejących wskaźników interfejsu.

## <a name="see-also"></a>Zobacz też
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
