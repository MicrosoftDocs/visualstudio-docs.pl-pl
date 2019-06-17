---
title: 'Błąd: Usługa zdalnego debugera programu Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
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
ms.openlocfilehash: c07557fa64f86349a3baf8956d99b937ceab9f5a
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043439"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Błąd: Usługa zdalnego debugera programu Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem
Ten błąd oznacza, że usługa zdalnego debugera jest uruchomiona w ramach konta użytkownika, które nie mogą uwierzytelnić się podczas próby połączenia z komputerem, na którym wykonujesz debugowanie z. Ten błąd może wystąpić, gdy zdalne debugowanie przy użyciu starego aparatu debugowania i zdalny debuger działa jako usługa.

 W poniższej tabeli przedstawiono, jakie kont mogą uzyskiwać dostęp do komputera:

|||||
|-|-|-|-|
||Konto System lokalny|Konto domeny|Konta lokalne, które mają tej samej nazwy użytkownika i hasła na obu komputerach|
|Oba komputery w tej samej domenie|Tak|Yes|Tak|
|Oba komputery w domenach, które mają dwukierunkowe relacje zaufania|Nie|Nie|Tak|
|Jeden lub oba komputery w grupie roboczej|Nie|Nie|Tak|
|Komputery w różnych domenach|Nie|Nie|Tak|

 Ponadto:

- Konto uruchamiania usługi zdalnego debugera Visual Studio w obszarze należy administrator na komputerze zdalnym, aby go debugować dowolny proces.

- Ponadto konto musi mieć uprawnienia `Log on as a service` uprawnień na komputerze zdalnym, który używa **zasady zabezpieczeń lokalnych** narzędzie administracyjne.

- Korzystając z dostępu do lokalnego konta komputera, należy uruchomić usługę zdalnego debugera Visual Studio przy użyciu lokalnego konta.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, że usługa zdalnego debugera Visual Studio jest prawidłowo skonfigurowany na komputerze zdalnym. Aby uzyskać więcej informacji, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

2. Uruchom usługę zdalnego debugera przy użyciu konta, które mogą uzyskiwać dostęp do komputera hosta debugera, jak pokazano w poprzedniej tabeli.

### <a name="to-add-log-on-as-a-service-privilege"></a>Aby dodać uprawnienie "Logowanie jako usługa"

1. Na **Start** menu, wybierz **Panelu sterowania**.

2. W Panelu sterowania wybierz **Klasyczny**, jeśli to konieczne.

3. Kliknij dwukrotnie **narzędzia administracyjne**.

4. W oknie Narzędzia administracyjne kliknij dwukrotnie **zasady zabezpieczeń lokalnych**.

5. W **ustawienia zabezpieczeń lokalnych** okna, rozwiń węzeł **zasady lokalne** folderu.

6. Kliknij przycisk **Przypisywanie praw użytkownika**.

7. W **zasad** kolumny, kliknij dwukrotnie **Zaloguj się jako usługa** Aby przejrzeć bieżące przypisania zasad grupy lokalne, w **Zaloguj się jako usługa** okno dialogowe.

8. Aby dodać nowych użytkowników, kliknij **Dodaj użytkownika lub grupę** przycisku.

9. Po zakończeniu dodawania użytkowników kliknij **OK**.

### <a name="to-work-around-this-error"></a>Aby obejść ten błąd

- Uruchom Monitor debugera zdalnego jako aplikację, a nie jako usługa.

## <a name="see-also"></a>Zobacz też
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)