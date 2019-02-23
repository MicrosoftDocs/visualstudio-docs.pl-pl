---
title: 'Ostrzeżenie o zabezpieczeniach: Debuger musi wykonać polecenie niezaufane | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c4ab45feeae409a1951e1a57e964eaaa5963896
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690357"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Ostrzeżenie o zabezpieczeniach: Debuger musi wykonać polecenie niezaufane
To okno dialogowe ostrzeżenia pojawia się podczas korzystania z serwera źródłowego. Oznacza, że polecenie, które debugger musi wykonać, aby uzyskać kod źródłowy nie jest na liście zaufanych poleceń dla serwera źródłowego, zawartej w pliku srcsvr.ini. Jeśli jest to prawidłowe polecenie, można dodać go do pliku srcsvr.ini. W przeciwnym razie nie należy uruchamiać go. Aby uzyskać więcej informacji, zobacz [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="message-text"></a>Tekst komunikatu
 **Debuger musi wykonać następujące polecenie niezaufane, aby uzyskać kod źródłowy z serwera źródłowego.**

 **Jeśli pliku symboli, debugowania (\*.pdb) jest spoza znanego i zaufanego źródła, to polecenie może być nieprawidłowe lub niebezpieczne do uruchomienia.**

 **Czy chcesz uruchomić to polecenie?**

## <a name="uielement-list"></a>Lista elementów UI
 Okno polecenia tekst z pliku .pdb do uruchomienia.

 Uruchom Zezwalaj na polecenie do uruchomienia.

 Nie, uruchom, Zatrzymaj wykonywanie polecenia i pobieranie plików z serwera źródłowego.

## <a name="see-also"></a>Zobacz też
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Source Server](/windows/desktop/Debug/source-server-and-source-indexing)