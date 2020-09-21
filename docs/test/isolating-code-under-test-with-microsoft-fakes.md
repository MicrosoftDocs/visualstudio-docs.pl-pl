---
title: Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes
ms.date: 06/03/2020
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- VB
- CSharp
ms.openlocfilehash: 9ef41b8645e77a28c8422fff49111b41215ba971
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90739879"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes

Sztuczne firmy Microsoft ułatwiają Izolowanie testowanego kodu przez zastąpienie innych części aplikacji za pomocą *wycinków* lub *podkładek*. Są to małe fragmenty kodu, będące pod kontrolą Twoich testów. Izolując kod do testowania, wiesz, że jeśli test wypadnie niepomyślnie, przyczyna leży tam, a nie w żadnym innym miejscu. Podkładki i wycinki pozwalają na testowanie kodu, nawet jeśli pozostałe części aplikacji jeszcze nie działają.

Podróbki występują w dwóch wersjach:

- [Procedura zastępcza](#get-started-with-stubs) zastępuje klasę niewielkim substytutem, który implementuje ten sam interfejs.  Aby użyć wycinków, należy tak zaprojektować aplikację, aby każdy składnik zależał jedynie od interfejsów, a nie od innych składników. (Przez „składnik” rozumie się klasy lub grupy klas, które są zaprojektowane i aktualizowane łącznie i zwykle są zawarte w zestawie).

- [Podkładka](#get-started-with-shims) modyfikuje skompilowany kod aplikacji w czasie wykonywania, tak że zamiast wykonywania określonego wywołania metody jest uruchamiany kod podkładki, który zapewnia test. Podkładki mogą służyć do zastępowania wywołań do zestawów, których nie można modyfikować, takich jak zestawy .NET.

![Elementy sztuczne zastępują inne składniki](../test/media/fakes-2.png)

**Wymagania**

- Visual Studio Enterprise
- Projekt .NET Framework
- Obsługa projektu w stylu .NET Core i zestawu SDK jest obecnie w wersji zapoznawczej. [Przeczytaj więcej](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects)

> [!NOTE]
> - Projekty .NET Standard nie są obsługiwane.
> - Profilowanie za pomocą programu Visual Studio nie jest dostępne dla testów korzystających z elementów sztucznych firmy Microsoft.

## <a name="choose-between-stub-and-shim-types"></a>Wybór między elementami zastępczymi i typami podkładki
Projekt Visual Studio zazwyczaj zostanie zakwalifikowany jako składnik, ponieważ klasy te są opracowywane i aktualizowane równocześnie. Można rozważyć użycie wycinków i podkładek do wywołań, które dany projekt kieruje w stronę innych projektów w rozwiązaniu, lub w stronę innych zestawów, do których projekt się odnosi.

Jako ogólnej wskazówki należy użyć fragmentów dla wywołań w ramach rozwiązania Visual Studio i podkładek dla wywołań do innych zestawów, do których istnieje odwołanie. Dzieje się tak, ponieważ wewnątrz własnego rozwiązania warto ćwiczyć rozdzielanie par składników przez definiowanie interfejsów w sposób wymagany przez wycinkowanie. Ale zestawy zewnętrzne, takie jak *System.dll* zwykle nie są dostarczane z oddzielnymi definicjami interfejsów, dlatego należy zamiast tego użyć podkładek.

Inne zagadnienia to:

**Skuteczności.** Podkładki działają wolniej, ponieważ przepisują kod w czasie wykonywania. Wycinki kodu nie mają dodatkowego obciążenia i są równie szybkie, jak metody wirtualne.

**Metody statyczne, typy zapieczętowane.** Możesz używać wycinków tylko do implementacji interfejsów. Tym samym typy wycinka nie mogą być stosowane dla metod statycznych, metod niewirtualnych, zaplombowanych metod wirtualnych, metod w zaplombowanych typach itd.

**Typy wewnętrzne.** Zarówno elementy zastępcze, jak i podkładki mogą być używane z wewnętrznymi typami, które są dostępne za pomocą atrybutu Assembly <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> .

**Metody prywatne.** Podkładki zastępują wywołania metod prywatnych, jeśli widoczne są wszystkie typy podpisów metody. Wycinki kodu mogą zastąpić jedynie metody widoczne.

**Interfejsy i metody abstrakcyjne.** Wycinki kodu zapewniają implementacje interfejsów i metody abstrakcyjne, które mogą służyć do testowania. Podkładki nie mogą instrumentować interfejsów i metod abstrakcyjnych, ponieważ nie zawierają treści metody.

Zasadniczo zaleca się używanie typów wycinków w celu odseparowania od zależności w ramach własnej bazy kodów. Można to zrobić, ukrywając składniki za interfejsami. Typy podkładek można wykorzystywać do izolowania od składników innych firm, które nie mają sprawdzalnego API.

## <a name="get-started-with-stubs"></a>Wprowadzenie do wycinków
Aby uzyskać bardziej szczegółowy opis, zobacz [Używanie wycinków do izolowania części aplikacji od siebie do testowania jednostkowego](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

1. **Wsuń interfejsy**

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

2. **Dodaj zestaw elementów sztucznych**

    1. W **Eksplorator rozwiązań**rozwiń listę odwołania projektu testowego. Jeśli pracujesz w Visual Basic, musisz wybrać opcję **Pokaż wszystkie pliki** , aby zobaczyć listę odwołań.

    2. Wybierz odwołanie do zestawu, w którym zdefiniowano interfejs (na przykład IStockFeed). W menu skrótów tego odwołania wybierz pozycję **Dodaj zestaw**elementów sztucznych.

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

    Specjalna część Magic jest klasą `StubIStockFeed` . Dla każdego interfejsu w zestawie, do którego istnieje odwołanie, mechanizm Microsoft Fakes generuje klasę zastępczą. Nazwa klasy zastępczej pochodzi od nazwy interfejsu, z " `Fakes.Stub` " jako prefiksem i dołączonymi nazwami typu parametru.

    Wycinki kodu są generowane także dla metod pobierających i ustawiających właściwości, dla zdarzeń i metod ogólnych. Aby uzyskać więcej informacji, zobacz [Używanie wycinków do izolowania części aplikacji od siebie do testowania jednostkowego](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

## <a name="get-started-with-shims"></a>Wprowadzenie do podkładki
(Aby uzyskać bardziej szczegółowy opis, zobacz [Używanie podkładki do izolowania aplikacji od innych zestawów do testowania jednostek](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)).

Załóżmy, że składnik zawiera wywołania `DateTime.Now` :

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }
```

Podczas testowania chcesz zmienić podkładkę na `Now` Właściwość, ponieważ rzeczywista wersja niewygodnie zwraca inną wartość przy każdym wywołaniu.

Aby używać podkładek, nie trzeba modyfikować kodu aplikacji ani pisać go w określony sposób.

1. **Dodaj zestaw elementów sztucznych**

     W **Eksplorator rozwiązań**Otwórz odwołania do projektu testu jednostkowego i wybierz odwołanie do zestawu, który zawiera metodę, która ma zostać sfałszowana. W tym przykładzie `DateTime` Klasa jest w *System.dll*.  Aby wyświetlić odwołania w projekcie Visual Basic, wybierz **Pokaż wszystkie pliki**.

     Wybierz pozycję **Dodaj zestaw**elementów sztucznych.

2. **Wstaw podkładkę w ShimsContext**

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

    Nazwy klas podkładków składają się z prefiksu `Fakes.Shim` do oryginalnej nazwy typu. Nazwy parametrów są dołączane do nazwy metody. (Nie trzeba dodawać żadnego odwołania do zestawu do System. resztuczne).

W poprzednim przykładzie podkładka jest wykorzystana do metody statycznej. Aby użyć podkładki dla metody wystąpienia, napisz `AllInstances` między nazwą typu a nazwą metody:

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

(Nie istnieje zestaw "System. IO. resztuczne" do odwołania. Przestrzeń nazw jest generowana przez proces tworzenia podkładki. Ale w zwykły sposób można użyć opcji "Using" lub "Import").

Można również utworzyć podkładki dla konkretnych wystąpień, konstruktorów i właściwości. Aby uzyskać więcej informacji, zobacz [Używanie podkładki do izolowania aplikacji od innych zestawów do testowania jednostkowego](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="in-this-section"></a>W tej sekcji
[Stosowanie wycinków kodu do izolowania od siebie poszczególnych części aplikacji w celu przeprowadzania testów jednostkowych](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

[Stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

[Konwencje dotyczące generowania kodu, jego kompilowania i nazywania w Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
