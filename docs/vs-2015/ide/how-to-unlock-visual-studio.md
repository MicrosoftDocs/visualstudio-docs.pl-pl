---
title: Odblokowanie programu Visual Studio 2015 | Dokumentacja firmy Microsoft"
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8876cebf5851454aa3140f6a3269fa0d3ecbbc95
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774546"
---
# <a name="how-to-unlock-visual-studio"></a>Jak odblokować program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz ocenić programu Visual Studio bezpłatnie do 30 dni. Po zalogowaniu się do środowiska IDE można rozszerzyć okresu próbnego o 90 dni. Aby kontynuować korzystanie z programu Visual Studio można odblokować środowisko IDE przez

1.  za pomocą subskrypcją w trybie online.

2.  wprowadzanie klucza produktu.

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Aby odblokować programu Visual Studio z subskrypcją w trybie online
 Odblokować program Visual Studio przy użyciu subskrypcji MSDN lub Visual Studio online skojarzone z kontem Microsoft lub konta służbowego lub szkolnego:

1.  Kliknij przycisk "Sign in" w prawym górnym rogu IDE (lub przejdź do pliku > Ustawienia konta, aby otworzyć okno dialogowe Ustawienia konta, a następnie kliknij przycisk "Zaloguj".)

2.  Wprowadź poświadczenia dla konta Microsoft lub konta służbowego lub szkolnego. Program Visual Studio znajdzie subskrypcję MSDN lub Visual Studio Team Services skojarzonych z Twoim kontem.

> [!IMPORTANT]
>  Program Visual Studio automatycznie wyszuka skojarzone subskrypcje w trybie online, po nawiązaniu połączenia z kontem usługi Visual Studio Team Services z okna narzędzia Team Explorer. Po nawiązaniu połączenia z kontem usługi Visual Studio Team Services, możesz zalogować się przy użyciu Microsoft i jej pracy lub kont służbowych. Jeśli istnieje subskrypcją w trybie online dla tego konta użytkownika, Visual Studio automatycznie odblokować środowisko IDE dla Ciebie.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Aby odblokować program Visual Studio za pomocą klucza produktu

1.  Wybierz **Plik > Ustawienia konta** aby otworzyć okno dialogowe Ustawienia konta i kliknij "**licencji za pomocą klucza produktu**" link.

2.  Wprowadź klucz produktu, w tym miejscu.

> [!TIP]
>  Wersje wstępne programu Visual Studio nie ma kluczy produktów. Musisz się zarejestrować się do IDE na używanie wersji wstępnej.

## <a name="addressing-license-problem-states"></a>Adresowanie stanów Problem licencji

### <a name="updating-stale-licenses"></a>Aktualizowanie starych licencji
 Można było zaobserwować poniżej komunikat licencja będzie przestarzałe w programie Visual Studio.

 ![Okno dialogowe informacji użytkownika programu Visual Studio](../ide/media/vs2013-userinfo.png "VS2013_UserInfo")

 Ten komunikat oznacza, że gdy Twoja subskrypcja może nadal znajdować się prawidłowy token program Visual Studio używa na bieżąco swoją subskrypcję licencji nie została odświeżona i stała się przestarzała z jednego z następujących powodów:

1. Bez użycia programu Visual Studio lub mieli Brak połączenia internetowego, Przedłuż okres.

2. Nastąpiło wylogowanie programu Visual Studio.

   Token licencji przejdzie starych, Visual Studio najpierw wyświetli ostrzeżenie komunikat z prośbą o ponowne wprowadzenie poświadczeń.

   Jeśli nie ponownie wprowadzić swoje poświadczenia token zostanie uruchomiony do starych. W takim przypadku okno dialogowe Ustawienia konta informujący o tym ile dni pozostało przed pełni wygaśnięcia tokenu. Po wygaśnięciu tokenu programu, należy ponownie wprowadzić swoje poświadczenia dla tego konta lub aktywnej licencji przy użyciu innej metody powyżej, przed kontynuowaniem za pomocą programu Visual Studio.

> [!IMPORTANT]
>  Jeśli używasz programu Visual Studio przez dłuższy czas, w środowiskach o ograniczonym lub Brak dostępu do Internetu, należy użyć klucza produktu odblokować program Visual Studio, aby uniknąć przerw w działaniu.

### <a name="updating-expired-licenses"></a>Aktualizowanie wygasłych licencji
 Jeśli Twoja subskrypcja wygasła całkowicie i nie jest już prawa dostępu do programu Visual Studio, musisz mieć:

1.  Odnów subskrypcję. Aby uzyskać więcej informacji o licencji, którego używasz, przejdź do pliku > okno dialogowe Ustawienia konta i spójrz na informacje o licencjach po prawej stronie okna dialogowego.

2.  Jeśli masz inną subskrypcję skojarzony z innym kontem, należy dodać to konto do listy wszystkich kont po lewej stronie w pliku > okno dialogowe Ustawienia konta, klikając polecenie "Dodaj konto..." link.

## <a name="see-also"></a>Zobacz też
 [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md)
