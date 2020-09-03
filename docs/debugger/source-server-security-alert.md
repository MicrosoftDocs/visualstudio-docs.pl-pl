---
title: Alert zabezpieczeń serwera źródłowego | Microsoft Docs
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
ms.openlocfilehash: 69511c2f83570abf37ef4bea8b71c8f59431a128
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72729572"
---
# <a name="source-server-security-alert"></a>Alarm zabezpieczeń serwera źródłowego
W przypadku korzystania z serwera źródłowego należy używać tylko plików symboli, które pochodzą z znanej i zaufanej lokalizacji.

 To ostrzeżenie jest wyświetlane po włączeniu obsługi serwera źródłowego. Polecenia serwera źródłowego są osadzone w plikach symboli debugowania (pliki** \* . pdb** ). Upewnij się, że wiesz, skąd pochodzą pliki PDB.

> [!IMPORTANT]
> Podczas korzystania z serwera źródłowego należy wziąć pod uwagę następujące potencjalne zagrożenia bezpieczeństwa: dowolne polecenia mogą być osadzone w pliku PDB aplikacji, więc upewnij się, że umieścisz tylko te, które chcesz wykonać w pliku srcsrv.ini. Każda próba wykonania polecenia nie w pliku srcsvr.ini spowoduje pojawienie się okna dialogowego potwierdzenia. Aby uzyskać więcej informacji, zobacz [Ostrzeżenie o zabezpieczeniach: debuger musi wykonać polecenie niezaufane](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nie jest sprawdzana poprawność parametrów poleceń, więc należy być ostrożnym z poleceniami zaufanymi. Na przykład, jeśli użytkownik zaufał narzędziu cmd.exe, złośliwy użytkownik może określić parametry, które czyniłyby polecenie niebezpiecznym.

## <a name="see-also"></a>Zobacz też
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Serwer źródłowy](/windows/desktop/Debug/source-server-and-source-indexing)
