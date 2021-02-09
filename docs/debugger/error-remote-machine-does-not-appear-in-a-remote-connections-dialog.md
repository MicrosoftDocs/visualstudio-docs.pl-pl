---
title: Maszyna zdalna nie jest wyświetlana w oknie dialogowym połączenia zdalne | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: be39d733b2e5fe83fa9f7e2241c7de06980bb583
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871372"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Błąd: Komputer zdalny nie jest wyświetlany w oknie dialogowym połączeń zdalnych
Jeśli maszyna zdalna nie jest wyświetlana w oknie dialogowym połączenia zdalne, należy sprawdzić następujące typowe przyczyny.

 Jeśli używasz zarządzanego trybu zgodności, zapoznaj się z dokumentacją programu Visual Studio 2010: [Rozwiązywanie problemów z debugowaniem zdalnym — Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Typowe przyczyny tego błędu

- Maszyna zdalna jest uruchomiona na komputerze znajdującym się w innej podsieci. Aby rozwiązać ten problem, ręcznie wpisz nazwę lub adres IP komputera w oknie dialogowym kwalifikator

- Zdalny debuger nie jest uruchomiony na komputerze zdalnym. Aby rozwiązać ten problem, uruchom zdalny debuger.

- Zapora blokuje komunikację między programem Visual Studio i komputerem zdalnym. Aby rozwiązać ten problem, należy skonfigurować zaporę tak, aby zezwalała na komunikację programu Visual Studio i zdalnego debugera (msvsmon).

- Oprogramowanie antywirusowe blokuje komunikację między programem Visual Studio i komputerem zdalnym. Aby rozwiązać ten problem, Skonfiguruj oprogramowanie antywirusowe, aby umożliwić komunikację programu Visual Studio i zdalnego debugera (msvsmon).

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)