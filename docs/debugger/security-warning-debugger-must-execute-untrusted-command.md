---
description: To ostrzeżenie jest wyświetlane podczas korzystania z serwera źródłowego.
title: 'Ostrzeżenie o zabezpieczeniach: debuger musi wykonać niezaufane polecenie | Microsoft Docs'
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1ca71db31fc976a2bc3c652929fd9215f2f3123f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166661"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Ostrzeżenie o zabezpieczeniach: Debuger musi wykonać niezaufaną komendę
To ostrzeżenie jest wyświetlane podczas korzystania z serwera źródłowego. Wskazuje, że polecenie debuger musi zostać wykonane w celu uzyskania kodu źródłowego nie znajduje się na liście zaufanych poleceń dla serwera źródłowego zawartego w pliku srcsvr.ini. Jeśli jest to prawidłowe polecenie, można je dodać do pliku srcsvr.ini. W przeciwnym razie nie należy uruchamiać go. Aby uzyskać więcej informacji, zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="message-text"></a>Tekst komunikatu
 **Debuger musi wykonać następujące niezaufane polecenie, aby uzyskać kod źródłowy z serwera źródłowego.**

 **Jeśli plik symbolu debugowania ( \* . pdb) nie pochodzi ze znanego i zaufanego źródła, to polecenie może być nieprawidłowe lub niebezpieczne do uruchomienia.**

 **Czy chcesz uruchomić to polecenie?**

## <a name="uielement-list"></a>Lista elementów UI
 Polecenie pola tekstowego z pliku. pdb do uruchomienia.

 Uruchom polecenie Zezwalaj na uruchomienie polecenia.

 Nie uruchamiaj zatrzymania wykonywania polecenia i pobierania pliku z serwera źródłowego.

## <a name="see-also"></a>Zobacz też
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Serwer źródłowy](/windows/desktop/Debug/source-server-and-source-indexing)
