---
title: Testowanie dużej aplikacji przy użyciu wielu map interfejsu użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
ms.assetid: 6e1ae9ec-e9b1-458a-bd96-0eb15e46f1d5
caps.latest.revision: 24
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2f6936811ea753d66d212facdda627930fb1ab10
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672128"
---
# <a name="testing-a-large-application-with-multiple-ui-maps"></a>Testowanie dużej aplikacji przy użyciu wielu map UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie omówiono sposób korzystania z kodowanych testów interfejsu użytkownika podczas testowania dużej aplikacji przy użyciu wielu map interfejsu użytkownika.

 **Wymagania**

- Visual Studio Enterprise

  Podczas tworzenia nowego kodowanego testu interfejsu użytkownika, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Struktura testowa generuje kod dla testu domyślnie w klasie [UIMap](/previous-versions/dd580454(v=vs.140)) . Aby uzyskać więcej informacji na temat rejestrowania kodowanych testów interfejsu użytkownika, zobacz [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) i [anatomię KODOWANEGO testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md).

  Wygenerowany kod dla mapowania interfejsu użytkownika zawiera klasę dla każdego obiektu, z którym test współdziała z. Dla każdej wygenerowanej metody Klasa pomocnika dla parametrów metody jest generowana w odniesieniu do tej metody. W przypadku dużej liczby obiektów, stron i formularzy i kontrolek w aplikacji Mapa interfejsu użytkownika może być bardzo duża. Ponadto, jeśli kilka osób pracuje nad testami, aplikacja zostanie nieporęczny za pomocą pojedynczego dużego pliku mapy interfejsu użytkownika.

  Korzystanie z wielu plików map interfejsu użytkownika może zapewnić następujące korzyści:

- Każda mapa może być skojarzona z logicznym podzbiorem aplikacji. Ułatwia to zarządzanie zmianami.

- Każdy tester może pracować nad sekcją aplikacji i ewidencjonować swój kod bez zakłócania pracy innych testerów pracujących nad innymi sekcjami aplikacji.

- Dodatki do interfejsu użytkownika aplikacji mogą być skalowane przyrostowo z minimalnym wpływem na testy dla innych części interfejsu użytkownika.

## <a name="do-you-need-multiple-ui-maps"></a>Potrzebujesz wielu map interfejsu użytkownika?
 Utwórz wiele map interfejsu użytkownika w każdym z następujących typów sytuacji:

- Kilka złożonych zbiorów złożonych formantów interfejsu użytkownika, które wspólnie wykonują operacje logiczne, takie jak Strona rejestracji w witrynie sieci Web lub strona zakupu koszyka zakupów.

- Niezależny zestaw kontrolek, do których uzyskuje się dostęp z różnych punktów aplikacji, takich jak Kreator z kilkoma stronami operacji. Jeśli każda Strona kreatora jest szczególnie złożona, można utworzyć oddzielne mapy interfejsu użytkownika dla każdej strony.

## <a name="adding-multiple-ui-maps"></a>Dodawanie wielu map interfejsu użytkownika

#### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Aby dodać mapę interfejsu użytkownika do projektu kodowanego testu interfejsu użytkownika

1. W **Eksplorator rozwiązań**, aby utworzyć folder w projekcie kodowanego testu interfejsu użytkownika do przechowywania wszystkich map interfejsu użytkownika, kliknij prawym przyciskiem myszy plik projektu kodowanego testu interfejsu użytkownika, wskaż polecenie **Dodaj** , a następnie wybierz pozycję **Nowy folder**. Można na przykład nazwać ją `UIMaps` .

    Nowy folder zostanie wyświetlony w ramach projektu kodowanego testu interfejsu użytkownika.

2. Kliknij prawym przyciskiem myszy `UIMaps` folder, wskaż polecenie **Dodaj**, a następnie wybierz **nowy element**.

    Zostanie wyświetlone okno dialogowe **Dodaj nowy element**.

   > [!NOTE]
   > Aby dodać nową mapę kodowanego testu interfejsu użytkownika, musisz być w projekcie kodowanego testu interfejsu użytkownika.

3. Wybierz z listy pozycję **Mapa kodowanego testu interfejsu użytkownika** .

    W polu **Nazwa** wprowadź nazwę nowej mapy interfejsu użytkownika. Użyj nazwy składnika lub strony, która będzie reprezentować mapa, na przykład `HomePageMap` .

4. Wybierz pozycję **Dodaj**.

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Zostanie zminimalizowane okno dialogowe **Konstruktor kodowanego testu interfejsu użytkownika** .

5. Zarejestruj akcje dla pierwszej metody i wybierz polecenie **Generuj kod**.

6. Po zarejestrowaniu wszystkich akcji i potwierdzeń pierwszego składnika lub strony i zgrupowaniu ich w metody, Zamknij okno dialogowe **Konstruktor kodowanego testu interfejsu użytkownika** .

7. Kontynuuj tworzenie map interfejsu użytkownika. Rejestrowanie akcji i potwierdzeń, grupowanie ich w metody dla każdego składnika, a następnie Generowanie kodu.

   W wielu przypadkach okno najwyższego poziomu aplikacji pozostaje stałe dla wszystkich kreatorów, formularzy i stron. Chociaż każda Mapa interfejsu użytkownika ma klasę dla okna najwyższego poziomu, wszystkie mapy są prawdopodobnie odwołujące się do tego samego okna najwyższego poziomu, w którym są uruchamiane wszystkie składniki aplikacji. Kodowane testy interfejsu użytkownika przeszukają kontrolki hierarchicznie od góry w dół, rozpoczynając od okna najwyższego poziomu, więc w przypadku złożonej aplikacji okno najwyższego poziomu może być zduplikowane w każdej mapie interfejsu użytkownika. Jeśli okno rzeczywiste najwyższego poziomu jest zduplikowane, wielokrotne modyfikacje zostaną wprowadzone w przypadku zmiany tego okna. Może to spowodować problemy z wydajnością podczas przełączania map interfejsu użytkownika.

   Aby zminimalizować ten efekt, można użyć metody, `CopyFrom()` Aby upewnić się, że nowe okno najwyższego poziomu w tej mapie interfejsu użytkownika jest takie samo, jak główne okno najwyższego poziomu.

## <a name="example"></a>Przykład
 Poniższy przykład jest częścią klasy narzędzi, która zapewnia dostęp do każdego składnika i ich formantów podrzędnych, które są reprezentowane przez klasy generowane w różnych mapach interfejsu użytkownika.

 W tym przykładzie aplikacja sieci Web o nazwie `Contoso` ma stronę główną, stronę produktu i stronę koszyka zakupów. Każda z tych stron udostępnia wspólne okno najwyższego poziomu, które jest oknem przeglądarki. Istnieje Mapa interfejsu użytkownika dla każdej strony, a Klasa narzędzi ma kod podobny do następującego:

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

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
