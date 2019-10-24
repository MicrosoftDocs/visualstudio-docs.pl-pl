---
title: Nie można dołączyć do procesu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.unable2attach
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
ms.openlocfilehash: 22d798d30d09cb509f53d093ae61bb1a02b414ec
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728874"
---
# <a name="unable-to-attach-to-the-process"></a>Nie można dołączyć do procesu
Nie można dołączyć do procesu. Składnik debugera na serwerze otrzymał odmowę dostępu podczas nawiązywania połączenia z tą maszyną.

 Istnieją dwa typowe scenariusze, które powodują wystąpienie tego błędu:

 **Scenariusz 1:** Na maszynie A jest uruchomiony system Windows XP. Na komputerze B jest uruchomiony system Windows Server 2003. Rejestr na komputerze B zawiera następującą wartość DWORD:

 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`

 Użytkownik 1 uruchamia sesję serwera terminali (sesja 1) na komputerze B i uruchamia zarządzaną aplikację z tej sesji.

 Użytkownik 2, który jest administratorem na obu komputerach, jest zalogowany na komputerze A. Z tego miejsca próbuje dołączyć do aplikacji uruchomionej na sesji 1 na komputerze B.

 **Scenariusz 2:** Jeden użytkownik jest zalogowany na dwóch komputerach, a i B, w tej samej grupie roboczej, przy użyciu tego samego hasła na obu komputerach. Debuger działa na maszynie A i próbuje dołączyć do zarządzanej aplikacji uruchomionej na komputerze B. komputer A ma **dostęp do sieci: udostępnianie i model zabezpieczeń dla kont lokalnych** ustawionych na **gościa**.

### <a name="to-solve-scenario-1"></a>Aby rozwiązać scenariusz 1

- Uruchom Debuger i zarządzaną aplikację w ramach tej samej nazwy konta użytkownika i hasła.

### <a name="to-solve-scenario-2"></a>Aby rozwiązać scenariusz 2

1. Z menu **Start** wybierz pozycję **Panel sterowania**.

2. W panelu sterowania kliknij dwukrotnie ikonę **Narzędzia administracyjne**.

3. W oknie Narzędzia administracyjne kliknij dwukrotnie pozycję **zasady zabezpieczeń lokalnych**.

4. W oknie Zasady zabezpieczeń lokalnych wybierz pozycję **Zasady lokalne**.

5. W kolumnie **zasady** kliknij dwukrotnie pozycję **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych**.

6. W oknie dialogowym **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych** Zmień ustawienie zabezpieczeń lokalnych na **klasyczne**, a następnie kliknij przycisk **OK**.

    > [!CAUTION]
    > Zmiana modelu zabezpieczeń na klasyczny może skutkować nieoczekiwanym dostępem do udostępnionych plików i składników modelu DCOM. Po wprowadzeniu tej zmiany użytkownik zdalny może uwierzytelnić się przy użyciu konta użytkownika lokalnego zamiast gościa. Jeśli użytkownik zdalny jest zgodny z nazwą użytkownika i hasłem, ten użytkownik będzie mógł uzyskać dostęp do dowolnych folderów lub obiektów DCOM, które zostały udostępnione. W przypadku korzystania z tego modelu zabezpieczeń upewnij się, że wszystkie konta użytkowników na komputerze mają silne hasła lub skonfiguruj odizolowaną wyspa sieciową dla debugowanych i debugowanych maszyn, aby zapobiec nieautoryzowanemu dostępowi.

7. Zamknij wszystkie okna.

## <a name="see-also"></a>Zobacz także
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)