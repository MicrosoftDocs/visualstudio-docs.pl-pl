---
title: Przegląd (zestaw SDK dostępu do interfejsu debugowania) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179208"
---
# <a name="overview-debug-interface-access-sdk"></a>Przegląd (Zestaw SDK dostępu do interfejsu debugowania)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj DIA SDK, aby uzyskać dostęp do informacji dotyczących debugowania firmy Microsoft. DIA SDK udostępnia zestaw interfejsów API opartych na modelu COM, który eliminuje konieczność ponownego pisania kodu, gdy firma Microsoft zmieni format informacji debugowania. DIA SDK umożliwia również odczytywanie z wyboru zestawu poprzednich wersji informacji o debugowaniu znajdujących się w plikach. pdb i. dbg generowanych przez [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] wersje 5,0 i nowsze.  
  
 Każdy interfejs w DIA SDK reprezentuje inny obiekt COM, chyba że określono inaczej. Dodatkowe interfejsy, a tym samym dodatkowe obiekty, są tworzone za pomocą jawnych zapytań, takich jak [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) lub [IDiaSession:: findChildren —](../../debugger/debug-interface-access/idiasession-findchildren.md), a nie poprzez wywoływanie `QueryInterface` istniejących wskaźników interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
