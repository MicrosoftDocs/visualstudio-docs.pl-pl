---
title: 'Błąd: Błąd logowania grupy roboczej zdalnego | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7d919c287ecff6672ad5ba020be2e89c992e7a2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699213"
---
# <a name="error-workgroup-remote-logon-failure"></a>Błąd: Błąd logowania zdalnego grupy roboczej
Odczytuje ten błąd:

 Błąd logowania: Nieznana nazwa użytkownika lub nieprawidłowe hasło

 **Przyczyna**

 Ten błąd może wystąpić podczas próby nawiązania połączenia z maszyną zdalną, gdy debugowany na komputerze w grupie roboczej. Możliwe przyczyny:

-   Nie ma konta przy użyciu nazwy i hasła na komputerze zdalnym.

-   Jeśli komputer z programem Visual Studio i komputer zdalny znajdują się w grupach roboczych, ten błąd może wystąpić z powodu domyślnie **zasady zabezpieczeń lokalnych** ustawienie na komputerze zdalnym. Ustawieniem domyślnym dla **zasady zabezpieczeń lokalnych** jest ustawienie **tylko Gość — Uwierzytelnij jako gościa, użytkownicy lokalni**. Do debugowania w tej konfiguracji, należy zmienić ustawienie na komputerze zdalnym, aby **klasycznego — uwierzytelnianie użytkowników lokalnych, jak samodzielnie**.

> [!NOTE]
>  Musi być administratorem, aby wykonywać następujące zadania.

### <a name="to-open-the-local-security-policy-window"></a>Aby otworzyć okno Zasady zabezpieczeń lokalnych

1.  Rozpocznij **secpol.msc** przystawkę Microsoft Management Console. W polu wyszukiwania Windows, pole Uruchom Windows lub w wierszu polecenia, wpisz secpol.msc.

### <a name="to-add-user-rights-assignments"></a>Aby dodać przypisania praw użytkownika

1.  Otwórz **zasady zabezpieczeń lokalnych** okna.

2.  Rozwiń **zasady lokalne** folderu.

3.  Kliknij przycisk **Przypisywanie praw użytkownika**.

4.  W **zasad** kolumny, kliknij dwukrotnie **debugowanie programów** Aby przejrzeć bieżące przypisania zasad grupy lokalnej w **Ustawianie zasad zabezpieczeń lokalnych** okno dialogowe.

     ![Prawa użytkownika zasady zabezpieczeń lokalnych](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")

5.  Aby dodać nowych użytkowników, kliknij **Dodaj użytkownika lub grupę** przycisku.

### <a name="to-change-the-sharing-and-security-model"></a>Aby zmienić udostępnianie i Model zabezpieczeń

1.  Otwórz **zasady zabezpieczeń lokalnych** okna.

2.  Rozwiń **zasady lokalne** folderu.

3.  Kliknij przycisk **opcje zabezpieczeń**.

4.  W **zasad** kolumny, kliknij dwukrotnie **dostęp sieciowy: Udostępnianie i model zabezpieczeń dla kont lokalnych**.

5.  W **dostęp sieciowy: Udostępnianie i model zabezpieczeń dla kont lokalnych** okna dialogowego pola, zmień wartość na **klasycznego — uwierzytelnianie użytkowników lokalnych, jak samodzielnie** i kliknij przycisk **Zastosuj** przycisku.

     ![Local Security Policy Security Options](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")

## <a name="see-also"></a>Zobacz też
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)