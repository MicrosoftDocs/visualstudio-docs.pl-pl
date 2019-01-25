---
title: 'Błąd: Debugowanie nie powiodło się, ponieważ nie włączono uwierzytelniania zintegrowanego Windows | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6027cd94-74cf-470f-b7ce-6f6b68bc56ba
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 11b4834cfe6c87f3d6093a38c7a97fe0da67aab4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797496"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Błąd: Debugowanie nie powiodło się, ponieważ nie włączono uwierzytelniania zintegrowanego Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uwierzytelnianie użytkownika, która wnioskowała o debugowaniu została uniemożliwiona przez błąd uwierzytelniania. Taka sytuacja może wystąpić przy próbie wkraczać do aplikacji sieci Web lub usługi sieci Web XML. Jedną z przyczyn tego błędu jest to zintegrowane uwierzytelnianie Windows nie jest włączona. Aby ją włączyć, wykonaj kroki opisane w "Aby włączyć zintegrowane uwierzytelnianie Windows".  
  
 Jeśli ma włączone zintegrowane uwierzytelnianie Windows, a ten błąd jest nadal wyświetlana, może się zdarzyć, że ten błąd jest spowodowany **szyfrowanego uwierzytelniania dla Windows serwerów domeny** jest włączona. W takiej sytuacji należy skontaktować się z administratorem sieci.  
  
### <a name="to-enable-integrated-windows-authentication"></a>Aby włączyć zintegrowane uwierzytelnianie Windows  
  
1.  Zaloguj się do serwera sieci Web przy użyciu konta administratora.  
  
2.  Kliknij przycisk **Start** a następnie kliknij przycisk **Panelu sterowania**.  
  
3.  W **Panelu sterowania**, kliknij dwukrotnie **narzędzia administracyjne**.  
  
4.  Kliknij dwukrotnie **Internetowe usługi informacyjne**.  
  
5.  Kliknij węzeł serwera sieci Web.  
  
     A **witryn sieci Web** zostanie otwarty folder poniżej nazwę serwera.  
  
6.  Można skonfigurować uwierzytelniania dla wszystkich witryn sieci Web lub dla poszczególnych witryn sieci Web. Aby skonfigurować uwierzytelnianie dla wszystkich witryn sieci Web, kliknij prawym przyciskiem myszy **witryn sieci Web** folder, a następnie kliknij przycisk **właściwości**. Aby skonfigurować uwierzytelnianie witryny sieci Web, otwórz **witryn sieci Web** folderu, kliknij prawym przyciskiem myszy witryny sieci Web, a następnie kliknij przycisk **właściwości**.  
  
     **Właściwości** zostanie wyświetlone okno dialogowe.  
  
7.  Kliknij przycisk **zabezpieczeń katalogu** kartę.  
  
8.  W **anonimowy dostęp i kontrola uwierzytelniania** kliknij **Edytuj**.  
  
     **Metod uwierzytelniania** zostanie wyświetlone okno dialogowe.  
  
9. W obszarze **dostępu uwierzytelnionego**, wybierz opcję **uwierzytelniania zintegrowanego Windows**.  
  
10. Kliknij przycisk **OK** zamknąć **metod uwierzytelniania** okno dialogowe.  
  
11. Kliknij przycisk **OK** zamknąć **właściwości** okno dialogowe.  
  
12. Zamknij **Internetowe usługi informacyjne** okna.  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Aby włączyć zintegrowane uwierzytelnianie Windows w systemie Windows Vista/IIS 7  
  
1.  Zaloguj się do serwera sieci Web przy użyciu konta administratora.  
  
2.  Włącz uwierzytelnianie Windows oraz zgodność z narzędziami zarządzania II6, jeśli nie została wcześniej utworzona, wykonując następujące czynności:  
  
    1.  Kliknij przycisk **Start**, kliknij przycisk **Panelu sterowania** a następnie kliknij przycisk **programy**.  
  
    2.  W obszarze **programy i funkcje**, kliknij przycisk **Windows Włącz lub wyłącz funkcje**.  
  
         Okno dialogowe User Access Control pojawia się i wyświetli monit o uprawnienia kontynuować.  
  
    3.  Kliknij przycisk **Kontynuuj**.  
  
         Zostanie wyświetlone okno dialogowe funkcji Windows.  
  
    4.  Na liście funkcji Rozwiń **Internetowe usługi informacyjne** węzła.  
  
    5.  W obszarze **Internetowe usługi informacyjne**, rozwiń węzeł **usługi World Wide Web** węzła.  
  
    6.  W obszarze **usługi World Wide Web**, kliknij przycisk **zabezpieczeń**.  
  
    7.  Kliknij przycisk **uwierzytelniania Windows**.  
  
    8.  W obszarze **Internetowe usługi informacyjne**, rozwiń węzeł **narzędzia zarządzania siecią Web** węzła.  
  
    9. W obszarze **narzędzia zarządzania siecią Web**, rozwiń węzeł **zgodność z narzędziami zarządzania usług IIS 6** , a następnie wybierz węzeł **metabazy programu IIS 6 i zgodności konfiguracji usług IIS 6** pole wyboru.  
  
    10. W obszarze **narzędzia zarządzania siecią Web**, wybierz opcję **Konsola zarządzania usługami IIS** i kliknij przycisk **OK.**  
  
    11. Uruchom ponownie komputer, aby zmiany zaczęły obowiązywać.  
  
3.  Kliknij przycisk **Start** , a następnie kliknij **Panelu sterowania**.  
  
4.  Kliknij przycisk **Klasyczny**, a następnie kliknij dwukrotnie **narzędzia administracyjne**.  
  
5.  W **nazwa** kolumny i kliknij dwukrotnie plik **Internet Information Services (IIS) Manager**.  
  
6.  W **połączeń** kolumny, rozwiń węzeł serwera.  
  
     A **witryn sieci Web** zostanie otwarty folder poniżej nazwę serwera.  
  
7.  Rozwiń **witryn sieci Web** węzła i kliknij witrynę sieci Web, dla której chcesz włączyć zintegrowane uwierzytelnianie Windows.  
  
8.  Tytuł w środkowym okienku zmienia nazwę wybranej witryny sieci Web. W tym okienku w obszarze **IIS** nagłówek, kliknij dwukrotnie **uwierzytelniania**.  
  
     Zmiany tytułu okienka **uwierzytelniania**.  
  
9. W **uwierzytelniania** okienko w **nazwa** kolumny, kliknij prawym przyciskiem myszy **uwierzytelniania Windows** a następnie kliknij przycisk **Włącz**.  
  
10. Zamknij **Internet Information Services (IIS) Manager** okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Uwierzytelnianie szyfrowane firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Uruchamianie aplikacji sieci Web w systemie Windows Vista z usługami IIS 7.0 i Visual Studio](http://msdn.microsoft.com/library/262a82ac-dd0e-4096-86c6-fb463e88be66)
