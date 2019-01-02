---
title: 'Błąd: Zdalny komputer nie mógł zainicjować komunikacji DCOM | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f507f8f2630c001beb9aad3e6f76904e6cd11489
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887506"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Błąd: Zdalny komputer nie mógł zainicjować komunikacji DCOM
Wystąpił błąd modelu DCOM podczas próby komunikacji z komputera lokalnego komputera zdalnego. Komputer lokalny to komputer, na którym jest  
  
 Uruchamianie programu Visual Studio. Ten błąd może wystąpić z kilku powodów:  
  
-   Komputer lokalny jest włączona Zapora.  
  
-   Uwierzytelnianie Windows z komputera zdalnego na komputer lokalny nie działa.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Jeśli komputer lokalny jest włączona Zapora Windows, zobacz [zdalne debugowanie](../debugger/remote-debugging.md) instrukcje dotyczące sposobu konfigurowania zapory dla debugowania lokalnego.  
  
2.  Testuj uwierzytelnienie Windows przez próby otwarcia udział plików na komputerze lokalnym z serwera zdalnego.  
  
3.  Aby przywrócić uwierzytelniania Windows, spróbuj wykonać ponowny rozruch obu komputerach. Sprawdź dzienniki zdarzeń na komputerach lokalnych i zdalnych dla błędów protokołu Kerberos i skontaktuj się z administratorami domeny o znanych problemach.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)