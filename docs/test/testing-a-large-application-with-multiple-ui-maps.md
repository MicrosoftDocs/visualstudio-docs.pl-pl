---
title: Testowanie dużej aplikacji przy użyciu wielu map interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fa5afd01ad25d4eebdc0b29e924cb2430d9c775
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590296"
---
# <a name="test-a-large-application-with-multiple-ui-maps"></a>Testowanie dużej aplikacji z wieloma mapami interfejsu użytkownika

W tym temacie omówiono sposób używania kodowanych testów interfejsu użytkownika podczas testowania dużej aplikacji przy użyciu wielu map interfejsu użytkownika.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

- Visual Studio Enterprise

Podczas tworzenia nowego testu interfejsu użytkownika kodowane, visual studio testowania framework generuje kod dla testu domyślnie w [UIMap](/previous-versions/dd580454(v=vs.140)) klasy. Aby uzyskać więcej informacji na temat rejestrowania zakodowanych testów interfejsu użytkownika, zobacz [Tworzenie zakodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md) i [anatomii zakodowanych testów interfejsu użytkownika.](../test/anatomy-of-a-coded-ui-test.md)

Wygenerowany kod mapy interfejsu użytkownika zawiera klasę dla każdego obiektu, z którym test wchodzi w interakcję. Dla każdej wygenerowanej metody klasa towarzysząca dla parametrów metody jest generowana specjalnie dla tej metody. Jeśli istnieje duża liczba obiektów, stron i formularzy i form i formantów w aplikacji, mapa interfejsu użytkownika może rosnąć bardzo duże. Ponadto, jeśli kilka osób pracuje nad testami, aplikacja staje się nieporęczna z jednym dużym plikiem mapy interfejsu użytkownika.

Korzystanie z wielu plików mapy interfejsu użytkownika może zapewnić następujące korzyści:

- Każda mapa może być skojarzona z logicznym podzbiorem aplikacji. Dzięki temu zmiany są łatwiejsze w zarządzaniu.

- Każdy tester może pracować nad sekcją aplikacji i sprawdzać swój kod bez zakłócania pracy z innymi testerami pracującymi nad innymi sekcjami aplikacji.

- Dodatki do interfejsu użytkownika aplikacji mogą być skalowane stopniowo z minimalnym wpływem na testy dla innych części interfejsu użytkownika.

## <a name="do-you-need-multiple-ui-maps"></a>Czy potrzebujesz wielu map interfejsu użytkownika?
Utwórz wiele map interfejsu użytkownika w każdej z tych sytuacji:

- Kilka złożonych zestawów formantów interfejsu użytkownika złożonych, które razem wykonują operację logiczną, taką jak strona rejestracji w witrynie sieci Web lub strona zakupu koszyka.

- Niezależny zestaw formantów, który jest dostępny z różnych punktów aplikacji, takich jak kreator z kilku stron operacji. Jeśli każda strona kreatora jest szczególnie złożona, można utworzyć oddzielne mapy interfejsu użytkownika dla każdej strony.

## <a name="add-multiple-ui-maps"></a>Dodawanie wielu map interfejsu użytkownika

### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Aby dodać mapę interfejsu użytkownika do zakodowany projekt testu interfejsu użytkownika

1. W **Eksploratorze rozwiązań**, aby utworzyć folder w kodowanym projekcie testowym interfejsu użytkownika do przechowywania wszystkich map interfejsu użytkownika, kliknij prawym przyciskiem myszy zakodowany plik projektu testu interfejsu użytkownika, wskaż polecenie **Dodaj**, a następnie wybierz pozycję **Nowy folder**. Na przykład można nazwać go `UIMaps`.

    Nowy folder jest wyświetlany w ramach zakodowanego projektu testu interfejsu użytkownika.

2. Kliknij prawym `UIMaps` przyciskiem myszy folder, wskaż polecenie **Dodaj**, a następnie wybierz polecenie **Nowy element**.

    Zostanie wyświetlone okno dialogowe **Dodaj nowy element**.

   > [!NOTE]
   > Musisz być w zakodowanym projekcie testu interfejsu użytkownika, aby dodać nową kodowane mapy testu interfejsu użytkownika.

3. Wybierz z listy **pozycję Zakodowana mapa testowa interfejsu** użytkownika.

    W polu **Nazwa** wprowadź nazwę nowej mapy interfejsu użytkownika. Użyj nazwy komponentu lub strony, którą mapa będzie `HomePageMap`reprezentować, na przykład .

4. Wybierz **pozycję Dodaj**.

    Okno programu Visual Studio minimalizuje i jest wyświetlane okno dialogowe **Konstruktor testów kodowanych** interfejsu użytkownika.

5. Zapisz akcje dla pierwszej metody i wybierz pozycję **Generuj kod**.

6. Po zarejestrowaniu wszystkich akcji i potwierdzeń dla pierwszego składnika lub strony i pogrupowania ich w metody zamknij okno dialogowe **Konstruktora testów kodowanych interfejsów** użytkownika.

7. Kontynuuj tworzenie map interfejsu użytkownika. Rejestrowanie akcji i potwierdzeń, grupowanie ich w metody dla każdego składnika, a następnie generowanie kodu.

   W wielu przypadkach okno najwyższego poziomu aplikacji pozostaje stałe dla wszystkich kreatorów, formularzy i stron. Mimo że każda mapa interfejsu użytkownika ma klasę dla okna najwyższego poziomu, wszystkie mapy prawdopodobnie odnoszą się do tego samego okna najwyższego poziomu, w którym wszystkie składniki aplikacji są uruchamiane. Coded UI tests search for controls hierarchically from the top down, starting from the top-level window, so in a complex application, the real top-level window could be duplicated in every UI Map. Jeśli rzeczywiste okno najwyższego poziomu jest duplikowany, wiele modyfikacji spowoduje, jeśli to okno się zmieni. Może to spowodować problemy z wydajnością podczas przełączania między mapami interfejsu użytkownika.

   Aby zminimalizować ten efekt, można `CopyFrom()` użyć metody, aby upewnić się, że nowe okno najwyższego poziomu w tej mapie interfejsu użytkownika jest taka sama jak główne okno najwyższego poziomu.

## <a name="example"></a>Przykład

Poniższy przykład jest częścią klasy narzędzia, która zapewnia dostęp do każdego składnika i ich formantów podrzędnych, które są reprezentowane przez klasy generowane w różnych map interfejsu użytkownika.

W tym przykładzie aplikacja `Contoso` sieci web o nazwie ma stronę główną, stronę produktu i stronę koszyka. Każda z tych stron ma wspólne okno najwyższego poziomu, które jest oknem przeglądarki. Istnieje mapa interfejsu użytkownika dla każdej strony, a klasa narzędzia ma kod podobny do następującego:

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

## <a name="see-also"></a>Zobacz też

- [Uimap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>
- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Anatomia zakodowany test interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
