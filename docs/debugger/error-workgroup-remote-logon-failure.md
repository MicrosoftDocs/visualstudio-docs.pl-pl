---
title: Błąd — niepowodzenie zdalnego logowania grupy roboczej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 97045215098b1f59d5f76a928e9e0a1ab8362756
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460095"
---
# <a name="error-workgroup-remote-logon-failure"></a>Błąd: Błąd zdalnego logowania grupy roboczej
Ten błąd odczytuje:

 Niepowodzenie logowania: Nieznana nazwa użytkownika lub nieprawidłowe hasło

 **Przyczyna**

 Ten błąd może wystąpić w przypadku debugowania z komputera w grupie roboczej i próby nawiązania połączenia z maszyną zdalną. Ta sytuacja może mieć następujące przyczyny:

- Na komputerze zdalnym nie ma konta o pasującej nazwie i haśle.

- Jeśli zarówno komputer z programem Visual Studio, jak i maszyna zdalna znajdują się w grupach roboczych, ten błąd może wystąpić z powodu domyślnego ustawienia **zasad zabezpieczeń lokalnych** na maszynie zdalnej. Domyślnym ustawieniem **zasad zabezpieczeń lokalnych** jest **tylko gość — Użytkownicy lokalni są uwierzytelniani jako gość**. Aby debugować tę konfigurację, należy zmienić ustawienie na maszynie zdalnej na **klasyczne — Użytkownicy lokalni są uwierzytelniani jako same**.

> [!NOTE]
> Aby wykonać następujące zadania, musisz być administratorem.

### <a name="to-open-the-local-security-policy-window"></a>Aby otworzyć okno zasady zabezpieczeń lokalnych

1. Uruchom przystawkę Microsoft Management Console programu **secpol. msc** . W usłudze Windows Search wpisz polecenie secpol. msc, Windows Run lub w wierszu polecenia.

### <a name="to-add-user-rights-assignments"></a>Aby dodać przypisania praw użytkownika

1. Otwórz okno **zasady zabezpieczeń lokalnych** .

2. Rozwiń folder **Zasady lokalne** .

3. Kliknij pozycję **Przypisywanie praw użytkownika**.

4. W kolumnie **zasady** kliknij dwukrotnie pozycję **debugowanie programów** , aby wyświetlić bieżące przypisania lokalnych zasad grupy w oknie dialogowym **Ustawienia zasad zabezpieczeń lokalnych** .

     ![Prawa użytkownika zasad zabezpieczeń lokalnych](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")

5. Aby dodać nowych użytkowników, kliknij przycisk **Dodaj użytkownika lub grupę** .

### <a name="to-change-the-sharing-and-security-model"></a>Aby zmienić model udostępniania i zabezpieczeń

1. Otwórz okno **zasady zabezpieczeń lokalnych** .

2. Rozwiń folder **Zasady lokalne** .

3. Kliknij pozycję **Opcje zabezpieczeń**.

4. W kolumnie **zasady** kliknij dwukrotnie pozycję **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych**.

5. W oknie dialogowym **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych** Zmień wartość na **klasyczny — Użytkownicy lokalni uwierzytelniają się jako same** i kliknij przycisk **Zastosuj** .

     ![Opcje zabezpieczeń lokalnych zasad zabezpieczeń](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")

## <a name="see-also"></a>Zobacz też
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)