---
title: Testowanie dużej aplikacji przy użyciu wielu map UI | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
ms.assetid: 6e1ae9ec-e9b1-458a-bd96-0eb15e46f1d5
caps.latest.revision: 24
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 18180ee3277cdff60d11c0ae35e8aa3c990764de
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386048"
---
# <a name="testing-a-large-application-with-multiple-ui-maps"></a>Testowanie dużej aplikacji przy użyciu wielu map UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie omówiono sposób używania kodowanych testów interfejsu użytkownika podczas testowania dużych aplikacji przy użyciu wielu map interfejsu użytkownika.  
  
 **Wymagania**  
  
- Visual Studio Enterprise  
  
  Po utworzeniu nowego kodowanego testu interfejsu użytkownika, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] struktura testowania generuje kod dla testu domyślnie <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasy. Aby uzyskać więcej informacji na temat sposobu rejestrowania kodowane testy interfejsu użytkownika, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) i [anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md).  
  
  Kod generowany dla mapy interfejsu użytkownika zawiera klasę dla każdego obiektu, który test współdziała z. Dla każdej wygenerowanej metody do klasy pomocnika na potrzeby parametrów metody jest generowany specjalnie dla tej metody. W przypadku dużej liczby obiektów, stron i formularzy i kontrolek w aplikacji mapy interfejsu użytkownika można powiększać dużych. Ponadto jeśli kilka osób pracuje testy, aplikacja staje się niewygodna za pomocą pojedynczego dużego pliku mapy interfejsu użytkownika.  
  
  Użycie wielu plików mapy interfejsu użytkownika może zapewnić następujące korzyści:  
  
- Każda mapa może być skojarzony z podzbiorem logiczny aplikacji. Dzięki temu zmiany do zarządzania.  
  
- Każdego testera może pracować nad części aplikacji, a następnie sprawdź w ich kodzie bez zakłócania innych testerów, pracy w innych częściach aplikacji.  
  
- Dodatki do interfejsu użytkownika aplikacji mogą być skalowane przyrostowo z minimalnym wpływem na testy dla innych części interfejsu użytkownika.  
  
## <a name="do-you-need-multiple-ui-maps"></a>Czy potrzebujesz wielu map interfejsu użytkownika?  
 Tworzenie wielu map interfejsu użytkownika w każdym z tego typu sytuacje:  
  
- Kilka złożonych zestawów złożonych kontrolek interfejsu użytkownika, które wspólnie wykonują operacji logicznej, takich jak strony rejestracji w witrynie sieci Web lub strony zakupu koszyk sklepowy.  
  
- Niezależny zestaw formantów, które są dostępne w różnych punktach aplikacji, na przykład Kreator z kilku stron operacji. Jeśli każda strona kreatora jest szczególnie złożony, można utworzyć oddzielne map interfejsu użytkownika dla każdej strony.  
  
## <a name="adding-multiple-ui-maps"></a>Dodawanie wielu map UI  
  
#### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Aby dodać mapę interfejsu użytkownika do projektu kodowanego testu interfejsu użytkownika  
  
1. W **Eksploratora rozwiązań**, aby utworzyć folder w projekcie kodowanego testu interfejsu użytkownika do przechowywania wszystkich map interfejsu użytkownika, kliknij prawym przyciskiem myszy plik projektu kodowanego testu interfejsu użytkownika, wskaż **Dodaj** , a następnie wybierz **nowy Folder**. Na przykład nazwać ją `UIMaps`.  
  
    W obszarze projektu kodowanego testu interfejsu użytkownika zostanie wyświetlony nowy folder.  
  
2. Kliknij prawym przyciskiem myszy `UIMaps` folderu, wskaż **Dodaj**, a następnie wybierz **nowy element**.  
  
    **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
   > [!NOTE]
   > Musisz być w projektu kodowanego testu interfejsu użytkownika można dodać nowej mapy kodowanego testu interfejsu użytkownika.  
  
3. Wybierz **kodowanego interfejsu użytkownika testu mapy** z listy.  
  
    W **nazwa** wprowadź nazwę dla nowej mapy interfejsu użytkownika. Użyj nazwy składnika lub strona, która mapy będzie reprezentować, na przykład `HomePageMap`.  
  
4. Wybierz **Dodaj**.  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Minimalizuje okna i **kodowanego testu interfejsu użytkownika** zostanie wyświetlone okno dialogowe.  
  
5. Rejestruj akcje w przypadku pierwszej metody, a następnie wybierz **Generuj kod**.  
  
6. Zamknij po rejestrowane wszystkie akcje i potwierdzenia dla pierwszego składnika lub strony i pogrupowane metody **kodowanego testu interfejsu użytkownika** okno dialogowe.  
  
7. Kontynuuj tworzenie map interfejsu użytkownika. Rejestruj akcje i potwierdzenia, zgrupować je w metody dla każdego składnika, a następnie generowania kodu.  
  
   W wielu przypadkach okien najwyższego poziomu aplikacji pozostaje na stałym dla kreatorów, formularze i stron. Mimo że każdy mapy interfejsu użytkownika ma klasę okna najwyższego poziomu, wszystkie mapowania prawdopodobnie odwołują się do tego samego okno najwyższego poziomu w ramach której wszystkie składniki aplikacji Uruchom. Kodowanego interfejsu użytkownika testy wyszukiwania dla formantów hierarchicznie od góry do dołu, zaczynając od okna najwyższego poziomu, dzięki czemu w przypadku złożonych aplikacji w oknie rzeczywistych najwyższego poziomu można zduplikowane w każdej mapie interfejsu użytkownika. W oknie rzeczywistych najwyższego poziomu jest zduplikowany, wprowadzanie wielu modyfikacji spowoduje zmiany tego okna. Może to spowodować problemy z wydajnością podczas przełączania między map interfejsu użytkownika.  
  
   Aby zminimalizować ten efekt, można użyć `CopyFrom()` metodę, aby zapewnić, że nowe okno najwyższego poziomu w tym mapę interfejsu użytkownika jest taka sama jak główne okno najwyższego poziomu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest częścią klasy narzędzia, która zapewnia dostęp do poszczególnych składników oraz ich formantów podrzędnych, które są reprezentowane przez klasy generowane w różnych map interfejsu użytkownika.  
  
 Na przykład aplikacja sieci Web o nazwie `Contoso` ma stronę główną, stronę produktu i strony koszyka zakupów. Każda z tych stron współużytkują wspólne okno najwyższego poziomu czyli okna przeglądarki. Istnieje mapę interfejsu użytkownika dla każdej strony i klasa narzędzie ma podobny do następującego kodu:  
  
```  
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
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>   
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
