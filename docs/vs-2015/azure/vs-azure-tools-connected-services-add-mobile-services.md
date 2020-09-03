---
title: Dodawanie Mobile Services przy użyciu usług połączonych
description: Dodawanie Mobile Services przy użyciu okna dialogowego Dodawanie usług połączonych programu Visual Studio
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
ms.openlocfilehash: 0a8f6fab3c8f30834a467e2ad98843b16a9245b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916708"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Dodawanie Mobile Services przy użyciu usług połączonych programu Visual Studio
Za pomocą programu Visual Studio 2015 można nawiązać połączenie z usługą Azure Mobile Services przy użyciu okna dialogowego **Dodawanie podłączonej usługi** . Możesz nawiązać połączenie z dowolnej aplikacji klienckiej języka C#, dowolnej aplikacji JavaScript lub wieloplatformowej aplikacji oprogramowania Cordova. Po nawiązaniu połączenia możesz tworzyć i uzyskiwać dostęp do danych, tworzyć niestandardowe interfejsy API i zaplanowane zadania lub dodawać obsługę powiadomień wypychanych.  Operacja usługi połączonej dodaje wszystkie odpowiednie odwołania i kod połączenia. Możesz również skorzystać z wbudowanej obsługi uwierzytelniania przy użyciu różnych popularnych schematów tożsamości, takich jak Azure AD, Facebook, Twitter i konta Microsoft.

## <a name="supported-project-types"></a>Obsługiwane typy projektów
> [!NOTE]
> W programie Visual Studio 2015 Dodawanie Mobile Services platformy Azure do projektów uniwersalnych systemu Windows (Windows 10) przy użyciu okna dialogowego Dodawanie połączonych usług nie jest obsługiwane. Możesz dodać Mobile Services platformy Azure, instalując odpowiednie pakiety przy użyciu Menedżera pakietów NuGet dla projektu.
>
>

Za pomocą okna dialogowego połączone usługi można nawiązać połączenie z usługą Azure Mobile Services w następujących typach projektów.

* Projekty platformy .NET Windows 8.1, telefonu i aplikacji uniwersalnych
* Skrypty JavaScript Windows 8.1 sklepu, telefonu i aplikacji uniwersalnych
* Projekty utworzone przy użyciu Visual Studio Tools dla Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Nawiązywanie połączenia z usługą Azure Mobile Services przy użyciu okna dialogowego Dodawanie połączonych usług
1. Upewnij się, że masz konto platformy Azure. Jeśli nie masz konta platformy Azure, możesz zarejestrować się, aby skorzystać z [bezpłatnej wersji próbnej](https://azure.microsoft.com/pricing/free-trial/).
2. Otwórz okno dialogowe **Dodawanie połączonych usług** .

   * W przypadku aplikacji .NET Otwórz projekt w programie Visual Studio, otwórz menu kontekstowe dla węzła **odwołania** w Eksplorator rozwiązań, a następnie wybierz polecenie **Dodaj podłączoną usługę**

        ![Nawiązywanie połączenia z usługą Azure Mobile Service](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * W przypadku projektów aplikacji Apache Cordova Otwórz projekt w programie Visual Studio, otwórz menu kontekstowe dla węzła projektu w Eksplorator rozwiązań, a następnie wybierz polecenie **Dodaj podłączoną usługę**.
3. W oknie dialogowym **Dodawanie podłączonej usługi** wybierz pozycję **Azure Mobile Services**, a następnie wybierz przycisk **Konfiguruj** . Jeśli jeszcze tego nie zrobiono, może zostać wyświetlony monit o zalogowanie się do platformy Azure.

    ![Dodawanie usługi mobilnej Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. W oknie dialogowym **Mobile Services platformy Azure** wybierz istniejącą usługę mobilną, jeśli ją masz. Jeśli musisz utworzyć nową usługę Azure Mobile Service, postępuj zgodnie z poniższą procedurą. W przeciwnym razie pomiń ten krok i przejdź do następnego kroku.

    Aby utworzyć nowe konto usługi mobilnej:

   1. Wybierz łącze **Utwórz usługę** u dołu okna dialogowego.
       ![Dodawanie nowej usługi połączonej z urządzeniami przenośnymi](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. W oknie dialogowym **Tworzenie usługi mobilnej** możesz wybrać usługę mobilną w języku JavaScript lub usługę mobilną .NET zaplecza z listy rozwijanej **środowisko uruchomieniowe** .

       ![Tworzenie usługi mobilnej](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Usługa zaplecza JavaScript jest prosta i wydajna. W przypadku tworzenia usługi mobilnej zaplecza języka JavaScript kod JavaScript po stronie serwera jest przechowywany w chmurze, ale skrypty serwera można edytować za pomocą Eksplorator serwera lub portalu zarządzania Azure.

       Usługa mobilna zaplecza platformy .NET zapewnia pełną moc i elastyczność interfejsu API sieci Web i Entity Framework. W przypadku utworzenia usługi mobilnej zaplecza platformy .NET projekt zostanie utworzony dla Ciebie i dodany do rozwiązania.
   3. Wybierz region, w którym ma zostać **wyświetlona** usługa mobilna, a następnie wprowadź nazwę użytkownika i hasło dla serwera.
   4. Po wprowadzeniu wszystkich wymaganych informacji wybierz przycisk **Utwórz** , aby utworzyć usługę mobilną.
   5. Nowa usługa mobilna powinna pojawić się na liście usług w oknie dialogowym **Azure Mobile Services** . Wybierz nową usługę mobilną z listy, a następnie wybierz przycisk **Dodaj** , aby dodać usługę do projektu.
5. Zapoznaj się z wyświetlaną stroną Wprowadzenie i Dowiedz się, w jaki sposób projekt został zmodyfikowany. W przeglądarce zostanie wyświetlona strona Wprowadzenie po dodaniu połączonej usługi. Możesz przejrzeć sugerowane następne kroki i przykłady kodu lub przełączyć się na stronę co się stało, aby zobaczyć, jakie odwołania zostały dodane do projektu, oraz jak zmodyfikowano kod i pliki konfiguracji.
6. Korzystając z przykładów kodu jako przewodnika, zacznij pisać kod, aby uzyskać dostęp do usługi mobilnej.

## <a name="next-steps"></a>Następne kroki
Zadawaj pytania i uzyskaj pomoc:

* [Forum MSDN: Mobile Services platformy Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Mobile Services platformy Azure na blogu zespołu Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Mobile Services platformy Azure pod adresem azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Dokumentacja usługi Azure Mobile Services w witrynie azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
