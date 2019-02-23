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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e936292010c73decffadc5b215156f2200ed8b3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683077"
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