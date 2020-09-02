---
title: 'Błąd: niepowodzenie zdalnego logowania grupy roboczej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 09f018982b81535ae23eafe7158aa88c0b6b08a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64798707"
---
# <a name="error-workgroup-remote-logon-failure"></a>Błąd: Błąd zdalnego logowania grupy roboczej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
1. Otwórz Loca  
  
2. Otwórz okno **zasady zabezpieczeń lokalnych** .  
  
3. Rozwiń folder **Zasady lokalne** .  
  
4. Kliknij pozycję **Przypisywanie praw użytkownika**.  
  
5. W kolumnie **zasady** kliknij dwukrotnie pozycję **debugowanie programów** , aby wyświetlić bieżące przypisania lokalnych zasad grupy w oknie dialogowym **Ustawienia zasad zabezpieczeń lokalnych** .  
  
     ![Prawa użytkownika zasad zabezpieczeń lokalnych](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6. Aby dodać nowych użytkowników, kliknij przycisk **Dodaj użytkownika lub grupę** .  
  
### <a name="to-change-the-sharing-and-security-model"></a>Aby zmienić model udostępniania i zabezpieczeń  
  
1. Otwórz okno **zasady zabezpieczeń lokalnych** .  
  
2. Rozwiń folder **Zasady lokalne** .  
  
3. Kliknij pozycję **Opcje zabezpieczeń**.  
  
4. W kolumnie **zasady** kliknij dwukrotnie pozycję **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych**.  
  
5. W oknie dialogowym **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych** Zmień wartość na **klasyczny — Użytkownicy lokalni uwierzytelniają się jako same** i kliknij przycisk **Zastosuj** .  
  
     ![Opcje zabezpieczeń lokalnych zasad zabezpieczeń](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)
