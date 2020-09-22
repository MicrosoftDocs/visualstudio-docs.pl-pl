---
title: Program SQL Server może &apos; znajdować SSDEBUGPS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50c8b6c2385879e4cf41c8cc2aea57715050b5e2
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851791"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Błąd: SQL może&#39;t Find SSDEBUGPS

SSDEBUGPS.dll to składnik hosta debugowania SQL Server.

Ten błąd występuje podczas próby uruchomienia debugowania i wskazuje, że określony plik nie jest obecny na [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] maszynie. Możliwe przyczyny to, że Instalator zdalnego debugowania nigdy nie został uruchomiony lub właśnie ten plik został usunięty.

Istnieją dwa sposoby rozwiązania tego błędu: przez odinstalowanie Instalatora zdalnego debugowania i skopiowanie pliku na [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] komputer.

Aby ponownie uruchomić Instalatora zdalnego debugowania, postępuj zgodnie z instrukcjami na stronie [debugowanie zdalne](../debugger/remote-debugging.md).

Jeśli można znaleźć kopię ssdebugps.dll, można skopiować ją na [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] maszynę. Jeśli jest obecny, plik będzie w katalogu \Program Files \ Common Files\Microsoft Shared\SQL Debug. Można go znaleźć na innym [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] komputerze lub na komputerze, na którym jest zainstalowany program Visual Studio 2005.

Aby skopiować SSDEBUGPS.dll na maszynę SQL Server 2005:

1. Skopiuj plik do katalogu o tej samej nazwie i ścieżce na [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] komputerze.

2. Zarejestruj go, otwierając **wiersz polecenia**i uruchamiając następujące polecenie:

    ```cmd
    regsvr32 ssdebugps.dll
    ```
