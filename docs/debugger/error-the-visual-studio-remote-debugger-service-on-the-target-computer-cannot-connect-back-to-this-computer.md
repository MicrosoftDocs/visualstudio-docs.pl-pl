---
description: Ten błąd oznacza, że usługa zdalnego debugera jest uruchomiona w ramach konta użytkownika, którego nie można uwierzytelnić, gdy próbuje nawiązać połączenie z komputerem, na którym odbywa się debugowanie.
title: Usługa zdalnego debugera programu Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
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
ms.openlocfilehash: a08f1a7638233e2633a34287aad500ee81245be6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146694"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Błąd: Usługa zdalnego debugera Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem
Ten błąd oznacza, że usługa zdalnego debugera jest uruchomiona w ramach konta użytkownika, którego nie można uwierzytelnić, gdy próbuje nawiązać połączenie z komputerem, na którym odbywa się debugowanie. Ten błąd może wystąpić, gdy debugowanie zdalne korzysta ze starszego aparatu debugowania, a zdalny debuger działa jako usługa.

 W poniższej tabeli przedstawiono, jakie konta mogą uzyskać dostęp do komputera:

|Scenariusz|Konto LocalSystem|Konto domeny|Konta lokalne, które mają taką samą nazwę użytkownika i hasło na obu komputerach|
|-|-|-|-|
|Oba komputery w tej samej domenie|Tak|Tak|Tak|
|Oba komputery w domenach z zaufaniem dwukierunkowym|Nie|Nie|Tak|
|Jeden lub oba komputery w grupie roboczej|Nie|Nie|Tak|
|Komputery w różnych domenach|Nie|Nie|Tak|

 Dodatkowo:

- Konto, na którym uruchomiono usługę zdalny debuger programu Visual Studio, powinno być kontem administratora na komputerze zdalnym, aby można było debugować każdy proces.

- Konto musi mieć również przyznane `Log on as a service` uprawnienie na komputerze zdalnym korzystającym z narzędzia administracyjnego **zasad zabezpieczeń lokalnych** .

- Jeśli używasz konta lokalnego dostępu do komputera, musisz uruchomić usługę zdalny debuger programu Visual Studio w ramach konta lokalnego.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, że usługa zdalny debuger programu Visual Studio została prawidłowo skonfigurowana na komputerze zdalnym. Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).

2. Uruchom usługę zdalnego debugera w ramach konta, które ma dostęp do komputera hosta debugera, jak pokazano w poprzedniej tabeli.

### <a name="to-add-log-on-as-a-service-privilege"></a>Aby dodać uprawnienie "Logowanie w trybie usługi"

1. W menu **Start** wybierz pozycję **Panel sterowania**.

2. W panelu sterowania wybierz pozycję **Widok klasyczny**, w razie potrzeby.

3. Kliknij dwukrotnie pozycję **Narzędzia administracyjne**.

4. W oknie Narzędzia administracyjne kliknij dwukrotnie pozycję **zasady zabezpieczeń lokalnych**.

5. W oknie **Ustawienia zabezpieczeń lokalnych** rozwiń folder **Zasady lokalne** .

6. Kliknij pozycję **Przypisywanie praw użytkownika**.

7. W kolumnie **zasady** kliknij dwukrotnie pozycję **Logowanie jako usługa** , aby wyświetlić bieżące przypisania lokalnego zasady grupy w oknie dialogowym **Logowanie jako usługa** .

8. Aby dodać nowych użytkowników, kliknij przycisk **Dodaj użytkownika lub grupę** .

9. Po zakończeniu dodawania użytkowników kliknij przycisk **OK**.

### <a name="to-work-around-this-error"></a>Aby obejść ten błąd

- Uruchom Monitor zdalnego debugowania jako aplikację zamiast usługi.

## <a name="see-also"></a>Zobacz też
- [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
