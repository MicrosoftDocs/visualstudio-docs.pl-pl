---
title: Rozszerzanie wersji próbnej lub aktualizowanie licencji
description: Dowiedz się, jak zwiększyć bezpłatną wersję próbną programu Visual Studio, użyć subskrypcji online lub klucza produktu, aby odblokować program Visual Studio i zaktualizować przestarzałą lub wygasłą licencję.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: db0f75b3e4c2f066b7a9d79976a50efd3364d7bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591375"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Rozszerzanie wersji próbnej lub aktualizowanie licencji

Możesz oszacować bezpłatną wersję próbną [Visual Studio Professional lub Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) przez 30 dni. Jeśli zalogujesz się, możesz zwiększyć okres próbny do 90 dni. (Program Visual Studio Community jest bezpłatny bez okresu próbnego. Należy jednak [zalogować](signing-in-to-visual-studio.md) się okresowo, aby zapewnić aktualność [licencji](#update-a-stale-license).

Aby nadal korzystać z programu Visual Studio po zakończeniu okresu próbnego, Odblokuj go z [subskrypcją online](#use-an-online-subscription) lub [kluczem produktu](#enter-a-product-key).

## <a name="use-an-online-subscription"></a>Korzystanie z subskrypcji online

1. Wybierz przycisk **Zaloguj** w prawym górnym rogu środowiska IDE (lub przejdź do **pliku** > **Ustawienia konta** , aby otworzyć okno dialogowe **Ustawienia konta** , a następnie wybierz przycisk **Zaloguj się** ).

1. Wprowadź poświadczenia dla konta Microsoft lub konta służbowego lub szkolnego. Program Visual Studio znajduje subskrypcję programu Visual Studio lub organizację usługi Azure DevOps skojarzoną z Twoim kontem.

> [!IMPORTANT]
> Program Visual Studio automatycznie wyszukuje skojarzone subskrypcje online po nawiązaniu połączenia z organizacją usługi Azure DevOps za pomocą okna narzędzia **Team Explorer** . Po nawiązaniu połączenia z organizacją usługi Azure DevOps możesz zalogować się przy użyciu kont firmy Microsoft i służbowych. Jeśli istnieje subskrypcją w trybie online dla tego konta użytkownika, Visual Studio automatycznie odblokować środowisko IDE dla Ciebie.

Aby uzyskać więcej informacji o subskrypcjach programu Visual Studio i sposobie ich działania, zobacz stronę [często zadawanych pytań dotyczących subskrypcji](https://visualstudio.microsoft.com/subscriptions/support/) .

## <a name="enter-a-product-key"></a>Wprowadzanie klucza produktu

1. Wybierz pozycję plik **Ustawienia konta** > , aby otworzyć okno dialogowe **Ustawienia konta** , a następnie wybierz **licencję za pomocą linku klucz produktu** .

1. Wprowadź klucz produktu, w tym miejscu.

> [!TIP]
> Wersje wstępne programu Visual Studio nie mają kluczy produktów. Aby korzystać z wersji wstępnych, należy zalogować się do środowiska IDE.

Więcej informacji o kluczach produktów programu Visual Studio dla programu Visual Studio i sposobach ich uzyskania można znaleźć na stronie [Korzystanie z kluczy produktów w subskrypcjach programu Visual Studio](/visualstudio/subscriptions/product-keys) .

## <a name="update-a-stale-license"></a>Aktualizowanie starej licencji

W programie Visual Studio może zostać wyświetlony komunikat "Twoja licencja została nieodświeżona i należy ją zaktualizować".

![Komunikat o nieodświeżonej licencji programu Visual Studio](../ide/media/vs2017_stale-license.png)

Ten komunikat oznacza, że w przypadku, gdy subskrypcja może nadal być prawidłowa, token licencji używany przez program Visual Studio do zapewnienia aktualności subskrypcji nie został odświeżony. Program Visual Studio zgłasza, że licencja jest nieodświeżona z jednego z następujących powodów:

* Nie korzystasz z programu Visual Studio lub nie masz połączenia z Internetem przez dłuższy czas.
* Nastąpiło wylogowanie programu Visual Studio.

Zanim token licencji zostanie odświeżony, program Visual Studio najpierw wyświetli komunikat ostrzegawczy z prośbą o wprowadzenie poświadczeń.

Jeśli nie wprowadzisz ponownie poświadczeń, token zaczyna się nieodświeżone, a okno dialogowe **Ustawienia konta** informuje o liczbie dni pozostałych przed wygaśnięciem tokenu. Po wygaśnięciu tokenu należy ponownie wprowadzić poświadczenia dla konta, aby można było kontynuować korzystanie z programu Visual Studio.

> [!Important]
> Jeśli używasz programu Visual Studio dla rozszerzonych okresów w środowiskach z ograniczeniami lub bez dostępu do Internetu, należy użyć klucza produktu do odblokowania programu Visual Studio, aby uniknąć przerw w działaniu.

## <a name="update-an-expired-license"></a>Aktualizowanie wygasłej licencji

Jeśli Twoja subskrypcja wygasła i nie masz już uprawnień dostępu do programu Visual Studio, musisz odnowić subskrypcję lub dodać kolejne konto z subskrypcją. Aby wyświetlić więcej informacji na temat używanej licencji, przejdź do **pliku** > **Ustawienia konta** i przejrzyj informacje o licencji po prawej stronie okna dialogowego. Jeśli masz inną subskrypcję skojarzoną z innym kontem, Dodaj to konto do listy **wszystkie konta** po lewej stronie okna dialogowego, wybierając łącze **Dodaj konto** .

## <a name="get-support"></a>Uzyskaj pomoc techniczną

Czasami problemy są nieprawidłowe. Jeśli wystąpi problem, poniżej przedstawiono niektóre opcje pomocy technicznej:

* Zgłoś problemy dotyczące produktów za pomocą narzędzia [Zgłoś problem](how-to-report-a-problem-with-visual-studio.md) .
* Znajdź odpowiedzi na pytania dotyczące subskrypcji, kont i rozliczeń w ramach [subskrypcji — często zadawane pytania](https://visualstudio.microsoft.com/subscriptions/support/).

## <a name="see-also"></a>Zobacz także

* [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md)
* [Porównanie wersji programu Visual Studio](https://visualstudio.microsoft.com/vs/compare/)
* [Dowiedz się więcej o subskrypcjach programu Visual Studio](/visualstudio/subscriptions/)
