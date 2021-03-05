---
description: Zapora połączenia internetowego na komputerze zdalnym nie została skonfigurowana w taki sposób, aby zezwalała na debugowanie zdalne.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2bb46b09af4f87ac93fd7001ff1de02a782ae263
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146993"
---
# <a name="error-firewall-no-authentication"></a>Błąd: Brak uwierzytelnienia zapory
Zapora połączenia internetowego na komputerze zdalnym nie została skonfigurowana w taki sposób, aby zezwalała na debugowanie zdalne. W przypadku zdalnego debugowania z `No Authentication` , msvsmon.exe należy dodać do listy wyjątków. Może być również konieczne otworzenie niektórych portów IPSEC.

> [!NOTE]
> Zdalny debuger jest w stanie automatycznie konfigurować zaporę systemu Windows. W przypadku korzystania z zapory innej niż Zapora systemu Windows, takiej jak Zapora oprogramowania innej firmy lub zapora sprzętowa, należy ręcznie skonfigurować zaporę, aby umożliwić zdalne debugowanie. W tym celu Zezwól na ruch na portach TCP/IP, które msvsmon.exe nasłuchuje. Domyślnie są to porty 4018 i 4019, gdzie 4018 jest używany we wszystkich systemach operacyjnych, a 4019 jest używany tylko w systemie Windows x64 do zezwalania na Debugowanie procesów x86.

 Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).
