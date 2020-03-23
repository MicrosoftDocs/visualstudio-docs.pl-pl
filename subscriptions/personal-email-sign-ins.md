---
title: Osobiste wiadomości e-mail wyświetlane w vlsc
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 03/17/2020
ms.topic: conceptual
description: Subskrypcje programu Visual Studio — dlaczego widzę adresy Hotmail lub Gmail dla moich subskrybentów?
ms.openlocfilehash: 7cd6a4761efb7dcad7568bd0a95ba33141407055
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "79550333"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Subskrypcje programu Visual Studio — dlaczego widzę konta osobiste subskrybentów?
Po migracji firm z Centrum usług licencjonowania zbiorowego (VLSC) do nowego [portalu administracyjnego subskrypcji](https://manage.visualstudio.com)programu Visual Studio administratorzy byli zaskoczeni, że "Adres e-mail logowania" dla niektórych subskrybentów zawiera osobisty adres e-mail, taki jak Hotmail lub Outlook.  Aby uzyskać więcej informacji, zapoznaj się z [tym filmem](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Przyczyna
Ten scenariusz występuje z powodu procesów logowania, które były skojarzone z starszego środowiska subskrybenta MSDN. Użytkownicy zostali migrowani z Centrum usług licencji zbiorczych (VLSC) do portalu administracyjnego subskrypcji programu Visual Studio bez modyfikacji. Administratorzy mogli nie wiedzieć, że użytkownicy korzystali z kont osobistych w celu uzyskania dostępu do korzyści z subskrypcji. Przed migracjami subskrybentów programu Visual Studio, które zostały ukończone w 2016 r., istniały dwie akcje wymagane do pomyślnego użycia subskrypcji programu Visual Studio:
1. Administrator "przypisał" subskrypcję poszczególnym subskrybentom, używając służbowego adresu e-mail.
2. Subskrybent "aktywował" subskrypcję.

Podczas procesu aktywacji subskrybenta: do zalogowania się wymagane było konto Microsoft (MSA). Jeśli subskrybent nie próbował utworzyć konta służbowego (np. tasha@contoso.com) msa, może utworzyć nowy MSA lub wykorzystać istniejące. Spowodowało to, że ich "Adres e-mail logowania" różni się od "Przypisany do adresu e-mail".

> [!NOTE]
> Nowoczesne środowisko subskrybenta [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) obsługuje zarówno typy tożsamości usługi Praca/Szkoła, jak i Konto Microsoft (MSA).

## <a name="solution"></a>Rozwiązanie
Aby rozwiązać ten problem, po prostu wybierz przycisk **Połącz wiadomości e-mail,** a system spróbuje dopasować konta z msa do istniejących użytkowników w usłudze Azure Active Directory (Azure AD) organizacji na podstawie dopasowania imienia i nazwiska. Jeśli wystąpi błąd, możesz usunąć dowolne dopasowanie, klikając **x** po prawej stronie meczu.  

> [!div class="mx-imgBorder"]
> ![Przycisk Połącz e-maile](_img/connect-emails/connect-emails-button.png)

Można również użyć **katalogu wyszukiwania,** aby poprawić błędy lub wypełnić brakujące informacje z usługi Azure AD. Jeśli wszystkie dopasowania wyglądają poprawnie, możesz wybrać opcję "Wybierz wszystkich pasujących subskrybentów", zamiast wybierać je po jednym naraz.  

> [!div class="mx-imgBorder"]
> ![Łączenie wiadomości e-mail wylatuje](_img/connect-emails/connect-emails-flyout.png)

Następnie kliknij na "kontynuuj", który zabierze Cię do ekranu przedstawiającego zmiany, które mają się odbyć. Jeśli wyrazisz na to zgodę, kliknij przycisk "Zapisz", a zmiany zostaną wprowadzone. Subskrybent otrzyma również wiadomość informującą o zmianie przy następnym logowaniu się do subskrypcji.   

> [!div class="mx-imgBorder"]
> ![Połącz e-maile z potwierdzeniem](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Podczas edytowania adresu e-mail logowania jest to tylko aktualizacja wiadomości e-mail https://my.visualstudio.comużywanej przez subskrybenta do logowania się do subskrypcji w programie . Jeśli subskrybent ma już aktywowane korzyści, takie jak Azure lub Pluralsight przy użyciu innego adresu e-mail, będą musieli nadal używać tych adresów e-mail, aby uzyskać do nich dostęp. W przypadku nowych korzyści, do których uzyskują dostęp, powinni użyć nowego adresu e-mail. 

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>Następne kroki
- Jeśli zaktualizowano adres(y) e-mail subskrybenta(-ów), możesz powiadomić ich o zmianie informacji o logowaniu.  Otrzymają również wiadomość e-mail ze zaktualizowanymi informacjami.
- Może być przydatne [filtrowanie listy subskrybentów](search-license.md) w organizacji, aby wyszukać wszelkie logowania adresy e-mail, które mogą wymagać zmiany.  
