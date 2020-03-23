---
title: Tworzenie wtyczki testu wydajności sieci Web
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc2eeafa41b953f9d853c7ff435a6a9706ae73ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589113"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Jak: Tworzenie wtyczki testu wydajności sieci Web

Wtyczki testów wydajności sieci Web umożliwiają izolowanie i ponowne użycie kodu poza głównymi instrukcjami deklaratywnymi w teście wydajności sieci Web. Dostosowana wtyczka testu wydajności sieci Web oferuje sposób wywołania kodu podczas uruchamiania testu wydajności sieci Web. Wtyczka testu wydajności sieci web jest uruchamiana jeden raz dla każdej iteracji testowej. Ponadto jeśli zastąpisz Metody PreRequest lub PostRequest w testowej utyp-in, te wtyczki żądania będą uruchamiane odpowiednio przed lub po każdym żądaniu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Można utworzyć wtyczkę testu wydajności sieci web, wyprowadzając własną <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> klasę z klasy podstawowej.

Można użyć dostosowanych wtyczek testów wydajności sieci web z testami wydajności sieci Web, które zostały zarejestrowane, co umożliwia zapisanie minimalnej ilości kodu w celu uzyskania większego poziomu kontroli nad testami wydajności sieci Web. Można ich jednak również używać z kodowanych testów wydajności sieci Web. Aby uzyskać więcej informacji, zobacz [Generowanie i uruchamianie zakodowany test wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> Można również utworzyć wtyczki testowe obciążenia. Zobacz [Jak: Tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Aby utworzyć niestandardową wtyczkę testu wydajności sieci Web

1. Otwórz projekt testu wydajności sieci web i obciążenia, który zawiera test wydajności sieci web.

2. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie i wybierz pozycję **Dodaj,** a następnie wybierz pozycję **Nowy projekt**.

3. Utwórz nowy projekt **biblioteki klas.**

   Nowy projekt biblioteki klas zostanie dodany do **Eksploratora rozwiązań,** a nowa klasa pojawi się w **Edytorze kodu**.

4. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy folder **Odwołania** w nowej bibliotece klas i wybierz polecenie **Dodaj odwołanie**.

   Zostanie wyświetlone okno dialogowe **Dodawanie odwołania.**

5. Wybierz kartę **.NET,** przewiń w dół i wybierz pozycję **Microsoft.VisualStudio.QualityTools.WebTestFramework**

6. Wybierz pozycję **OK**.

     Odwołanie do **pliku Microsoft.VisualStudio.QualityTools.WebTestFramework** jest dodawane do folderu **Odwołania** w **Eksploratorze rozwiązań**.

7. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy górny węzeł projektu testu wydajności sieci web i obciążenia zawierający test obciążenia, do którego chcesz dodać wtyczkę testu wydajności sieci Web i wybierz pozycję **Dodaj odwołanie**.

8. Zostanie **wyświetlone okno dialogowe Dodawanie odwołania**.

9. Wybierz kartę **Projekty** i wybierz **projekt biblioteki klas**.

10. Wybierz pozycję **OK**.

11. W **Edytorze kodów**napisz kod wtyczki. Najpierw utwórz nową klasę publiczną, która wywodzi się z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

12. Zaimplementuj kod wewnątrz jednego lub więcej programów obsługi zdarzeń. Przykładową implementację przedstawiono w następującej sekcji Przykład.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

13. Po napisaniu kodu skompiluj nowy projekt.

14. Otwórz test wydajności sieci Web.

15. Aby dodać wtyczkę testu wydajności sieci Web, wybierz pozycję **Dodaj wtyczkę testu sieci Web** na pasku narzędzi.

     Zostanie wyświetlone okno dialogowe **Dodawanie wtyczki testu sieci Web.**

16. W obszarze **Wybierz wtyczkę**wybierz klasę wtyczki testu wydajności sieci Web.

17. W okienku **Właściwości dla wybranych wtyczek** ustaw wartości początkowe dla wtyczki do użycia w czasie wykonywania.

    > [!NOTE]
    > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Można również zmienić właściwości wtyczki testu wydajności sieci web później za pomocą okna Właściwości.

18. Wybierz pozycję **OK**.

     Wtyczka zostanie dodana do folderu **wtyczek testów internetowych.**

    > [!WARNING]
    > Po uruchomieniu testu wydajności sieci Web lub testu obciążenia, który używa wtyczki, może pojawić się błąd podobny do następującego:
    >
    > **Żądanie nie powiodło \<się: Wyjątek w> zdarzenia dodatku\<plug-in: nie można załadować pliku lub zestawu\<' "Nazwa wtyczki".dll plik>, Version= n.n.n.n>, Culture=neutral, PublicKeyToken=null' lub jedną z jego zależności. System nie może odnaleźć określonego pliku.**
    >
    > Jest to spowodowane wprowadzeniem zmian w kodzie do któregokolwiek z wtyczek i utworzeniem nowej wersji biblioteki DLL **(Version=0.0.0.0),** ale wtyczka nadal odwołuje się do oryginalnej wersji wtyczki. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1. W projekcie testu wydajności sieci web i obciążenia zostanie wyświetlone ostrzeżenie w odwołaniach. Usuń i ponownie dodaj odwołanie do biblioteki DLL wtyczek.
    > 2. Wyjmij wtyczkę z testu lub w odpowiedniej lokalizacji, a następnie dodaj ją z powrotem.

## <a name="example"></a>Przykład

Poniższy kod tworzy wtyczkę testu wydajności sieci web, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> która dodaje element do tego, który reprezentuje iterację testu.

Po uruchomieniu testu wydajności sieci Web, za pomocą tej wtyczki można zobaczyć dodany element o nazwie **TestIteratnionNumber** na karcie **Kontekst** w **przeglądarce wyników wydajności sieci Web**.

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleRules
{
    [Description("This plugin can be used to set the ParseDependentsRequests property for each request")]
    public class SampleWebTestPlugin : WebTestPlugin
    {
        private bool m_parseDependents = true;

        public override void PreWebTest(object sender, PreWebTestEventArgs e)
        {
            // TODO: Add code to execute before the test.
        }

        public override void PostWebTest(object sender, PostWebTestEventArgs e)
        {
            // TODO: Add code to execute after the test.
        }

        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            // Code to execute before each request.
            // Set the ParseDependentsRequests value on the request
            e.Request.ParseDependentRequests = m_parseDependents;
        }

        // Properties for the plugin.
        [DefaultValue(true)]
        [Description("All requests will have their ParseDependentsRequests property set to this value")]
        public bool ParseDependents
        {
            get
            {
                return m_parseDependents;
            }
            set
            {
                m_parseDependents = value;
            }
        }
    }
}
```

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Jak: Tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md)
- [Kodowania niestandardowej reguły wyodrębniania dla testu wydajności sieci Web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodowania niestandardowej reguły sprawdzania poprawności dla testu wydajności sieci Web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Jak: Tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
- [Generowanie i uruchamianie kodowanego testu wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md)
