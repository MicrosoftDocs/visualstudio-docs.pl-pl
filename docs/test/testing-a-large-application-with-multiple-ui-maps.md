---
title: Testowanie dużej aplikacji przy użyciu wielu map interfejsu użytkownika
description: Dowiedz się, jak używać kodowanych testów interfejsu użytkownika podczas testowania dużej aplikacji przy użyciu wielu map interfejsu użytkownika. Ta funkcja wymaga Visual Studio Enterprise.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93ae6aaa77a133a0d1805554a38b2714bff5b312
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330163"
---
# <a name="test-a-large-application-with-multiple-ui-maps"></a>Testowanie dużej aplikacji przy użyciu wielu map interfejsu użytkownika

W tym temacie omówiono sposób korzystania z kodowanych testów interfejsu użytkownika podczas testowania dużej aplikacji przy użyciu wielu map interfejsu użytkownika.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

- Visual Studio Enterprise

Podczas tworzenia nowego kodowanego testu interfejsu użytkownika, struktura testowa programu Visual Studio generuje kod dla testu domyślnie w klasie [UIMap](/previous-versions/dd580454(v=vs.140)) . Aby uzyskać więcej informacji na temat rejestrowania kodowanych testów interfejsu użytkownika, zobacz [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md) i [anatomię KODOWANEGO testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md).

Wygenerowany kod dla mapowania interfejsu użytkownika zawiera klasę dla każdego obiektu, z którym test współdziała z. Dla każdej wygenerowanej metody Klasa pomocnika dla parametrów metody jest generowana w odniesieniu do tej metody. W przypadku dużej liczby obiektów, stron i formularzy i kontrolek w aplikacji Mapa interfejsu użytkownika może być bardzo duża. Ponadto, jeśli kilka osób pracuje nad testami, aplikacja zostanie nieporęczny za pomocą pojedynczego dużego pliku mapy interfejsu użytkownika.

Korzystanie z wielu plików map interfejsu użytkownika może zapewnić następujące korzyści:

- Każda mapa może być skojarzona z logicznym podzbiorem aplikacji. Ułatwia to zarządzanie zmianami.

- Każdy tester może pracować nad sekcją aplikacji i ewidencjonować swój kod bez zakłócania pracy innych testerów pracujących nad innymi sekcjami aplikacji.

- Dodatki do interfejsu użytkownika aplikacji mogą być skalowane przyrostowo z minimalnym wpływem na testy dla innych części interfejsu użytkownika.

## <a name="do-you-need-multiple-ui-maps"></a>Potrzebujesz wielu map interfejsu użytkownika?
Utwórz wiele map interfejsu użytkownika w każdym z następujących typów sytuacji:

- Kilka złożonych zbiorów złożonych formantów interfejsu użytkownika, które wspólnie wykonują operacje logiczne, takie jak Strona rejestracji w witrynie sieci Web lub strona zakupu koszyka zakupów.

- Niezależny zestaw kontrolek, do którego dostęp jest uzyskiwany z różnych punktów aplikacji, takich jak Kreator z kilkoma stronami operacji. Jeśli każda Strona kreatora jest szczególnie złożona, można utworzyć oddzielne mapy interfejsu użytkownika dla każdej strony.

## <a name="add-multiple-ui-maps"></a>Dodawanie wielu map interfejsu użytkownika

### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Aby dodać mapę interfejsu użytkownika do projektu kodowanego testu interfejsu użytkownika

1. W **Eksplorator rozwiązań**, aby utworzyć folder w projekcie kodowanego testu interfejsu użytkownika do przechowywania wszystkich map interfejsu użytkownika, kliknij prawym przyciskiem myszy plik projektu kodowanego testu interfejsu użytkownika, wskaż polecenie **Dodaj**, a następnie wybierz polecenie **Nowy folder**. Można na przykład nazwać ją `UIMaps` .

    Nowy folder zostanie wyświetlony w ramach projektu kodowanego testu interfejsu użytkownika.

2. Kliknij prawym przyciskiem myszy `UIMaps` folder, wskaż polecenie **Dodaj**, a następnie wybierz **nowy element**.

    Zostanie wyświetlone okno dialogowe **Dodaj nowy element**.

   > [!NOTE]
   > Aby dodać nową mapę kodowanego testu interfejsu użytkownika, musisz być w projekcie kodowanego testu interfejsu użytkownika.

3. Wybierz z listy pozycję **Mapa kodowanego testu interfejsu użytkownika** .

    W polu **Nazwa** wprowadź nazwę nowej mapy interfejsu użytkownika. Użyj nazwy składnika lub strony, która będzie reprezentować mapa, na przykład `HomePageMap` .

4. Wybierz pozycję **Dodaj**.

    Okno programu Visual Studio minimalizuje i zostanie wyświetlone okno dialogowe **Konstruktor kodowanego testu interfejsu użytkownika** .

5. Zarejestruj akcje dla pierwszej metody i wybierz polecenie **Generuj kod**.

6. Po zarejestrowaniu wszystkich akcji i potwierdzeń pierwszego składnika lub strony i zgrupowaniu ich w metody, Zamknij okno dialogowe **Konstruktor kodowanego testu interfejsu użytkownika** .

7. Kontynuuj tworzenie map interfejsu użytkownika. Rejestrowanie akcji i potwierdzeń, grupowanie ich w metody dla każdego składnika, a następnie Generowanie kodu.

   W wielu przypadkach okno najwyższego poziomu aplikacji pozostaje stałe dla wszystkich kreatorów, formularzy i stron. Chociaż każda Mapa interfejsu użytkownika ma klasę dla okna najwyższego poziomu, wszystkie mapy są prawdopodobnie odwołują się do tego samego okna najwyższego poziomu, w ramach którego są uruchamiane wszystkie składniki aplikacji. Kodowane testy interfejsu użytkownika przeszukają kontrolki hierarchicznie od góry w dół, rozpoczynając od okna najwyższego poziomu, a więc w złożonej aplikacji, rzeczywiste okno najwyższego poziomu może być zduplikowane w każdej mapie interfejsu użytkownika. Jeśli rzeczywiste okno najwyższego poziomu jest duplikowane, wielokrotne modyfikacje zostaną wprowadzone w przypadku zmiany tego okna. Może to spowodować problemy z wydajnością podczas przełączania map interfejsu użytkownika.

   Aby zminimalizować ten efekt, można użyć metody, `CopyFrom()` Aby upewnić się, że nowe okno najwyższego poziomu w tej mapie interfejsu użytkownika jest takie samo jak główne okno najwyższego poziomu.

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
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
