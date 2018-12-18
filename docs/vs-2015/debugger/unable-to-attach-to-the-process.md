---
title: Nie można dołączyć do procesu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0075050b6d24b63ed8380644ad9ec50dd4aa8ec
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737667"
---
# <a name="unable-to-attach-to-the-process"></a>Nie można dołączyć do procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nie można dołączyć do procesu. Składnik debugera na serwerze Odebrano odmowa dostępu podczas łączenia z tą maszyną.  
  
 Istnieją dwa typowe scenariusze, które przyczyny wystąpienia tego błędu:  
  
 **Scenariusz 1:** maszyny, A systemem Windows XP. Komputer B jest uruchomiony system Windows Server 2003. Rejestr na komputerze B zawiera następującą wartość DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 Użytkownik 1 uruchamia sesję serwera terminali (sesja 1) na komputerze B i uruchamia aplikację zarządzaną z tej sesji.  
  
 Użytkownik 2, który jest administratorem na obu komputerach, jest zalogowany do komputera A. W efekcie użytkownik próbuje dołączyć do aplikacji uruchomionej w sesji 1 na maszynie B.  
  
 **Scenariusz 2:** jeden użytkownik jest zalogowany na dwie maszyny, A i B, w tej samej grupie roboczej, za pomocą tego samego hasła na obu komputerach. Debuger jest uruchomiony na komputerze A, a następnie próbujesz podłączyć się do zarządzanej aplikacji uruchomionych na maszynie B. maszyny, A ma **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych** równa **gościa**.  
  
### <a name="to-solve-scenario-1"></a>Aby rozwiązać scenariusz 1  
  
-   Uruchom debuger i zarządzanych aplikacji w ramach tej samej nazwy konta użytkownika i hasło.  
  
### <a name="to-solve-scenario-2"></a>Aby rozwiązać scenariuszu 2  
  
1.  Z **Start** menu, wybierz **Panelu sterowania**.  
  
2.  W Panelu sterowania kliknij dwukrotnie **narzędzia administracyjne**.  
  
3.  W oknie Narzędzia administracyjne kliknij dwukrotnie **zasady zabezpieczeń lokalnych**.  
  
4.  W oknie lokalne zasady zabezpieczeń wybierz **zasady lokalne**.  
  
5.  W **zasady** kolumny, kliknij dwukrotnie **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych**.  
  
6.  W **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych** okna dialogowego pole, zmień ustawienie zabezpieczeń lokalnych, aby **klasycznego**i kliknij przycisk **OK**.  
  
    > [!CAUTION]
    >  Zmiana modelu zabezpieczeń do klasycznego modelu może spowodować nieoczekiwany dostęp do udostępnionych plików i składników DCOM components. W przypadku wprowadzenia tej zmiany użytkownika zdalnego mogą uwierzytelniać za pomocą Twojego konta użytkownika lokalnego, a nie gościa. Jeśli użytkownik zdalny pasuje do nazwy użytkownika i hasło, ten użytkownik będzie można uzyskać dostęp do dowolnego folderu lub udostępnione się obiekt modelu DCOM. Jeśli używasz tego modelu zabezpieczeń, upewnij się, że wszystkie konta użytkowników na komputerze silnych haseł lub konfigurowanie sieci izolowanej wyspie debugowanie i debugować maszyn w celu uniemożliwienia nieupoważnionego dostępu.  
  
7.  Zamknij wszystkie okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)



