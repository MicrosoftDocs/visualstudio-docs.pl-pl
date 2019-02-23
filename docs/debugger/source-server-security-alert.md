---
title: Alarm zabezpieczeń serwera źródłowego | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af216023b1a157136f86f0ca8527a8b433b0a34b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719148"
---
# <a name="source-server-security-alert"></a>Alarm zabezpieczeń serwera źródłowego
Podczas korzystania z serwera źródłowego, należy używać tylko plików symboli ze znanych i zaufanych lokalizacji.

 To ostrzeżenie jest wyświetlane po włączeniu obsługi serwera źródłowego. Polecenia serwera źródłowego są osadzone w pliki symboli debugowania (**\*.pdb** plików). Upewnij się, że wiesz skąd pochodzą pliki PDB.

> [!IMPORTANT]
>  Następujące potencjalne zagrożenia bezpieczeństwa musi być brana pod uwagę podczas korzystania z serwera źródłowego: Dowolne polecenia mogą być osadzone w pliku PDB aplikacji, dlatego upewnij się, że możesz umieścić tylko te, które chcesz wykonać w pliku srcsrv.ini. Każda próba wykonania polecenia nie w pliku srcsvr.ini spowoduje pojawienie się okna dialogowego potwierdzenia. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: Debuger musi wykonać polecenie niezaufane](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nie jest sprawdzana poprawność parametrów poleceń, więc należy być ostrożnym z poleceniami zaufanymi. Na przykład, jeśli użytkownik zaufał narzędziu cmd.exe, złośliwy użytkownik może określić parametry, które czyniłyby polecenie niebezpiecznym.

## <a name="see-also"></a>Zobacz też
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Source Server](/windows/desktop/Debug/source-server-and-source-indexing)
