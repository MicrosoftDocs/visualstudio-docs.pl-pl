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
ms.openlocfilehash: 87a1813410a092ced335f37b9df4cf6547ca1cc3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851043"
---
# <a name="error-firewall-on-local-machine"></a>Błąd: Zapora na zdalnym komputerze
Nie skonfigurowano Zapora połączenia internetowego na komputerze lokalnym komputerze, na którym używasz programu Visual Studio, aby zezwolić na zdalne debugowanie. Zarządzane lub natywne zdalne debugowanie przy użyciu transportu domyślnego, należy otworzyć port TCP 135 dla ruchu modelu DCOM. Udostępnianie plików i drukarek muszą być otwarte i devenv.exe, należy dodać do listy wyjątków. Otwieranie Niektóre porty protokołu IPSEC może być konieczne także.

 Aby uzyskać więcej informacji, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).