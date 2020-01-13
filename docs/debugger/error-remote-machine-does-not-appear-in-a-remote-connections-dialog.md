---
title: 'Błąd: maszyna zdalna nie jest wyświetlana w oknie dialogowym połączeń zdalnych | Microsoft Docs'
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
ms.openlocfilehash: dd46d2164ccb3cd26831160235b992d699229e2c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916183"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Błąd: maszyna zdalna nie jest wyświetlana w oknie dialogowym połączeń zdalnych
Jeśli maszyna zdalna nie jest wyświetlana w oknie dialogowym połączenia zdalne, należy sprawdzić następujące typowe przyczyny.

 Jeśli używasz zarządzanego trybu zgodności, zapoznaj się z dokumentacją programu Visual Studio 2010: [Rozwiązywanie problemów z debugowaniem zdalnym — Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Typowe przyczyny tego błędu

- Maszyna zdalna jest uruchomiona na komputerze znajdującym się w innej podsieci. Aby rozwiązać ten problem, ręcznie wpisz nazwę lub adres IP komputera w oknie dialogowym kwalifikator

- Zdalny debuger nie jest uruchomiony na komputerze zdalnym. Aby rozwiązać ten problem, uruchom zdalny debuger.

- Zapora blokuje komunikację między programem Visual Studio i komputerem zdalnym. Aby rozwiązać ten problem, należy skonfigurować zaporę tak, aby zezwalała na komunikację programu Visual Studio i zdalnego debugera (msvsmon).

- Oprogramowanie antywirusowe blokuje komunikację między programem Visual Studio i komputerem zdalnym. Aby rozwiązać ten problem, Skonfiguruj oprogramowanie antywirusowe, aby umożliwić komunikację programu Visual Studio i zdalnego debugera (msvsmon).

## <a name="see-also"></a>Zobacz także
- [Debugowanie zdalne](../debugger/remote-debugging.md)