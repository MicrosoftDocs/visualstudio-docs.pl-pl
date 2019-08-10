---
title: 'Instrukcje: Odblokuj program Visual Studio'
titleSuffix: ''
ms.date: 03/30/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: fe0aa86be242e9a7e7ed8d877944c66247718167
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926304"
---
# <a name="how-to-unlock-visual-studio"></a>Instrukcje: Odblokuj program Visual Studio

Możesz ocenić programu Visual Studio bezpłatnie do 30 dni. Zalogowanie się do środowiska IDE wydłuża okres próbny do 90 dni. Aby nadal korzystać z programu Visual Studio, Odblokuj środowisko IDE przez:

- Korzystanie z subskrypcji online

- Wprowadzanie klucza produktu

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Aby odblokować program Visual Studio przy użyciu subskrypcji online

Aby odblokować program Visual Studio przy użyciu subskrypcji programu Visual Studio lub organizacji usługi Azure DevOps skojarzonej z konto Microsoft lub konta służbowego:

1. Wybierz przycisk **Zaloguj** w prawym górnym rogu środowiska IDE (lub przejdź do**ustawień konta** **pliku** > , aby otworzyć okno dialogowe **Ustawienia konta** i wybierz przycisk **Zaloguj** ).

1. Wprowadź poświadczenia dla konta Microsoft lub konta służbowego lub szkolnego. Program Visual Studio znajduje subskrypcję programu Visual Studio lub organizację usługi Azure DevOps skojarzoną z Twoim kontem.

> [!IMPORTANT]
> Program Visual Studio automatycznie wyszukuje skojarzone subskrypcje online po nawiązaniu połączenia z organizacją usługi Azure DevOps za pomocą okna narzędzia **Team Explorer** . Po nawiązaniu połączenia z organizacją usługi Azure DevOps możesz zalogować się przy użyciu kont firmy Microsoft i służbowych. Jeśli istnieje subskrypcją w trybie online dla tego konta użytkownika, Visual Studio automatycznie odblokować środowisko IDE dla Ciebie.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Aby odblokować program Visual Studio za pomocą klucza produktu

1. Wybierz pozycję**Ustawienia konta** **pliku** > , aby otworzyć okno dialogowe **Ustawienia konta** , a następnie wybierz **licencję za pomocą linku klucz produktu** .

1. Wprowadź klucz produktu, w tym miejscu.

> [!TIP]
> Wersje wstępne programu Visual Studio nie mają kluczy produktów. Aby korzystać z wersji wstępnych, należy zalogować się do środowiska IDE.

## <a name="address-license-problem-states"></a>Stany problemu z licencją

### <a name="update-stale-licenses"></a>Aktualizowanie starych licencji

Być może zobaczysz następujący komunikat informujący o tym, że Twoja licencja jest przestarzała w programie Visual Studio. Odczytuje, "Twoja licencja stała się przestarzała i należy ją zaktualizować".

![Komunikat o nieodświeżonej licencji programu Visual Studio](../ide/media/vs2017_stale-license.png)

Ten komunikat oznacza, że mimo że subskrypcja może nadal być prawidłowa, token licencji używany przez program Visual Studio w celu zachowania aktualności subskrypcji nie został odświeżony i został usunięty z jednego z następujących powodów:

- Nie korzystasz z programu Visual Studio lub nie masz połączenia z Internetem przez dłuższy czas.
- Nastąpiło wylogowanie programu Visual Studio.

Zanim token licencji zostanie odświeżony, program Visual Studio najpierw wyświetli komunikat ostrzegawczy z prośbą o wprowadzenie poświadczeń.

Jeśli nie wprowadzisz ponownie poświadczeń, token zaczyna się nieodświeżone, a okno dialogowe **Ustawienia konta** informuje o tym, ile dni pozostało do wygaśnięcia tokenu. Po wygaśnięciu tokenu należy ponownie wprowadzić poświadczenia dla konta, aby można było kontynuować korzystanie z programu Visual Studio.

> [!Important]
> Jeśli używasz programu Visual Studio dla rozszerzonych okresów w środowiskach z ograniczeniami lub bez dostępu do Internetu, należy użyć klucza produktu do odblokowania programu Visual Studio, aby uniknąć przerw w działaniu.

### <a name="update-expired-licenses"></a>Aktualizuj wygasłe licencje

Jeśli subskrypcja wygasła całkowicie i nie masz już uprawnień dostępu do programu Visual Studio, musisz odnowić subskrypcję lub dodać kolejne konto z subskrypcją. Aby wyświetlić więcej informacji na temat używanej licencji, przejdź do pozycji**Ustawienia konta** **pliku** > i sprawdź informacje o licencji po prawej stronie okna dialogowego. Jeśli masz inną subskrypcję skojarzoną z innym kontem, Dodaj to konto do listy **wszystkie konta** po lewej stronie okna dialogowego, wybierając łącze **Dodaj konto** .

## <a name="see-also"></a>Zobacz także

* [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md)
