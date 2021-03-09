---
title: Uwierzytelnianie Kerberos nie powiodło się | Microsoft Docs
description: Ten błąd występuje, gdy Monitor zdalnego debugowania programu Visual Studio jest uruchomiony w ramach konta System lokalny lub usługa sieciowa.
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 41ffc4e5cb71c78462c9dbfd18472a4fc4e57c7d
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466241"
---
# <a name="error-kerberos-authentication-failed"></a>Błąd: Uwierzytelnianie Kerberos nie powiodło się
Podczas próby wykonania zdalnego debugowania może zostać wyświetlony następujący komunikat o błędzie:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.
```

 Ten błąd występuje, gdy Monitor zdalnego debugowania programu Visual Studio jest uruchomiony w ramach konta System lokalny lub usługa sieciowa. W ramach jednego z tych kont zdalny debuger musi nawiązać połączenie z uwierzytelnianiem Kerberos, aby komunikować się z komputerem hosta debugera programu Visual Studio.

 Uwierzytelnianie Kerberos nie jest dostępne w następujących warunkach:

- Komputer docelowy lub komputer hosta debugera znajduje się w grupie roboczej, a nie w domenie

   \- oraz

- Protokół Kerberos został wyłączony na kontrolerze domeny.

  Jeśli uwierzytelnianie Kerberos nie jest dostępne, Zmień konto używane do uruchamiania programu Visual Studio Monitor zdalnego debugowania. Aby uzyskać procedurę, zobacz [błąd: usługa zdalny debuger programu Visual Studio na komputerze docelowym nie może nawiązać połączenia z powrotem z tym komputerem](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).

  Jeśli oba komputery są połączone z tą samą domeną, a ten komunikat jest nadal wyświetlany, sprawdź, czy serwer DNS na komputerze docelowym prawidłowo rozpoznaje nazwę komputera hosta debugera. Zapoznaj się z poniższą procedurą.

### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Aby sprawdzić, czy usługa DNS na komputerze docelowym prawidłowo rozwiązuje nazwę komputera hosta debugera

1. Na komputerze docelowym otwórz menu **Start** , wskaż **akcesoria** , a następnie kliknij przycisk **wiersz polecenia**.

2. W oknie **wiersza polecenia** wpisz:

    ```cmd
    ping <debugger_host_computer_name>
    ```

3. Pierwszy wiersz `ping` odpowiedzi przedstawia pełną nazwę komputera i adres IP zwrócone przez system DNS dla określonego komputera.

4. Na komputerze hosta debugera Otwórz okno **wiersza polecenia** i uruchom polecenie `ipconfig` .

5. Porównaj wartości adresów IP.

## <a name="see-also"></a>Zobacz też
- [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
