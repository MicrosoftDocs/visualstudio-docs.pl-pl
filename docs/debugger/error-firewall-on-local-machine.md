---
title: 'Błąd: Zapora na zdalnym komputerze | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 1781fef79dc9d80bae6a0484788298324e8bbd52
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963739"
---
# <a name="error-firewall-on-local-machine"></a>Błąd: Zapora na zdalnym komputerze
Nie skonfigurowano Zapora połączenia internetowego na komputerze lokalnym komputerze, na którym używasz programu Visual Studio, aby zezwolić na zdalne debugowanie. Zarządzane lub natywne zdalne debugowanie przy użyciu transportu domyślnego, należy otworzyć port TCP 135 dla ruchu modelu DCOM. Udostępnianie plików i drukarek muszą być otwarte i devenv.exe, należy dodać do listy wyjątków. Otwieranie Niektóre porty protokołu IPSEC może być konieczne także.  
  
 Aby uzyskać więcej informacji, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).