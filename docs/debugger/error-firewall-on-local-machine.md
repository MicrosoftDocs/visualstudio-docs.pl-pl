---
title: Błąd — Zapora na komputerze lokalnym | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 115546a0fd3a9aad804391816ce8bac88429d0ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460755"
---
# <a name="error-firewall-on-local-machine"></a>Błąd: Zapora na zdalnym komputerze
Zapora połączenia internetowego na komputerze lokalnym, na którym jest uruchomiony program Visual Studio, nie jest skonfigurowana do zezwalania na debugowanie zdalne. W przypadku zarządzanego lub natywnego debugowania zdalnego przy użyciu domyślnego transportu należy otworzyć port TCP 135 dla ruchu DCOM. Udostępnianie plików i drukarek musi być otwarte, a devenv.exe należy dodać do listy wyjątków. Może być również konieczne otworzenie niektórych portów IPSEC.

 Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).