---
title: Refaktoryzacja kodu
description: Ponowne organizowanie kodu w programie Visual Studio dla komputerów Mac jest proste za pomocą analizy źródła.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 7b11f09d8fb70612d4496987f69583b2ac691275
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985235"
---
# <a name="refactoring"></a>Refaktoryzacja

Refaktoryzacja kodu jest sposobem, aby zmienić rozmieszczenie, restrukturyzacji i wyjaśnienia istniejącego kodu, zapewniając jednocześnie, że ogólne zachowanie kodu nie zmienia.

Refaktoryzowanie tworzy zdrowszą bazę kodu, dzięki czemu jest bardziej użyteczny, czytelny i owalny dla Ciebie lub innego dewelopera lub użytkownika, który może odnosić się do kodu.

Integracja programu Visual Studio for Mac z Roslyn, platformą kompilatora .NET typu open source firmy Microsoft, umożliwia więcej operacji refaktoryzacji.

## <a name="renaming"></a>Zmienianie nazw

Polecenie *Zmień nazwę* refaktoryzacji może służyć do dowolnego identyfikatora kodu (na przykład nazwa klasy, nazwa właściwości itp.), aby znaleźć wszystkie wystąpienia tego identyfikatora i zmienić je. Aby zmienić nazwę symbolu, kliknij go prawym przyciskiem myszy i wybierz polecenie **Refaktor > Zmień nazwę**lub powiązanie **klawiszy Cmd + R:**

![Zmienianie nazwy elementu menu](media/refactoring-renaming1.png)

To wyróżnia symbol i wszelkie odniesienia do niego. Po rozpoczęciu wpisywania nowej nazwy automatycznie zmienia wszystkie odwołania w kodzie i można zasygnalizować zakończenie zmiany nazwy, naciskając **klawisz Enter:**

![Zmiana nazwy i identyfikator](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Akcje kontekstowe

Akcje kontekstu umożliwiają sprawdzenie dowolnego kodu języka C# i zobacz wszystkie możliwe opcje refaktoryzacji.

Elementy kontekstu **Rozpoznawania** i **refaktoryzowania** są łączone w jeden element *Quick Fix...,* który zapewni Ci wszystkie dostępne akcje kontekstu:

![Wyświetlanie elementów kontekstu](media/refactoring-context-action.png)

Najechanie kursorem na dowolną z akcji kontekstu zapewnia podgląd tego, co zostanie dodane lub usunięte z kodu.

Alternatywnie, można nacisnąć **Option + Wprowadź** w dowolnym miejscu w kodzie:

![Opcja Wprowadź elementy kontekstu](media/refactoring-image2a.png)

Aby włączyć te opcje, należy wybrać *włącz analizę źródła otwartych plików* w opcjach Visual Studio > **Preferencje > Edytor tekstu > analiza źródła:**

![Włączanie analizy źródła](media/refactoring-options.png)

Istnieje ponad 100 możliwych akcji, które można zasugerować, które są włączone lub wyłączone, przeglądając **program Visual Studio > Preferencje > analiza źródła > akcje kodu > C#** i zaznaczając lub odznaczając pole obok akcji:

![Akcje analizy źródła w języku C#](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Wspólne działania kontekstowe

Niektóre z najczęściej używanych akcji kontekstowych są wyjaśnione poniżej.

#### <a name="extract-method"></a>Wyodrębnianie metody

Operacja refaktoryzacji metody wyodrębniania umożliwia utworzenie nowej metody przez wyodrębnienie wyboru kodu w istniejącym elementem członkowskim. Ta akcja będzie działać dwie rzeczy:

* Tworzy nową metodę zawierającą wybrany kod
* Wywołuje nową metodę w miejscu, w którym został wybrany kod.

##### <a name="example"></a>Przykład

1. Dodaj następujący kod:

```csharp
    class MainClass
    {

        double CalculatePyramidVolume(double baseArea, double height)
        {

            double volume = (baseArea * height) / 3;

            return volume;
        }
    }
```

2. Zaznacz linię `double volume = (baseArea * height) / 3;`, kliknij ją prawym przyciskiem myszy i wybierz opcję **Refaktoryzator > Metoda wyodrębniania**.

3. Użyj klawiszy strzałek, aby wybrać, gdzie nowa metoda powinna być umieszczona w kodzie.

#### <a name="encapsulate-field"></a>Hermetyzowanie pola

Operacja Encapsulate Field umożliwia utworzenie właściwości z istniejącego pola i aktualizuje kod, aby odwołać się do nowo utworzonej właściwości. Tworząc właściwość, która hermetyzuje pole, nie zezwalasz na bezpośredni dostęp do pola publicznego, co oznacza, że inne obiekty nie mogą go modyfikować.

Ta akcja spowoduje następujące czynności:

* Zmienia modyfikator dostępu na prywatny.
* Generuje obiekt ustawiający i ustawiający dla pola (chyba że pole jest tylko do odczytu, w którym to przypadku utworzy tylko obiekt ustawiający).

## <a name="source-analysis"></a>Analiza źródła

Analiza źródła analizuje kod na bieżąco, podkreślając potencjalne błędy i naruszenia stylu i zapewniając automatyczne poprawki jako akcje kontekstu.

Wszystkie wyniki analizy źródłowej dla dowolnego pliku można wyświetlić w dowolnym momencie, przeglądając pasek przewijania po prawej stronie edytora tekstu:

![Pasek boczny analizy źródła](media/refactoring-image4a.png)

Jeśli klikniesz na okrąg u góry, możesz iterować za pomocą każdej sugestii, z najwyższymi problemami z ważnością wyświetlanymi jako pierwsze. Najechanie kursorem na pojedynczy wynik lub linię powoduje wyświetlenie problemu, który można rozwiązać za pomocą akcji kontekstowych:

![Element analizy źródła](media/refactoring-image5.png)

## <a name="related-video"></a>Podobne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Zobacz też

- [Szybkie akcje (Visual Studio w systemie Windows)](/visualstudio/ide/quick-actions)
- [Kod refaktoryzatora (Visual Studio w systemie Windows)](/visualstudio/ide/refactoring-in-visual-studio)