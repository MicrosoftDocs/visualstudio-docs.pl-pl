---
title: 'Instrukcje: Debugowanie aplikacji częściowej relacji zaufania | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7864728237e1fc84958d3edea6806508f1339902
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761284"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Instrukcje: Debugowanie aplikacji częściowej relacji zaufania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma zastosowanie do Windows i aplikacji konsoli.  
  
 [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md) ułatwia wdrażanie aplikacji częściowej relacji zaufania, które wykorzystują [zabezpieczenia dostępu kodu](http://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) Aby ograniczyć dostęp do zasobów na komputerze.  
  
 Debugowanie aplikacji częściowego zaufania może stanowić wyzwanie, ponieważ aplikacje częściowo zaufane mają uprawnienia zabezpieczeń (i działają inaczej niż w związku z tym) w zależności od tego, gdzie są one zainstalowane. Jeśli zainstalowany z Internetu, częściowo zaufanych aplikacji będą miały uprawnienia kilka. Jeśli została zainstalowana ze lokalny intranet, mają większe uprawnienia, a jeśli zainstalowane z komputera lokalnego, mają pełne uprawnienia. Mogą również mieć niestandardowej strefy, przy użyciu uprawnień niestandardowych. Może być konieczne debugowanie aplikacji częściowej relacji zaufania w ramach poszczególnych lub wszystkich tych warunków. Na szczęście program Visual Studio ułatwia to również.  
  
 Przed rozpoczęciem sesji debugowania w programie Visual Studio można wybrać strefy chcesz symulować zainstalowaną z aplikacją. Podczas uruchamiania debugowania, aplikacja będzie wymagać uprawnień aplikacji częściowej relacji zaufania, instalowane z tej strefy. Dzięki temu można sprawdzić sposób działania aplikacji, jak będzie wyglądał użytkownikowi, który pobrana z tej strefy.  
  
 Jeśli aplikacja próbuje wykonać akcję, która nie ma uprawnień do, wystąpi wyjątek. W tym momencie Asystent wyjątków daje szansę, aby dodać dodatkowe uprawnienia, która pozwala na ponowne uruchomienie sesji debugowania z wystarczającymi uprawnieniami, aby uniknąć tego problemu.  
  
 Można później, przejdź wstecz i wyświetlić uprawnienia, które dodano podczas debugowania. Gdyby trzeba było dodać uprawnienia podczas debugowania, prawdopodobnie oznacza to, należy dodać użytkownika monitu wyrazić zgodę na tym etapie w kodzie.  
  
> [!NOTE]
>  Wizualizatory debugera wymagają większe uprawnienia niż jest to dozwolone przez aplikację do częściowego zaufania. Wizualizatory nie zostanie załadowany, gdy zostały zatrzymane w kod z częściowej relacji zaufania. Aby debugować za pomocą wizualizatora, należy uruchomić kod z pełnym zaufaniem.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Aby wybrać strefy aplikacji częściowego zaufania  
  
1.  Z **projektu** menu, wybierz _Projectname_**właściwości**.  
  
2.  W *Projectname* strony właściwości, kliknij przycisk **zabezpieczeń** strony.  
  
3.  Wybierz **włączenie ustawień zabezpieczeń technologii ClickOnce**.  
  
4.  W obszarze **strefy, aplikacja zostanie zainstalowana z**, kliknij pole listy rozwijanej i wybierz strefę, którą chcesz symulować aplikacji instalowanych z.  
  
     **Uprawnień wymaganych przez aplikację** siatce są wyświetlane wszystkie dostępne uprawnienia. Znacznik wyboru wskazuje uprawnień udzielonych aplikacji.  
  
5.  Jeśli strefa wybierzesz **(niestandardowy)**, wybierz poprawne ustawienia niestandardowe w **ustawienie** kolumny **uprawnienia** siatki.  
  
6.  Kliknij przycisk **OK** zamknąć na stronach właściwości.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Aby dodać dodatkowe uprawnienia, gdy wystąpi wyjątek zabezpieczeń  
  
1.  **Asystenta wyjątków** pojawi się okno dialogowe z komunikatem: **Securityexception — jest nieobsługiwany.**  
  
2.  W **Asystenta wyjątków** dialogowego **akcje**, kliknij przycisk **Dodaj uprawnienia do projektu**.  
  
3.  **Uruchom ponownie debugowanie** pojawi się okno dialogowe.  
  
    -   Jeśli chcesz ponownie uruchomić sesję debugowania za pomocą nowego uprawnienia, kliknij przycisk **tak**.  
  
    -   Jeśli nie chcesz ponownie uruchomić jeszcze, kliknij przycisk **nie**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Aby wyświetlić dodatkowe uprawnienia dodany podczas debugowania  
  
1.  Z **projektu** menu, wybierz _Projectname_**właściwości**.  
  
2.  W *Projectname* strony właściwości, kliknij przycisk **zabezpieczeń** strony.  
  
3.  Przyjrzyj się **uprawnień wymaganych przez aplikację** siatki. Żadnych dodatkowych uprawnień, możesz dodać ma dwie ikony w **uwzględnione** kolumny: Normalny znacznik wyboru, które dołączane mają uprawnienia i dodatkowe ikonę, która ma postać dymek zawierającej literę "i".  
  
4.  Użyj pionowy pasek przewijania, aby wyświetlić całą **uprawnień wymaganych przez aplikację** siatki.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)
