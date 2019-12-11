---
title: Refaktoryzacja kodu
description: Ponowna organizacja kodu w Visual Studio dla komputerów Mac jest prosta przy użyciu analizy źródłowej.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 7b11f09d8fb70612d4496987f69583b2ac691275
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985235"
---
# <a name="refactoring"></a>Refaktoryzacja

Refaktoryzacja kodu jest sposobem na ponowne rozmieszczenie, restrukturyzację i wyjaśnienie istniejącego kodu przy zapewnieniu, że ogólne zachowanie kodu nie ulegnie zmianie.

Refaktoryzacja generuje bazę kodu dotyczący, dzięki czemu jest bardziej użyteczny, czytelny i konserwowany dla Ciebie lub dowolnego innego dewelopera lub użytkownika, który może odwoływać się do kodu.

Integracja Visual Studio dla komputerów Mac z usługą Roslyn — platforma kompilatora .NET Open Source firmy Microsoft umożliwia wykonywanie dodatkowych operacji refaktoryzacji.

## <a name="renaming"></a>Zmiana nazwy

Polecenia *zmiany nazwy* można użyć dla dowolnego identyfikatora kodu (na przykład nazwy klasy, nazwy właściwości itp.), aby znaleźć wszystkie wystąpienia tego identyfikatora i je zmienić. Aby zmienić nazwę symbolu, kliknij go prawym przyciskiem myszy, a następnie wybierz pozycję **refaktoryzacja > Zmień nazwę**lub powiązanie klawiszy **cmd + R** :

![Zmień nazwę elementu menu](media/refactoring-renaming1.png)

Podświetla symbol i wszystkie odwołania do niego. Po rozpoczęciu wpisywania nowej nazwy automatycznie zmienia wszystkie odwołania w kodzie i można sygnalizować zakończenie zmiany nazwy, naciskając klawisz **Enter**:

![Zmiana nazwy i identyfikator](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Akcje kontekstu

Akcje kontekstowe umożliwiają badanie dowolnego C# kodu i wyświetlanie wszystkich możliwych opcji refaktoryzacji.

Elementy kontekstu **rozwiązywania** i **refaktoryzacji** są łączone w jedną *szybką poprawkę...* element, który zapewni wszystkie dostępne akcje kontekstu:

![Wyświetl elementy kontekstu](media/refactoring-context-action.png)

Umieszczenie kursora na dowolnym z akcji kontekstowych zapewnia podgląd elementów, które zostaną dodane lub usunięte z kodu.

Alternatywnie możesz nacisnąć klawisz **Option + Enter** w dowolnym miejscu w kodzie:

![Opcja wprowadzania elementów kontekstu](media/refactoring-image2a.png)

Aby włączyć te opcje, należy wybrać opcję *Włącz analizę źródła otwartych plików* w opcjach, **Visual Studio dla komputerów Mac > preferencji > Edytor tekstu > Analiza źródła**:

![Włączanie analizy źródła](media/refactoring-options.png)

Istnieje ponad 100 możliwych akcji, które można zasugerować, które są włączone lub wyłączone przez przechodzenie do **Visual Studio dla komputerów Mac preferencji > > analizy C# źródłowej > > akcji kodu** i zaznaczając lub usuwając zaznaczenie pola obok akcji:

![C#Akcje analizy źródła](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Typowe akcje kontekstu

Poniżej opisano niektóre z najczęściej używanych akcji kontekstowych.

#### <a name="extract-method"></a>Wyodrębnianie metody

Operacja refaktoryzacji metody Extract umożliwia utworzenie nowej metody przez wyodrębnienie zaznaczenia kodu w istniejącym elemencie członkowskim. Ta akcja spowoduje wykonanie dwóch czynności:

* Tworzy nową metodę zawierającą wybrany kod
* Wywołuje nową metodę w miejscu, w którym zaznaczono kod.

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

2. Zaznacz wiersz `double volume = (baseArea * height) / 3;`, kliknij go prawym przyciskiem myszy, a następnie wybierz pozycję **refaktoryzacja > Metoda wyodrębnienia**.

3. Użyj klawiszy strzałek, aby wybrać miejsce, w którym Nowa metoda powinna zostać umieszczona w kodzie.

#### <a name="encapsulate-field"></a>Hermetyzowanie pola

Operacja hermetyzowania pola umożliwia utworzenie właściwości z istniejącego pola i zaktualizowanie kodu w celu odwoływania się do nowo utworzonej właściwości. Utworzenie właściwości, która hermetyzuje pole, nie zezwala na bezpośredni dostęp do pola publicznego, co oznacza, że inne obiekty nie mogą go modyfikować.

Ta akcja spowoduje wykonanie następujących czynności:

* Zmienia modyfikator dostępu na prywatny.
* Generuje metodę pobierającą i ustawiającą dla pola (chyba że pole jest tylko do odczytu, w takim przypadku tylko zostanie utworzona metoda pobierająca).

## <a name="source-analysis"></a>Analiza źródła

Analiza źródła analizuje kod na bieżąco przez podkreślanie potencjalnych błędów i naruszeń stylu oraz dostarczanie autopoprawek jako akcji kontekstowych.

W dowolnym momencie możesz wyświetlić wszystkie wyniki analizy źródłowej dowolnego pliku, wyświetlając pasek przewijania po prawej stronie edytora tekstu:

![Pasek boczny analizy źródła](media/refactoring-image4a.png)

Po kliknięciu kółka u góry można wykonać iterację poszczególnych sugestii z najwyższymi problemami dotyczącymi ważności, które są wyświetlane jako pierwsze. Umieszczenie wskaźnika myszy na pojedynczym wyniku lub w wierszu powoduje wyświetlenie problemu, który można naprawić za pomocą akcji kontekstu:

![Element analizy źródła](media/refactoring-image5.png)

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje (Visual Studio w systemie Windows)](/visualstudio/ide/quick-actions)
- [Kod refaktoryzacji (Visual Studio w systemie Windows)](/visualstudio/ide/refactoring-in-visual-studio)