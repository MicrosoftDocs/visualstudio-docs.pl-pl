---
title: 'Instrukcje: Odblokować program Visual Studio'
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
ms.openlocfilehash: 2bb6de32188abb11e0286c200383bdb1e8fb12f7
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58856823"
---
# <a name="how-to-unlock-visual-studio"></a>Instrukcje: Odblokować program Visual Studio

Możesz ocenić programu Visual Studio bezpłatnie do 30 dni. Logując się do IDE przedłuża okres próbny 90 dni. Aby nadal korzystać z programu Visual Studio, należy odblokować środowisko IDE przez:

- za pomocą subskrypcją w trybie online

- wprowadzanie klucza produktu

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Aby odblokować program Visual Studio przy użyciu subskrypcją w trybie online

Odblokować program Visual Studio przy użyciu subskrypcji programu Visual Studio lub organizacja DevOps platformy Azure skojarzone z kontem Microsoft lub konta służbowego lub szkolnego:

1. Wybierz **Zaloguj** przycisk w prawym górnym rogu IDE (lub przejdź do **pliku** > **ustawienia konta** otworzyć **ustawienia konta**  okna dialogowego i wybierz polecenie **Zaloguj** przycisk).

1. Wprowadź poświadczenia dla konta Microsoft lub konta służbowego lub szkolnego. Program Visual Studio znajdzie subskrypcji programu Visual Studio lub organizację DevOps platformy Azure skojarzony z Twoim kontem.

> [!IMPORTANT]
> Program Visual Studio automatycznie wyszuka skojarzone subskrypcje w trybie online podczas łączenia z organizacji DevOps platformy Azure z **Team Explorer** okna narzędzi. Po nawiązaniu połączenia z organizacją DevOps platformy Azure, możesz zalogować się przy użyciu Microsoft i jej pracy lub kont służbowych. Jeśli istnieje subskrypcją w trybie online dla tego konta użytkownika, Visual Studio automatycznie odblokować środowisko IDE dla Ciebie.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Aby odblokować program Visual Studio za pomocą klucza produktu

1. Wybierz **pliku** > **ustawienia konta** otworzyć **ustawienia konta** okno dialogowe, a następnie wybierz **licencji za pomocą klucza produktu** łącza.

1. Wprowadź klucz produktu, w tym miejscu.

> [!TIP]
> Wersje wstępne programu Visual Studio nie ma kluczy produktów. Musisz się zalogować do środowiska IDE programu do użycia wersji wstępnych.

## <a name="address-license-problem-states"></a>Stany problem licencji adresów

### <a name="update-stale-licenses"></a>Aktualizowanie starych licencji

 Możesz już znać następujący komunikat informujący o tym, czy Twoja licencja będzie przestarzałe w programie Visual Studio. Odczytuje, "licencja stała się przestarzała i trzeba ją zaktualizować."

 ![Visual Studio starych licencji wiadomości](../ide/media/vs2017_stale-license.png)

 Ten komunikat oznacza, że gdy Twoja subskrypcja może nadal znajdować się prawidłowy token program Visual Studio używa na bieżąco swoją subskrypcję licencji nie została odświeżona i stała się przestarzała z jednego z następujących powodów:

- Bez użycia programu Visual Studio lub mieli Brak połączenia z Internetem przez dłuższy czas.
- Nastąpiło wylogowanie programu Visual Studio.

Token licencji przejdzie starych, Visual Studio wyświetla najpierw ostrzeżenie informujące, że należy ponownie wprowadzić swoje poświadczenia.

Jeśli nie ponownie wprowadzić swoje poświadczenia, token rozpoczyna się do starych i **ustawienia konta** okno dialogowe informuje o ile dni pozostało przed pełni wygaśnięcia tokenu. Po wygaśnięciu tokenu programu musi ponownie wprowadzić swoje poświadczenia dla konta, zanim będzie można kontynuować przy użyciu programu Visual Studio.

> [!Important]
> Jeśli używasz programu Visual Studio przez dłuższy czas, w środowiskach o ograniczonym lub Brak dostępu do Internetu, należy użyć klucza produktu odblokować program Visual Studio, aby uniknąć przerw w działaniu.

### <a name="update-expired-licenses"></a>Wygasłe licencji

 Jeśli Twoja subskrypcja wygasła całkowicie i nie jest już prawa dostępu do programu Visual Studio, musisz odnowić subskrypcję lub Dodaj inne konto, które ma subskrypcję. Aby uzyskać więcej informacji o licencji, którego używasz, przejdź do **pliku** > **ustawienia konta** i przyjrzyj się informacje o licencjach po prawej stronie okna dialogowego. Jeśli masz inną subskrypcję skojarzony z innym kontem, należy dodać to konto do **wszystkich kont** liście po lewej stronie okna dialogowego wybierając **Dodaj konto** łącza.

## <a name="see-also"></a>Zobacz także

* [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md)
