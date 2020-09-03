---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0922461c4ca5366e6d1dc215f5711f5566d00ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72729747"
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