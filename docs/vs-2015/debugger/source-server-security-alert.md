---
title: Alarm zabezpieczeń serwera źródłowego | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc7c68fe767d2add0842e30f66c51a3dcc84905f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447289"
---
# <a name="source-server-security-alert"></a>Alarm zabezpieczeń serwera źródłowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas korzystania z serwera źródłowego, należy używać tylko plików symboli ze znanych i zaufanych lokalizacji.  
  
 To ostrzeżenie jest wyświetlane po włączeniu obsługi serwera źródłowego. Polecenia serwera źródłowego są osadzone w pliki symboli debugowania (pliki PDB). Upewnij się, że wiesz skąd pochodzą pliki PDB.  
  
> [!IMPORTANT]
> Następujące potencjalne zagrożenia bezpieczeństwa musi być brana pod uwagę podczas korzystania z serwera źródłowego: Dowolne polecenia mogą być osadzone w pliku PDB aplikacji, dlatego upewnij się, że możesz umieścić tylko te, które chcesz wykonać w pliku srcsrv.ini. Każda próba wykonania polecenia nie w pliku srcsvr.ini spowoduje pojawienie się okna dialogowego potwierdzenia. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: Debuger musi wykonać polecenie niezaufane](../debugger/security-warning-debugger-must-execute-untrusted-command.md). W parametrach polecenia jest wykonywana żadna Weryfikacja, więc należy być ostrożnym z poleceniami zaufanymi. Na przykład, jeśli użytkownik zaufał narzędziu cmd.exe, złośliwy użytkownik może określić parametry, które czyniłyby polecenie niebezpiecznym.  
  
## <a name="see-also"></a>Zobacz też  
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Source Server](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
