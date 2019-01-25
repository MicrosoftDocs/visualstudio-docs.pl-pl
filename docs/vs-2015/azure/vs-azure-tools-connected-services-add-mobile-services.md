---
title: Dodawanie usługi Mobile Services przy użyciu usług połączonych
description: Dodawanie usługi Mobile Services za pomocą okna dialogowego programu Visual Studio Dodaj połączone usługi
documentationcenter: na
author: ghogen
manager: jillfra
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 4bfda342952820b4472a1f826273a7b9075faa9a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54756078"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Dodawanie usługi Mobile Services za pomocą programu Visual Studio podłączone usługi
Za pomocą programu Visual Studio 2015, możesz nawiązać połączenie przy użyciu usług Azure Mobile Services **Dodaj podłączoną usługę** okna dialogowego. Możesz połączyć się z dowolnej aplikacji klienckiej języka C#, dowolnej aplikacji JavaScript lub aplikacji Cordova dla wielu platform. Po nawiązaniu połączenia, można utworzyć i uzyskać dostęp do danych, tworzenie niestandardowych interfejsów API i zaplanowane zadania lub dodawać obsługę powiadomień wypychanych.  Operacja usług połączonych dodaje wszystkie odpowiednie odwołania i kod połączenia. Możesz również korzystać z zalet wbudowanej obsługi uwierzytelniania przy użyciu różnych popularnych schematów tożsamości, takiego jak Azure AD, Facebook, Twitter i Accounts firmy Microsoft.

## <a name="supported-project-types"></a>Obsługiwane typy projektów
> [!NOTE]
> W programie Visual Studio 2015 Dodawanie usług Azure Mobile Services do Universal Windows (Windows 10) projektów za pomocą okna dialogowego Dodawanie podłączonych usług nie jest obsługiwane. Możesz dodać usług Azure Mobile Services, poprzez zainstalowanie odpowiednich pakietów przy użyciu Menedżera pakietów NuGet w projekcie.
>
>

Nawiązać połączenia z usług Azure Mobile Services w poniższych typów projektów, można użyć okna dialogowego podłączone usługi.

* Projekty .NET Windows 8.1 Store, Phone i aplikacji uniwersalnych
* JavaScript Windows 8.1 Store, Phone i aplikacji uniwersalnych projektów
* Projekty utworzone za pomocą programu Visual Studio Tools for Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Łączenie usług Azure Mobile Services za pomocą okna dialogowego Dodawanie podłączonych usług
1. Upewnij się, że masz konto platformy Azure. Jeśli nie masz konta platformy Azure, możesz zarejestrować się w celu [bezpłatna wersja próbna](http://go.microsoft.com/fwlink/?LinkId=518146).
2. Otwórz **Dodaj usługi połączone** okno dialogowe.

   * W przypadku aplikacji .NET Otwórz projekt w programie Visual Studio, otwórz menu kontekstowe dla **odwołania** węzła w Eksploratorze rozwiązań, a następnie wybierz **Dodaj podłączoną usługę**

        ![Nawiązywanie połączenia z usługą Azure Mobile Services](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Dla projektów aplikacji Apache Cordova, otwórz projekt w programie Visual Studio, otwórz menu kontekstowe dla węzła projektu w Eksploratorze rozwiązań, a następnie wybierz **Dodaj podłączoną usługę**.
3. W **Dodaj podłączoną usługę** okna dialogowego wybierz **usług Azure Mobile Services**, a następnie wybierz **Konfiguruj** przycisku. Może zostać wyświetlony monit do zalogowania się do platformy Azure, jeśli jeszcze tego nie zrobiłeś.

    ![Dodawanie usługi mobilnej Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. W **usług Azure Mobile Services** okna dialogowego Wybierz istniejącej usługi mobilnej, jeśli nie masz. Jeśli musisz utworzyć nową usługę mobilną systemu Azure, postępuj zgodnie z poniższą procedurą, aby to zrobić. W przeciwnym razie pomiń ten krok i przejdź do następnego kroku.

    Aby utworzyć nowe konto usługi mobilnej:

   1. Wybierz **żądania utworzenia usługi** widocznego u dołu okna dialogowego.
       ![Dodawanie nowej połączonej usługi mobilnej](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. Na **Tworzenie usługi mobilnej** okno dialogowe, można wybrać usługi mobilnej zaplecza JavaScript lub usługi mobilnej zaplecza platformy .NET z **środowiska uruchomieniowego** listy rozwijanej.

       ![Tworzenie usługi mobilnej](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Usługa zaplecza JavaScript jest proste i skuteczne. Po utworzeniu usługi mobilnej zaplecza JavaScript, kodu JavaScript po stronie serwera są przechowywane w chmurze, ale można edytować skrypty serwera za pomocą Eksploratora serwera lub portalu zarządzania systemu Azure.

       Usługi mobilnej zaplecza platformy .NET umożliwia pełną moc i elastyczność interfejsu API sieci Web i Entity Framework. Po utworzeniu usługi mobilnej zaplecza platformy .NET, projekt jest utworzony i dodany do rozwiązania.
   3. Wybierz **Region** gdzie mają usługę mobilną, a następnie wprowadź nazwę użytkownika i hasło dla serwera.
   4. Po wprowadzeniu wymaganych informacji wybierz **Utwórz** przycisk, aby utworzyć usługę mobilną.
   5. Nowej usługi mobilnej powinny pojawić się na liście usług na **usług Azure Mobile Services** okno dialogowe. Wybierz nowej usługi mobilnej na liście, a następnie wybierz **Dodaj** przycisk, aby dodać usługę do projektu.
5. Przejrzyj pobierania z wyświetloną stronę wprowadzenia i Dowiedz się, jak Twój projekt został zmodyfikowany. Strona wprowadzenie jest wyświetlana w przeglądarce, po każdym dodaniu usługi połączonej. Możesz przejrzeć proponowane następne kroki i przykłady kodu lub przejdź do strony co się stało, aby zobaczyć, jakie odwołania zostały dodane do projektu, i jak zostały zmodyfikowane pliki kodu i konfiguracji.
6. Używając przykładów kodu jako wskazówki, zacznij pisanie kodu w celu uzyskania dostępu do usługi mobilnej!

## <a name="how-your-project-is-modified"></a>Jak jest modyfikowana projektu
Jak program Visual Studio modyfikuje projekt zależy od typu projektu. Dla języka C# w aplikacjach klienckich, zobacz [co się stało — projekty języka C#](http://go.microsoft.com/fwlink/p/?LinkId=513119). Dla aplikacji klienckich dla języka JavaScript, zobacz [co się stało — projekty języka JavaScript](http://go.microsoft.com/fwlink/p/?LinkId=513120). W przypadku aplikacji Cordova zobacz [co się stało — projektów Cordova](http://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Następne kroki
Zadawanie pytań i uzyskiwanie pomocy:

* [MSDN Forum: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Usług Azure Mobile Services w blogu zespołu programu Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Usług Azure Mobile Services w witrynie azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Dokumentacja usług Azure Mobile Services w witrynie azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
