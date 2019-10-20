---
title: Odblokuj program Visual Studio 2015 | Microsoft Docs "
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a71a045661c48fd36733ecd8d2266470667a5c35
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670595"
---
# <a name="how-to-unlock-visual-studio"></a>Jak odblokować program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio można oszacować bezpłatnie do 30 dni. Po zalogowaniu się do środowiska IDE można zwiększyć okres próbny o 90 dni. Aby nadal korzystać z programu Visual Studio, możesz odblokować środowisko IDE przez

1. Korzystanie z subskrypcji online.

2. Wprowadzanie klucza produktu.

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Aby odblokować program Visual Studio przy użyciu subskrypcji online
 Aby odblokować program Visual Studio przy użyciu subskrypcji MSDN lub Visual Studio Online skojarzonej z konto Microsoft lub konta służbowego:

1. Kliknij przycisk "Zaloguj się" w prawym górnym rogu środowiska IDE (lub przejdź do pliku > Ustawienia konta, aby otworzyć okno dialogowe Ustawienia konta, a następnie kliknij przycisk "Zaloguj").

2. Wprowadź poświadczenia dla konto Microsoft lub konta służbowego. Program Visual Studio znajdzie subskrypcję MSDN lub subskrypcję Visual Studio Team Services skojarzoną z Twoim kontem.

> [!IMPORTANT]
> Program Visual Studio automatycznie wyszukuje skojarzone subskrypcje online po nawiązaniu połączenia z kontem Visual Studio Team Services z okna narzędzia Team Explorer. Po nawiązaniu połączenia z kontem Visual Studio Team Services możesz zalogować się przy użyciu kont Microsoft i służbowych. Jeśli dla tego konta użytkownika istnieje subskrypcja online, program Visual Studio automatycznie odblokuje środowisko IDE.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Aby odblokować program Visual Studio przy użyciu klucza produktu

1. Wybierz pozycję **plik ustawienia konta >** , aby otworzyć okno dialogowe Ustawienia konta, a następnie kliknij link "**Licencja z kluczem produktu**".

2. Wprowadź klucz produktu w udostępnionym obszarze.

> [!TIP]
> Wersje wstępne programu Visual Studio nie mają kluczy produktów. Aby użyć wersji wstępnych, należy zalogować się do środowiska IDE.

## <a name="addressing-license-problem-states"></a>Rozwiązywanie problemów z licencją

### <a name="updating-stale-licenses"></a>Aktualizowanie starych licencji
 Być może zobaczysz poniższy komunikat, że Twoja licencja jest przestarzała w programie Visual Studio.

 ![Okno dialogowe informacji o użytkowniku programu Visual Studio](../ide/media/vs2013-userinfo.png "VS2013_UserInfo")

 Ten komunikat oznacza, że mimo że subskrypcja może nadal być prawidłowa, token licencji używany przez program Visual Studio w celu zachowania aktualności subskrypcji nie został odświeżony i został usunięty z jednego z następujących powodów:

1. Nie korzystasz z programu Visual Studio lub nie masz połączenia z Internetem przez dłuższy czas.

2. Wylogowano Cię z programu Visual Studio.

   Zanim token licencji zostanie odświeżony, program Visual Studio najpierw wyświetli komunikat ostrzegawczy z prośbą o ponowne wprowadzenie poświadczeń.

   Jeśli nie wprowadzisz ponownie poświadczeń, token zaczyna się nieodświeżony. W takim przypadku okno dialogowe Ustawienia konta informuje o liczbie dni, po których token pozostał w pełni wygasa. Po wygaśnięciu tokenu należy ponownie wprowadzić poświadczenia dla tego konta lub licencji z inną metodą powyżej, aby można było kontynuować korzystanie z programu Visual Studio.

> [!IMPORTANT]
> Jeśli używasz programu Visual Studio dla rozszerzonych okresów w środowiskach z ograniczeniami lub bez dostępu do Internetu, należy użyć klucza produktu do odblokowania programu Visual Studio w celu uniknięcia przerw w działaniu.

### <a name="updating-expired-licenses"></a>Aktualizowanie wygasłych licencji
 Jeśli subskrypcja wygasła całkowicie i nie masz już uprawnień dostępu do programu Visual Studio, musisz:

1. Odnów subskrypcję. Aby wyświetlić więcej informacji na temat używanej licencji, przejdź do okna dialogowego Ustawienia konta > i sprawdź informacje o licencji znajdujące się po prawej stronie okna dialogowego.

2. Jeśli masz inną subskrypcję skojarzoną z innym kontem, Dodaj to konto do listy wszystkie konta po lewej stronie okna dialogowego ustawień konta > pliku, klikając pozycję "Dodaj konto..." powiązań.

## <a name="see-also"></a>Zobacz też
 [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md)
