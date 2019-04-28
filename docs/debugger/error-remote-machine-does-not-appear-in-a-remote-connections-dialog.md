---
title: 'Błąd: Komputer zdalny nie jest wyświetlana w oknie dialogowym połączeń zdalnych | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: dd194bc26574e8004894a72ce29d753cabf66a21
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850801"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Błąd: Maszyna zdalna nie jest wyświetlana w oknie dialogowym połączeń zdalnych
Jeśli komputer zdalny nie zostanie wyświetlony w oknie dialogowym połączeń zdalnych, sprawdź następujące typowe przyczyny.

 Jeśli używasz trybu zgodności zarządzanej, sprawdź w dokumentacji programu Visual Studio 2010: [Rozwiązywanie problemów z debugowaniem zdalnym — program Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Typowe przyczyny tego błędu

- Komputer zdalny jest uruchomiona na komputerze, na którym znajduje się w innej podsieci. Aby rozwiązać ten problem, ręcznie wpisać nazwę lub adres IP w oknie dialogowym kwalifikatora

- Zdalny debuger nie jest uruchomiona na komputerze zdalnym. Aby rozwiązać ten problem, uruchom zdalny debuger.

- Zapora blokuje komunikację między Visual Studio i komputera zdalnego. Aby rozwiązać ten problem, Skonfiguruj zaporę, aby umożliwić komunikowania się programu Visual Studio i zdalny debuger (msvsmon).

- Oprogramowanie antywirusowe blokuje komunikację między Visual Studio i komputera zdalnego. Aby rozwiązać ten problem, należy skonfigurować oprogramowanie antywirusowe, aby zezwolić na program Visual Studio i zdalny debuger (msvsmon), do komunikowania się.

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)