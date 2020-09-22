---
title: Zapora bez uwierzytelniania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8548880df8c69fa59d58bf4c13f7f547ad359bd
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852722"
---
# <a name="error-firewall-no-authentication"></a>Błąd: Brak uwierzytelnienia zapory
Zapora połączenia internetowego na komputerze zdalnym nie została skonfigurowana w taki sposób, aby zezwalała na debugowanie zdalne. W przypadku zdalnego debugowania z `No Authentication` , msvsmon.exe należy dodać do listy wyjątków. Może być również konieczne otworzenie niektórych portów IPSEC.

> [!NOTE]
> Zdalny debuger jest w stanie automatycznie konfigurować zaporę systemu Windows. W przypadku korzystania z zapory innej niż Zapora systemu Windows, takiej jak Zapora oprogramowania innej firmy lub zapora sprzętowa, należy ręcznie skonfigurować zaporę, aby umożliwić zdalne debugowanie. W tym celu Zezwól na ruch na portach TCP/IP, które msvsmon.exe nasłuchuje. Domyślnie są to porty 4018 i 4019, gdzie 4018 jest używany we wszystkich systemach operacyjnych, a 4019 jest używany tylko w systemie Windows x64 do zezwalania na Debugowanie procesów x86.

 Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).