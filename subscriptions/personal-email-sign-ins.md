---
title: Osobiste wiadomości e-mail wyświetlane w VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 04/10/2020
ms.topic: conceptual
description: Subskrypcje programu Visual Studio — Dlaczego widzę adresy Hotmail i Gmail dla subskrybentów?
ms.openlocfilehash: 44b18bd46d55349fae5a3ece03cee9fe93240148
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "81223687"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Subskrypcje programu Visual Studio — Dlaczego widzę konta osobiste dla moich subskrybentów?
Po przeprowadzeniu migracji z witryny Volume Licensing Service Center (VLSC) do nowego [portalu administratora subskrypcji](https://manage.visualstudio.com)programu Visual Studio Administratorzy mogli znaleźć, że adres e-mail logowania dla niektórych subskrybentów pokazuje osobisty adres e-mail, taki jak Hotmail lub Outlook.  

## <a name="cause"></a>Przyczyna
Ten scenariusz występuje ze względu na procesy logowania skojarzone ze starszym doświadczeniem subskrybenta MSDN. Użytkownicy zostali zmigrowani z witryny Volume License Service Center (VLSC) do portalu administracyjnego subskrypcji programu Visual Studio bez żadnych modyfikacji. Administratorzy mogą nie wiedzieć, że użytkownicy korzystali z kont osobistych w celu uzyskania dostępu do korzyści z subskrypcji. Przed migracją subskrybentów programu Visual Studio, które zostały wykonane w 2016, były dwie akcje wymagane do pomyślnego użycia Visual Studio Subscription:
1. Administrator "przypisał" subskrypcję do indywidualnego subskrybenta przy użyciu służbowego adresu e-mail.
2. Subskrybent "aktywowany" w ramach subskrypcji.

Podczas procesu aktywacji subskrybenta: konto Microsoft (MSA) było wymagane do zalogowania się. Jeśli subskrybent nie podjął próby przeprowadzenia konta służbowego (np. tasha@contoso.com ) jako elementu MSA, może utworzyć nowy element MSA lub wykorzystać istniejący. W związku z tym "adres E-mail logowania" jest inny niż przypisany do adresu E-mail.

> [!NOTE]
> Nowoczesne środowisko subskrybenta w systemie [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) obsługuje typy tożsamości zarówno służbowe, jak i konto Microsoft (MSA).

## <a name="solution"></a>Rozwiązanie

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

Aby rozwiązać ten problem, po prostu wybierz przycisk **Połącz wiadomości e-mail** , a system podejmie próbę dopasowania kont z kont MSA do istniejących użytkowników w organizacji Azure Active Directory (Azure AD) w oparciu o pasujące imię i nazwisko. Jeśli wystąpi błąd, możesz usunąć dowolne dopasowanie, klikając **znak X** z prawej strony dopasowania.  

> [!div class="mx-imgBorder"]
> ![Przycisk Połącz wiadomości E-mail](_img/connect-emails/connect-emails-button.png)

Możesz również użyć **katalogu wyszukiwania** , aby naprawić błędy lub uzupełnić brakujące informacje z usługi Azure AD. Jeśli wszystkie dopasowania wyglądają prawidłowo, możesz wybrać opcję "Wybierz wszystkich pasujących subskrybentów" zamiast wybierać je pojedynczo.  

> [!div class="mx-imgBorder"]
> ![Nawiązywanie połączenia z wiadomościami E-mail](_img/connect-emails/connect-emails-flyout.png)

Następnie kliknij pozycję "Kontynuuj", co spowoduje przejście do ekranu, który wprowadza zmiany, które mają zostać wykonane. Jeśli zgadzasz się, kliknij przycisk "Zapisz", a zmiany zostaną wprowadzone. Subskrybent otrzyma również komunikat z informacją o zmianie przy następnym logowaniu do swojej subskrypcji.   

> [!div class="mx-imgBorder"]
> ![Potwierdzenie łączenia wiadomości E-mail](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Podczas edytowania adresu e-mail należy tylko zaktualizować wiadomość e-mail używaną przez subskrybenta, aby zalogować się do swojej subskrypcji https://my.visualstudio.com . Jeśli subskrybent ma już aktywowane korzyści, takie jak Azure lub Pluralsight przy użyciu innego adresu e-mail, będzie musiał nadal korzystać z tych adresów e-mail w celu uzyskania dostępu do nich. W przypadku nowych korzyści, do których mają dostęp, powinny być używane nowe adresy e-mail. 

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja Microsoft 365](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>Następne kroki
- Jeśli Zaktualizowano adresy e-mail subskrybentów, można powiadomić ich, że informacje logowania zostały zmienione.  Otrzymają także wiadomość e-mail z zaktualizowanymi informacjami.
- Przydatne może być [odfiltrowanie listy subskrybentów](search-license.md) w organizacji, aby wyszukać wszelkie adresy e-mail logowania, które mogą wymagać zmiany.  
