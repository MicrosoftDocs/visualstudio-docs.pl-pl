---
title: Alert zabezpieczeń serwera źródłowego | Microsoft Docs
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
ms.openlocfilehash: 3f8b122deab5dbdc30b129bce221a804f8c53aa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699324"
---
# <a name="source-server-security-alert"></a>Alarm zabezpieczeń serwera źródłowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku korzystania z serwera źródłowego należy używać tylko plików symboli, które pochodzą z znanej i zaufanej lokalizacji.  
  
 To ostrzeżenie jest wyświetlane po włączeniu obsługi serwera źródłowego. Polecenia serwera źródłowego są osadzone w plikach symboli debugowania (pliki PDB). Upewnij się, że wiesz, skąd pochodzą pliki PDB.  
  
> [!IMPORTANT]
> Podczas korzystania z serwera źródłowego należy wziąć pod uwagę następujące potencjalne zagrożenia bezpieczeństwa: dowolne polecenia mogą być osadzone w pliku PDB aplikacji, więc upewnij się, że umieścisz tylko te, które chcesz wykonać w pliku srcsrv.ini. Każda próba wykonania polecenia nie w pliku srcsvr.ini spowoduje pojawienie się okna dialogowego potwierdzenia. Aby uzyskać więcej informacji, zobacz [Ostrzeżenie o zabezpieczeniach: debuger musi wykonać polecenie niezaufane](../debugger/security-warning-debugger-must-execute-untrusted-command.md). W parametrach poleceń nie jest przeprowadzana Walidacja, dlatego należy zachować ostrożność przy użyciu zaufanych poleceń. Na przykład, jeśli użytkownik zaufał narzędziu cmd.exe, złośliwy użytkownik może określić parametry, które czyniłyby polecenie niebezpiecznym.  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Serwer źródłowy](https://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
