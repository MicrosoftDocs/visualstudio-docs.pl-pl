---
title: 'Ostrzeżenie o zabezpieczeniach: debuger musi wykonać niezaufane polecenie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a29ba026f9b3c2b8839d474c2d0833eb79f7ffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683295"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Ostrzeżenie o zabezpieczeniach: Debuger musi wykonać niezaufaną komendę
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To ostrzeżenie jest wyświetlane podczas korzystania z serwera źródłowego. Wskazuje, że polecenie debuger musi zostać wykonane w celu uzyskania kodu źródłowego nie znajduje się na liście zaufanych poleceń dla serwera źródłowego zawartego w pliku srcsvr.ini. Jeśli jest to prawidłowe polecenie, można je dodać do pliku srcsvr.ini. W przeciwnym razie nie należy uruchamiać go. Aby uzyskać więcej informacji, zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Tekst komunikatu  
 **Debuger musi wykonać następujące niezaufane polecenie, aby uzyskać kod źródłowy z serwera źródłowego.**  
  
 **Jeśli plik symbolu debugowania ( \* . pdb) nie pochodzi ze znanego i zaufanego źródła, to polecenie może być nieprawidłowe lub niebezpieczne do uruchomienia.**  
  
 **Czy chcesz uruchomić to polecenie?**  
  
## <a name="uielement-list"></a>Lista elementów UI  
 Pole tekstowe  
 Polecenie z pliku. pdb do uruchomienia.  
  
 Uruchom  
 Zezwalaj na uruchomienie polecenia.  
  
 Nie uruchamiaj  
 Zatrzymaj wykonywanie polecenia i pobieranie pliku z serwera źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Serwer źródłowy](https://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)
