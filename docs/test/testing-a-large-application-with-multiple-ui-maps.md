---
title: Testi dużej aplikacji przy użyciu wielu map UI
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1677ac36222b3d7efddc22bc1c0a69394eaf564
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931687"
---
# <a name="test-a-large-application-with-multiple-ui-maps"></a>Testowanie dużej aplikacji przy użyciu wielu map UI

W tym temacie omówiono sposób używania kodowanych testów interfejsu użytkownika podczas testowania dużych aplikacji przy użyciu wielu map interfejsu użytkownika.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

- Visual Studio Enterprise

Gdy tworzysz nowy kodowany test interfejsu użytkownika, struktura testowania programu Visual Studio generuje kod dla testu domyślnie <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasy. Aby uzyskać więcej informacji na temat sposobu rejestrowania kodowane testy interfejsu użytkownika, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md) i [anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md).

Kod generowany dla mapy interfejsu użytkownika zawiera klasę dla każdego obiektu, który test współdziała z. Dla każdej wygenerowanej metody do klasy pomocnika na potrzeby parametrów metody jest generowany specjalnie dla tej metody. W przypadku dużej liczby obiektów, stron i formularzy i kontrolek w aplikacji mapy interfejsu użytkownika można powiększać dużych. Ponadto jeśli kilka osób pracuje testy, aplikacja staje się niewygodna za pomocą pojedynczego dużego pliku mapy interfejsu użytkownika.

Użycie wielu plików mapy interfejsu użytkownika może zapewnić następujące korzyści:

- Każda mapa może być skojarzony z podzbiorem logiczny aplikacji. Dzięki temu zmiany do zarządzania.

- Każdego testera może pracować nad części aplikacji, a następnie sprawdź w ich kodzie bez zakłócania innych testerów, pracy w innych częściach aplikacji.

- Dodatki do interfejsu użytkownika aplikacji mogą być skalowane przyrostowo z minimalnym wpływem na testy dla innych części interfejsu użytkownika.

## <a name="do-you-need-multiple-ui-maps"></a>Czy potrzebujesz wielu map interfejsu użytkownika?
 Tworzenie wielu map interfejsu użytkownika w każdym z tego typu sytuacje:

-   Kilka złożonych zestawów złożonych kontrolek interfejsu użytkownika, które wspólnie wykonują operacji logicznej, takich jak strony rejestracji w witrynie sieci Web lub strony zakupu koszyk sklepowy.

-   Niezależny zestaw kontrolek, które jest dostępne z różnych punktach aplikacji, na przykład Kreator z kilku stron operacji. Jeśli każda strona kreatora jest szczególnie złożony, można utworzyć oddzielne map interfejsu użytkownika dla każdej strony.

## <a name="add-multiple-ui-maps"></a>Dodawanie wielu map UI

### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Aby dodać mapę interfejsu użytkownika do projektu kodowanego testu interfejsu użytkownika

1. W **Eksploratora rozwiązań**, aby utworzyć folder w projekcie kodowanego testu interfejsu użytkownika do przechowywania wszystkich map interfejsu użytkownika, kliknij prawym przyciskiem myszy plik projektu kodowanego testu interfejsu użytkownika, wskaż **Dodaj**, a następnie wybierz **nowy Folder**. Na przykład nazwać ją `UIMaps`.

    W obszarze projektu kodowanego testu interfejsu użytkownika zostanie wyświetlony nowy folder.

2. Kliknij prawym przyciskiem myszy `UIMaps` folderu, wskaż **Dodaj**, a następnie wybierz **nowy element**.

    **Dodaj nowy element** zostanie wyświetlone okno dialogowe.

   > [!NOTE]
   > Musisz być w projektu kodowanego testu interfejsu użytkownika można dodać nowej mapy kodowanego testu interfejsu użytkownika.

