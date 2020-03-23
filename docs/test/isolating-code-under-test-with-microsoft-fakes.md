---
title: Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- VB
- CSharp
ms.openlocfilehash: 662a61bf97e1726892b877dc79a0ef98340a34ec
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566907"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes

Microsoft Fakes pomaga wyizolować testowany kod, zastępując inne części aplikacji *wycinkami* lub *podkładkami.* Są to małe fragmenty kodu, będące pod kontrolą Twoich testów. Izolując kod do testowania, wiesz, że jeśli test wypadnie niepomyślnie, przyczyna leży tam, a nie w żadnym innym miejscu. Podkładki i wycinki pozwalają na testowanie kodu, nawet jeśli pozostałe części aplikacji jeszcze nie działają.

Podróbki występują w dwóch wersjach:

- [Skrót zastępuje](#get-started-with-stubs) klasę z małym substytutem, który implementuje ten sam interfejs.  Aby użyć wycinków, należy tak zaprojektować aplikację, aby każdy składnik zależał jedynie od interfejsów, a nie od innych składników. (Przez „składnik” rozumie się klasy lub grupy klas, które są zaprojektowane i aktualizowane łącznie i zwykle są zawarte w zestawie).

- [Podkładka](#get-started-with-shims) modyfikuje skompilowany kod aplikacji w czasie wykonywania, tak aby zamiast wywoływania określonej metody, uruchamia kod podkładki, który zapewnia test. Podkładki mogą służyć do zastępowania wywołań do zestawów, których nie można modyfikować, takich jak zestawy .NET.

![Podróbki zastępują inne komponenty](../test/media/fakes-2.png)

**Wymagania**

- Visual Studio Enterprise
- Projekt .NET Framework

> [!NOTE]
> - Projekty .NET Standard nie są obsługiwane.
> - Profilowanie za pomocą programu Visual Studio nie jest dostępne dla testów, które używają Microsoft Fakes.

## <a name="choose-between-stub-and-shim-types"></a>Wybierz między typami skrótów i podkładek
Projekt Visual Studio zazwyczaj zostanie zakwalifikowany jako składnik, ponieważ klasy te są opracowywane i aktualizowane równocześnie. Można rozważyć użycie wycinków i podkładek do wywołań, które dany projekt kieruje w stronę innych projektów w rozwiązaniu, lub w stronę innych zestawów, do których projekt się odnosi.

Jako ogólnej wskazówki należy użyć fragmentów dla wywołań w ramach rozwiązania Visual Studio i podkładek dla wywołań do innych zestawów, do których istnieje odwołanie. Dzieje się tak, ponieważ wewnątrz własnego rozwiązania warto ćwiczyć rozdzielanie par składników przez definiowanie interfejsów w sposób wymagany przez wycinkowanie. Ale zestawy zewnętrzne, takie jak *System.dll* zazwyczaj nie są dostarczane z oddzielnymi definicjami interfejsu, więc zamiast tego należy użyć podkładek.

Inne zagadnienia to:

**Wydajności.** Podkładki działają wolniej, ponieważ przepisują kod w czasie wykonywania. Wycinki kodu nie mają dodatkowego obciążenia i są równie szybkie, jak metody wirtualne.

**Metody statyczne, typy zapieczętowane.** Możesz używać wycinków tylko do implementacji interfejsów. Tym samym typy wycinka nie mogą być stosowane dla metod statycznych, metod niewirtualnych, zaplombowanych metod wirtualnych, metod w zaplombowanych typach itd.

**Typy wewnętrzne.** Zarówno wycinki, jak i podkładki mogą być używane z <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>typami wewnętrznymi, które są dostępne za pomocą atrybutu zestawu .

**Metody prywatne.** Podkładki zastępują wywołania metod prywatnych, jeśli widoczne są wszystkie typy podpisów metody. Wycinki kodu mogą zastąpić jedynie metody widoczne.

**Interfejsy i metody abstrakcyjne.** Wycinki kodu zapewniają implementacje interfejsów i metody abstrakcyjne, które mogą służyć do testowania. Podkładki nie mogą przyrządy interfejsów i metod abstrakcyjnych, ponieważ nie mają organów metody.

Zasadniczo zaleca się używanie typów wycinków w celu odseparowania od zależności w ramach własnej bazy kodów. Można to zrobić, ukrywając składniki za interfejsami. Typy podkładek można wykorzystywać do izolowania od składników innych firm, które nie mają sprawdzalnego API.

## <a name="get-started-with-stubs"></a>Zacznij ować z wycinkami
Aby uzyskać bardziej szczegółowy opis, zobacz [Używanie wycinków do izolowania części aplikacji od siebie w celu testowania jednostkowego.](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

1. **Interfejsy wtryskowe**

     Aby użyć wycinków, musisz napisać kod, który chcesz przetestować w taki sposób, aby nie wymieniał wprost klas w innych składnikach Twojej aplikacji. Przez „składnik” rozumie się klasę lub grupę klas, które są opracowane i aktualizowane łącznie i zwykle są zawarte w jednym projekcie Visual Studio. Zmienne i parametry powinny być zdeklarowane przy użyciu interfejsów, a wystąpienia innych składników powinny zostać przekazane lub utworzone za pomocą fabryki. Jeśli na przykład StockFeed jest klasą w innym składniku aplikacji, zostałoby to uznane za nieprawidłowe:

     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`

     Zamiast tego zdefiniuj interfejs, który może być implementowany przez inny składnik, a także przez wycinek dla celów testowych:

    ```csharp
    public int GetContosoPrice(IStockFeed feed) => feed.GetSharePrice("COOO");
    ```

    ```vb
    Public Function GetContosoPrice(feed As IStockFeed) As Integer
     Return feed.GetSharePrice("COOO")
    End Function

    ```

2. **Dodaj zestaw podróbek**

    1. W **Eksploratorze rozwiązań**rozwiń listę referencyjną projektu testowego. Jeśli pracujesz w języku Visual Basic, musisz wybrać opcję **Pokaż wszystkie pliki,** aby wyświetlić listę odwołań.

    2. Wybierz odwołanie do zestawu, w którym zdefiniowano interfejs (na przykład IStockFeed). W menu skrótów tego odwołania wybierz polecenie **Dodaj zestaw podróbek**.

    3. Ponownie skompiluj rozwiązanie.

3. W testach należy skonstruować wystąpienia wycinka i podać kod dla jego metody:

    ```csharp
    [TestClass]
    class TestStockAnalyzer
    {
        [TestMethod]
        public void TestContosoStockPrice()
        {
          // Arrange:

            // Create the fake stockFeed:
            IStockFeed stockFeed =
                 new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.
                     {
                         // Define each method:
                         // Name is original name + parameter types:
                         GetSharePriceString = (company) => { return 1234; }
                     };

            // In the completed application, stockFeed would be a real one:
            var componentUnderTest = new StockAnalyzer(stockFeed);

          // Act:
            int actualValue = componentUnderTest.GetContosoPrice();

          // Assert:
            Assert.AreEqual(1234, actualValue);
        }
        ...
    }
    ```

    ```vb
    <TestClass()> _
    Class TestStockAnalyzer

        <TestMethod()> _
        Public Sub TestContosoStockPrice()
            ' Arrange:
            ' Create the fake stockFeed:
            Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed
            With stockFeed
                .GetSharePriceString = Function(company)
                                           Return 1234
                                       End Function
            End With
            ' In the completed application, stockFeed would be a real one:
            Dim componentUnderTest As New StockAnalyzer(stockFeed)
            ' Act:
            Dim actualValue As Integer = componentUnderTest.GetContosoPrice
            ' Assert:
            Assert.AreEqual(1234, actualValue)
        End Sub
    End Class

    ```

    Szczególnym kawałkiem magii jest `StubIStockFeed`tutaj klasa. Dla każdego interfejsu w zestawie, do którego istnieje odwołanie, mechanizm Microsoft Fakes generuje klasę zastępczą. Nazwa klasy skrótowej jest pochodną od nazwy interfejsu,`Fakes.Stub`z " jako prefiksem i nazwami typów parametrów.

    Wycinki kodu są generowane także dla metod pobierających i ustawiających właściwości, dla zdarzeń i metod ogólnych. Aby uzyskać więcej informacji, zobacz [Używanie wycinków do izolowania części aplikacji od siebie w celu testowania jednostkowego.](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

## <a name="get-started-with-shims"></a>Zacznij ować z podkładkami
(Aby uzyskać bardziej szczegółowy opis, zobacz [Używanie podkładek do izolowania aplikacji od innych zestawów do testowania jednostkowego).](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

Załóżmy, że `DateTime.Now`składnik zawiera wywołania:

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }
```

Podczas testowania, chcesz `Now` podkładkać właściwość, ponieważ rzeczywista wersja niewygodnie zwraca inną wartość przy każdym wywołaniu.

Aby użyć podkładek, nie trzeba modyfikować kodu aplikacji ani pisać go w określony sposób.

1. **Dodaj zestaw podróbek**

     W **Eksploratorze rozwiązań**otwórz odwołania do projektu testu jednostkowego i wybierz odwołanie do zestawu zawierającego metodę, którą chcesz sfałszować. W tym przykładzie klasa znajduje się `DateTime` w pliku *System.dll*.  Aby wyświetlić odwołania w projekcie języka Visual Basic, wybierz pozycję **Pokaż wszystkie pliki**.

     Wybierz **pozycję Dodaj zestaw podróbek**.

2. **Wstawianie podkładki w podkładce ShimsContext**

    ```csharp
    [TestClass]
    public class TestClass1
    {
            [TestMethod]
            public void TestCurrentYear()
            {
                int fixedYear = 2000;

                // Shims can be used only in a ShimsContext:
                using (ShimsContext.Create())
                {
                  // Arrange:
                    // Shim DateTime.Now to return a fixed date:
                    System.Fakes.ShimDateTime.NowGet =
                    () =>
                    { return new DateTime(fixedYear, 1, 1); };

                    // Instantiate the component under test:
                    var componentUnderTest = new MyComponent();

                  // Act:
                    int year = componentUnderTest.GetTheCurrentYear();

                  // Assert:
                    // This will always be true if the component is working:
                    Assert.AreEqual(fixedYear, year);
                }
            }
    }
    ```

    ```vb
    <TestClass()> _
    Public Class TestClass1
        <TestMethod()> _
        Public Sub TestCurrentYear()
            Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()
                Dim fixedYear As Integer = 2000
                ' Arrange:
                ' Detour DateTime.Now to return a fixed date:
                System.Fakes.ShimDateTime.NowGet = _
                    Function() As DateTime
                        Return New DateTime(fixedYear, 1, 1)
                    End Function

                ' Instantiate the component under test:
                Dim componentUnderTest = New MyComponent()
                ' Act:
                Dim year As Integer = componentUnderTest.GetTheCurrentYear
                ' Assert:
                ' This will always be true if the component is working:
                Assert.AreEqual(fixedYear, year)
            End Using
        End Sub
    End Class
    ```

    Nazwy klas podkładek shim są `Fakes.Shim` składane przez prefiks do oryginalnej nazwy typu. Nazwy parametrów są dołączane do nazwy metody. (Nie trzeba dodawać żadnych odwołań do zestawu do System.Fakes.)

W poprzednim przykładzie podkładka jest wykorzystana do metody statycznej. Aby użyć podkładki dla metody `AllInstances` wystąpienia, należy napisać między nazwą typu a nazwą metody:

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

(Nie ma zestawu "System.IO.Fakes", do którego można się odwołać. Obszar nazw jest generowany przez proces tworzenia podkładki. Ale można użyć "przy użyciu" lub "Import" w zwykły sposób.)

Można również utworzyć podkładki dla konkretnych wystąpień, konstruktorów i właściwości. Aby uzyskać więcej informacji, zobacz [Używanie podkładek do izolowania aplikacji od innych zestawów do testowania jednostek.](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

## <a name="in-this-section"></a>W tej sekcji
[Stosowanie wycinków kodu do izolowania od siebie poszczególnych części aplikacji w celu przeprowadzania testów jednostkowych](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

[Stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

[Konwencje dotyczące generowania kodu, jego kompilowania i nazywania w Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
