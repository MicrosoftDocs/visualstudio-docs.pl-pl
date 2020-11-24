---
title: Tworzenie Plug-In testów wydajności sieci Web
description: Dowiedz się, w jaki sposób wtyczki testów wydajności sieci Web umożliwiają ponowne użycie kodu poza głównymi instrukcjami w teście wydajności sieci Web.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ddb46b3e83c86396dfea6fbcdb3584882591fce
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442342"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Instrukcje: tworzenie wtyczki testu wydajności sieci Web

Wtyczki testów wydajności sieci Web umożliwiają izolowanie i ponowne użycie kodu poza głównymi instrukcjami deklaracyjne w teście wydajności sieci Web. Dostosowana wtyczka testu wydajności sieci Web umożliwia wywoływanie kodu w miarę przebiegu testu wydajności sieci Web. Wtyczka test wydajności sieci Web jest uruchamiana jednokrotnie dla każdej iteracji testu. Ponadto, jeśli zastąpisz metody żądania wstępnego lub PostRequest w dodatku plug-in testu, te wtyczki zostaną uruchomione przed lub po każdym żądaniu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Możesz utworzyć dostosowaną wtyczkę testu wydajności sieci Web, wprowadzając własną klasę z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> klasy bazowej.

Możesz użyć niestandardowych wtyczek do testowania wydajności sieci Web z zarejestrowanymi testami wydajności sieci Web, co umożliwia pisanie minimalnej ilości kodu w celu uzyskania wyższego poziomu kontroli nad testami wydajności sieci Web. Można ich również używać z kodowanymi testami wydajności sieci Web. Aby uzyskać więcej informacji, zobacz [generowanie i uruchamianie kodowanego testu wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> Możesz również utworzyć wtyczki testów obciążenia. Zobacz [jak: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Aby utworzyć niestandardową wtyczkę testu wydajności sieci Web

1. Otwórz projekt testu wydajności i obciążenia sieci Web, który zawiera test wydajności sieci Web.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz pozycję **Dodaj** , a następnie wybierz pozycję **Nowy projekt**.

3. Utwórz nowy projekt **biblioteki klas** .

   Nowy projekt biblioteki klas zostanie dodany do **Eksplorator rozwiązań** , a nowa klasa pojawi się w **edytorze kodu**.

4. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy folder **odwołania** w nowej bibliotece klas i wybierz polecenie **Dodaj odwołanie**.

   Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .

5. Wybierz kartę **.NET** , przewiń w dół i wybierz pozycję **Microsoft. VisualStudio. QualityTools. WebTestFramework**

6. Wybierz przycisk **OK**.

     Odwołanie do **Microsoft. VisualStudio. QualityTools. WebTestFramework** jest dodawane do folderu **Reference** w **Eksplorator rozwiązań**.

7. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy górny węzeł projektu testowego wydajności i obciążenia sieci Web, który zawiera test obciążenia, do którego chcesz dodać wtyczkę test wydajności sieci Web, a następnie wybierz pozycję **Dodaj odwołanie**.

8. **Zostanie wyświetlone okno dialogowe Dodawanie odwołania**.

9. Wybierz kartę **projekty** i wybierz **projekt Biblioteka klas**.

10. Wybierz przycisk **OK**.

11. W **edytorze kodu** Napisz kod wtyczki. Najpierw utwórz nową klasę publiczną, która pochodzi od <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> .

12. Zaimplementuj kod wewnątrz co najmniej jednego programu obsługi zdarzeń. Przykładową implementację przedstawiono w następującej sekcji Przykład.

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

15. Aby dodać wtyczkę test wydajności sieci Web, wybierz pozycję **Dodaj wtyczkę testu sieci Web** na pasku narzędzi.

     Zostanie wyświetlone okno dialogowe **Dodawanie wtyczki testu sieci Web** .

16. W obszarze **wybierz wtyczkę** wybierz klasę wtyczki testu wydajności sieci Web.

17. We **właściwościach wybranego okienka wtyczek** Ustaw początkowe wartości dla wtyczki, które mają być używane w czasie wykonywania.

    > [!NOTE]
    > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Możesz również zmienić właściwości wtyczki testu wydajności sieci Web później za pomocą okno Właściwości.

18. Wybierz przycisk **OK**.

     Wtyczka zostanie dodana do folderu **wtyczki testu sieci Web** .

    > [!WARNING]
    > Po uruchomieniu testu wydajności sieci Web lub testu obciążenia, który korzysta z wtyczki, może zostać wyświetlony błąd podobny do poniższego:
    >
    > **Żądanie nie powiodło się: wyjątek w \<plug-in> zdarzeniu: nie można załadować pliku lub zestawu " \<"Plug-in name".dll file> , Version = \<n.n.n.n> , Culture = neutral, PublicKeyToken = null" lub jednej z jego zależności. System nie może znaleźć określonego pliku.**
    >
    > Jest to spowodowane wprowadzeniem zmian w kodzie w dowolnych wtyczkach i utworzenie nowej wersji biblioteki DLL **(Version = 0.0.0.0)**, ale wtyczka nadal odwołuje się do oryginalnej wersji wtyczki. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1. W projekcie testu wydajności i obciążenia sieci Web zobaczysz ostrzeżenie w odwołaniach. Usuń i Dodaj odwołanie do biblioteki DLL wtyczki.
    > 2. Usuń wtyczkę z testu lub odpowiedniej lokalizacji, a następnie dodaj ją ponownie.

## <a name="example"></a>Przykład

Poniższy kod tworzy dostosowaną wtyczkę testu wydajności sieci Web, która dodaje element do <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> , który reprezentuje iterację testu.

Po uruchomieniu testu wydajności sieci Web za pomocą tej wtyczki można zobaczyć dodany element o nazwie **TestIteratnionNumber** na karcie **kontekst** w **podglądzie wyników wydajności sieci Web**.

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

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Instrukcje: tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md)
- [Kod reguły wyodrębniania niestandardowego dla testu wydajności sieci Web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kod reguły niestandardowego sprawdzania poprawności dla testu wydajności sieci Web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Instrukcje: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
- [Generowanie i uruchamianie kodowanego testu wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md)
