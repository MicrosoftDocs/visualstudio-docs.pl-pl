---
title: Zapora na komputerze lokalnym | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.localmachine
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
ms.openlocfilehash: d5f3e57bbac1d2c293c5a9f910beca5484db06cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871596"
---
# <a name="error-firewall-on-local-machine"></a>Błąd: Zapora na zdalnym komputerze
Zapora połączenia internetowego na komputerze lokalnym, na którym jest uruchomiony program Visual Studio, nie jest skonfigurowana do zezwalania na debugowanie zdalne. W przypadku zarządzanego lub natywnego debugowania zdalnego przy użyciu domyślnego transportu należy otworzyć port TCP 135 dla ruchu DCOM. Udostępnianie plików i drukarek musi być otwarte, a devenv.exe należy dodać do listy wyjątków. Może być również konieczne otworzenie niektórych portów IPSEC.

 Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).