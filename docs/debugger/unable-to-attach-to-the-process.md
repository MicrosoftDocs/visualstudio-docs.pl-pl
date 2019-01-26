---
title: Nie można dołączyć do procesu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 78246ffbb73aea2bbf6c774ec741d710d87586d2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042572"
---
# <a name="unable-to-attach-to-the-process"></a>Nie można dołączyć do procesu
Nie można dołączyć do procesu. Składnik debugera na serwerze Odebrano odmowa dostępu podczas łączenia z tą maszyną.  
  
 Istnieją dwa typowe scenariusze, które przyczyny wystąpienia tego błędu:  
  
 **Scenariusz 1:** A maszynie jest uruchomiony Windows XP. Komputer B jest uruchomiony system Windows Server 2003. Rejestr na komputerze B zawiera następującą wartość DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 Użytkownik 1 uruchamia sesję serwera terminali (sesja 1) na komputerze B i uruchamia aplikację zarządzaną z tej sesji.  
  
 Użytkownik 2, który jest administratorem na obu komputerach, jest zalogowany do komputera A. W efekcie użytkownik próbuje dołączyć do aplikacji uruchomionej w sesji 1 na maszynie B.  
  
 **Scenariusz 2:** Jeden użytkownik jest zalogowany na dwóch komputerach, A i B, w tej samej grupie roboczej, za pomocą tego samego hasła na obu komputerach. Debuger jest uruchomiony na komputerze A, a następnie próbujesz podłączyć się do zarządzanej aplikacji uruchomionych na maszynie B. maszyny, A ma **dostęp sieciowy: Udostępnianie i model zabezpieczeń dla kont lokalnych** równa **gościa**.  
  
### <a name="to-solve-scenario-1"></a>Aby rozwiązać scenariusz 1  
  
-   Uruchom debuger i zarządzanych aplikacji w ramach tej samej nazwy konta użytkownika i hasło.  
  
### <a name="to-solve-scenario-2"></a>Aby rozwiązać scenariuszu 2  
  
1.  Z **Start** menu, wybierz **Panelu sterowania**.  
  
2.  W Panelu sterowania kliknij dwukrotnie **narzędzia administracyjne**.  
  
3.  W oknie Narzędzia administracyjne kliknij dwukrotnie **zasady zabezpieczeń lokalnych**.  
  
4.  W oknie lokalne zasady zabezpieczeń wybierz **zasady lokalne**.  
  
5.  W **zasady** kolumny, kliknij dwukrotnie **dostęp sieciowy: Udostępnianie i model zabezpieczeń dla kont lokalnych**.  
  
6.  W **dostęp sieciowy: Udostępnianie i model zabezpieczeń dla kont lokalnych** okna dialogowego pole, zmień ustawienie zabezpieczeń lokalnych, aby **klasycznego**i kliknij przycisk **OK**.  
  
    > [!CAUTION]
    >  Zmiana modelu zabezpieczeń do klasycznego modelu może spowodować nieoczekiwany dostęp do udostępnionych plików i składników DCOM components. W przypadku wprowadzenia tej zmiany użytkownika zdalnego mogą uwierzytelniać za pomocą Twojego konta użytkownika lokalnego, a nie gościa. Jeśli użytkownik zdalny pasuje do nazwy użytkownika i hasło, ten użytkownik będzie można uzyskać dostęp do dowolnego folderu lub udostępnione się obiekt modelu DCOM. Jeśli używasz tego modelu zabezpieczeń, upewnij się, że wszystkie konta użytkowników na komputerze silnych haseł lub konfigurowanie sieci izolowanej wyspie debugowanie i debugować maszyn w celu uniemożliwienia nieupoważnionego dostępu.  
  
7.  Zamknij wszystkie okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)