3. Wybierz **kodowanego interfejsu użytkownika testu mapy** z listy.

    W **nazwa** wprowadź nazwę dla nowej mapy interfejsu użytkownika. Użyj nazwy składnika lub strona, która mapy będzie reprezentować, na przykład `HomePageMap`.

4. Wybierz **Dodaj**.

    Minimalizuje okna programu Visual Studio i **kodowanego testu interfejsu użytkownika** zostanie wyświetlone okno dialogowe.

5. Rejestruj akcje w przypadku pierwszej metody, a następnie wybierz **Generuj kod**.

6. Zamknij po rejestrowane wszystkie akcje i potwierdzenia dla pierwszego składnika lub strony i pogrupowane metody **kodowanego testu interfejsu użytkownika** okno dialogowe.

7. Kontynuuj tworzenie map interfejsu użytkownika. Rejestruj akcje i potwierdzenia, zgrupować je w metody dla każdego składnika, a następnie generowania kodu.

   W wielu przypadkach najwyższego poziomu okna aplikacji pozostaje na stałym dla kreatorów, formularze i stron. Mimo że każdy mapy interfejsu użytkownika ma klasę okna najwyższego poziomu, na tym samym oknie najwyższego poziomu w ramach której wszystkie składniki aplikacji uruchom prawdopodobnie odnosi się wszystkie mapowania. Kodowanego interfejsu użytkownika testy wyszukiwania dla formantów hierarchicznie od góry do dołu, zaczynając od okna najwyższego poziomu, dzięki czemu w przypadku złożonych aplikacji okno rzeczywiste najwyższego poziomu można zduplikowane w każdej mapie interfejsu użytkownika. Okno rzeczywiste najwyższego poziomu jest zduplikowany, wprowadzanie wielu modyfikacji spowoduje zmiany tego okna. Może to spowodować problemy z wydajnością podczas przełączania między map interfejsu użytkownika.

   Aby zminimalizować ten efekt, można użyć `CopyFrom()` metody, aby upewnić się, że nowe okno najwyższego poziomu, w tym mapę interfejsu użytkownika jest taka sama jak główne okno najwyższego poziomu.

## <a name="example"></a>Przykład

Poniższy przykład jest częścią klasy narzędzia, która zapewnia dostęp do poszczególnych składników oraz ich formantów podrzędnych, które są reprezentowane przez klasy generowane w różnych map interfejsu użytkownika.

Na przykład aplikacja sieci web o nazwie `Contoso` ma stronę główną, stronę produktu i strony koszyka zakupów. Każda z tych stron udostępnia wspólne okno najwyższego poziomu, które jest okna przeglądarki. Istnieje mapę interfejsu użytkownika dla każdej strony i klasa narzędzie ma podobny do następującego kodu:

```csharp
using ContosoProject.UIMaps;
using ContosoProject.UIMaps.HomePageClasses;
using ContosoProject.UIMaps.ProductPageClasses;
using ContosoProject.UIMaps.ShoppingCartClasses;

namespace ContosoProject
{
    public class TestRunUtility
    {
        // Private fields for the properties
        private HomePage homePage = null;
        private ProductPage productPage = null;
        private ShoppingCart shoppingCart = null;

        public TestRunUtility()
        {
            homePage = new HomePage();
        }

        // Properties that get each UI Map
        public HomePage HomePage
        {
            get { return homePage; }
            set { homePage = value; }
        }

        // Gets the ProductPage from the ProductPageMap.
        public ProductPage ProductPageObject
        {
            get
            {
                if (productPage == null)
                {
                    // Instantiate a new page from the UI Map classes
                    productPage = new ProductPage();

                    // Since the Product Page and Home Page both use
                    // the same browser page as the top level window,
                    // get the top level window properties from the
                    // Home Page.
                    productPage.UIContosoFinalizeWindow.CopyFrom(
                        HomePage.UIContosoWindowsIWindow);
                }
                return productPage;
            }
        }

    // Continue to create properties for each page, getting the
    // page object from the corresponding UI Map and copying the
    // top level window properties from the Home Page.
}
```

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
