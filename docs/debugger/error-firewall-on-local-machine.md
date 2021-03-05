---
description: Zapora połączenia internetowego na komputerze lokalnym, na którym jest uruchomiony program Visual Studio, nie jest skonfigurowana do zezwalania na debugowanie zdalne.
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
ms.openlocfilehash: bad1dcbfa2dd80ade46bd0e848e3c1f186f3c903
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146968"
---
# <a name="error-firewall-on-local-machine"></a>Błąd: Zapora na zdalnym komputerze
Zapora połączenia internetowego na komputerze lokalnym, na którym jest uruchomiony program Visual Studio, nie jest skonfigurowana do zezwalania na debugowanie zdalne. W przypadku zarządzanego lub natywnego debugowania zdalnego przy użyciu domyślnego transportu należy otworzyć port TCP 135 dla ruchu DCOM. Udostępnianie plików i drukarek musi być otwarte, a devenv.exe należy dodać do listy wyjątków. Może być również konieczne otworzenie niektórych portów IPSEC.

 Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).
