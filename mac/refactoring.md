---
title: Refaktoryzacja kodu
description: Ponowne porządkowanie kodu w programie Visual Studio dla komputerów Mac jest łatwiejsza przy użyciu analizy źródła.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: d7df01e2d2c6e4acb347b40cb82a04bee9394fe1
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335392"
---
# <a name="refactoring"></a>Refaktoryzacja

Refaktoryzacja kodu jest sposobem rozmieszczanie, restrukturyzacji i wyjaśnienia istniejącego kodu przy jednoczesnym zapewnieniu, która nie zmienia się ogólnym zachowaniom kodu.

Refaktoryzacja zapewnia lepszy wynik dotyczący bazy kodu, dzięki czemu bardziej użyteczny, czytelny i łatwego w utrzymaniu dla możesz żadnych innych deweloperów lub użytkownika, którego może odnosić się do kodu.

Program Visual Studio dla komputerów Mac integracji dzięki użyciu platformy Roslyn, platforma kompilatora .NET typu open source firmy Microsoft, pozwala na więcej operacji refaktoryzacji.

## <a name="renaming"></a>Zmiana nazwy

*Zmień nazwę* refaktoryzacji polecenie może służyć w dowolnym identyfikator kodu (na przykład nazwa klasy, nazwa właściwości itd.) aby znaleźć wszystkie wystąpienia identyfikatora, a następnie zmianę ich. Aby zmienić nazwę symbolu, kliknij prawym przyciskiem myszy na nim, a następnie wybierz **Refaktoryzuj > Zmień nazwę**, lub **Cmd + R** powiązanie klucza:

![Zmień nazwę elementu menu.](media/refactoring-renaming1.png)

Spowoduje to wyróżnienie symbolu i wszelkie odwołania do niego. Po uruchomieniu, wpisując nazwę nowej automatycznie zmienia wszystkie odwołania w kodzie, a Twoje ukończenia zmiany nazwy można sygnał, naciskając klawisz **Enter**:

![Zmiana nazwy i identyfikatora](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Kontekst akcji

Kontekst akcji pozwalają na sprawdzanie kodu C# i wyświetlić wszystkie możliwe opcje refaktoryzacji.

**Rozwiązać** i **Refaktoryzuj** kontekstu elementy są łączone w pojedynczy *szybka poprawka...*  element, który udostępnia wszystkie dostępne akcje kontekstowe:

![Wyświetl elementy kontekstu](media/refactoring-context-action.png)

Wszystkie akcje kontekstowe kursor umożliwia podgląd co zostaną dodane lub usunięte z Twojego kodu.

Alternatywnie, możesz nacisnąć przycisk **Option + Enter** dowolnym miejscu w kodzie:

![Opcja kontekstu wprowadź elementów](media/refactoring-image2a.png)

Aby włączyć te opcje, należy wybrać *Włącz analizę źródła otwartych plików* w opcjach **programu Visual Studio dla komputerów Mac > Preferencje > Edytor tekstu > analizę źródła**:

![Włączanie analizy źródła](media/refactoring-options.png)

Istnieje ponad 100 możliwych działań, które mogą być sugerowane, które są włączone lub wyłączone, przechodząc do **programu Visual Studio dla komputerów Mac > Preferencje > analizę źródła > C# > Akcje kodu** i zaznaczenie lub unselecting pole obok pozycji Akcja:

![Akcje analizy źródło języka C#](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Typowe akcje kontekstu

Poniżej opisano niektóre akcje przede wszystkim powszechnie używane kontekstu.

#### <a name="extract-method"></a>Wyodrębnianie metody

Operacji refaktoryzacji wyodrębniania metody umożliwia utworzenie nowej metody, wyodrębniając wybór kodu w istniejącą składową. Ta akcja spowoduje wykonać dwie czynności:

* Tworzy nową metodę zawierającą zaznaczony kod
* Wywołuje nową metodę w miejscu, gdzie został zaznaczony kod.

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

2. Zaznacz wiersz `double volume = (baseArea * height) / 3;`, kliknij prawym przyciskiem myszy kliknij go, a wybierz **Refaktoryzuj > Wyodrębnij metodę**.

3. Użyj klawiszy strzałek, aby wybrać, gdzie nowa metoda ma zostać umieszczony w kodzie.

#### <a name="encapsulate-field"></a>Hermetyzowanie pola

Operacja Hermetyzuj pole umożliwia tworzenie właściwości z istniejącego pola i aktualizuje swój kod, aby odwoływać się do nowo utworzonej właściwości. Tworząc właściwość, która hermetyzuje pola, możesz są nie można przydzielać bezpośredni dostęp do pola publiczne, co oznacza, czy inne obiekty nie można go modyfikować.

Ta akcja wykona następujące czynności:

* Zmienia modyfikator dostępu prywatnego.
* Generuje metodę getter i setter dla pola (chyba że pole jest tylko do odczytu, w którym to przypadku tylko utworzy on metody pobierającej).

## <a name="source-analysis"></a>Analiza źródła

Analiza źródła analizuje kod na bieżąco, podkreślenie potencjalnych błędów i naruszeń stylu i zapewniając automatyczne poprawki jako kontekst akcji.

Aby wyświetlić wszystkie wyniki analizy źródła dla każdego pliku w dowolnym momencie, wyświetlanie paska przewijania po prawej stronie edytora tekstu:

![Pasek boczny analizy źródła](media/refactoring-image4a.png)

Kliknięcie okręgu u góry można wykonać iterację każdego sugestię o najpoważniejszych problemów wyświetlone pierwsze. Kursor w wierszu lub wynik wyświetla problem można naprawić za pomocą kontekstu akcji:

![Element analizy źródła](media/refactoring-image5.png)

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje (Visual Studio Windows)](/visualstudio/ide/quick-actions)
- [Refaktoryzacja kodu (Visual Studio Windows)](/visualstudio/ide/refactoring-in-visual-studio)