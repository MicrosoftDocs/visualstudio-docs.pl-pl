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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: f4848fbaed6df9817cd9f0ddf16f388d855f5cd9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067657"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Porady: tworzenie wtyczki testu wydajności sieci web

Wtyczki sieci Web wydajności testów umożliwiają izolowanie i ponowne użycie kodu poza głównym deklaracyjne oświadczeń do testu wydajności sieci web. Dostosowane testu wydajności cieci web wtyczki oferuje możliwość wywołania kodu podczas uruchamiania testu wydajności sieci web. Wtyczki testu wydajności sieci web jest uruchamiane jeden raz dla każdej iteracji testu. Ponadto Jeśli zastąpisz PreRequest lub PostRequest metod w wtyczkę testu, te wtyczki żądania zostanie uruchomiony przed lub po każdym żądaniu odpowiednio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Można utworzyć dostosowane internetowego testu wydajnościowego wtyczki, wyprowadzanie klasy z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> klasy bazowej.

Umożliwia niestandardowe sieci web wydajności wtyczki testu za pomocą testów wydajności sieci web, zarejestrowanych, co pozwala na minimalnej ilości kodu, aby uzyskać wyższy poziom kontroli nad testy wydajności sieci web. Jednak umożliwia także je z kodowanego testu wydajności www. Aby uzyskać więcej informacji, zobacz [Generowanie i uruchom kodowany internetowy test wydajnościowy](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> Można również utworzyć wtyczki testu obciążenia. Zobacz [porady: tworzenie wtyczki testu obciążeniowego](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Aby utworzyć wtyczkę do niestandardowego internetowego testu wydajnościowego

1.  Otwórz wydajności sieci web i obciążenia projektu testowego, który zawiera test wydajności sieci web.

2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Dodaj** , a następnie wybierz **nowy projekt**.

     **Dodaj nowy projekt** zostanie wyświetlone okno dialogowe.

3.  W obszarze **zainstalowane szablony**, wybierz opcję **Visual C#**.

4.  Na liście szablonów wybierz **biblioteki klas**.

5.  W **nazwa** polu tekstowym wpisz nazwę dla swojej klasy.

6.  Wybierz **OK**.

7.  Nowy projekt biblioteki klas zostanie dodany do **Eksploratora rozwiązań** i Nowa klasa pojawi się w **Edytor kodu**.

8.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** folderu w nową bibliotekę klas i wybierz pozycję **Dodaj odwołanie**.

9. **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

10. Wybierz **.NET** karty, przewiń w dół i wybierz **Microsoft.VisualStudio.QualityTools.WebTestFramework**

11. Wybierz **OK**.

     Odwołanie do **Microsoft.VisualStudio.QualityTools.WebTestFramework** jest dodawany do **odwołania** folderu w **Eksploratora rozwiązań**.

12. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy górny węzeł wydajności sieci web i załadować projekt testowy, który zawiera test obciążeniowy, do którego chcesz dodać test wydajności sieci web dodatku typu plug-in i wybierz pozycję **Dodaj odwołanie**.

13. **Zostanie wyświetlone okno dialogowe Dodaj odwołanie**.

14. Wybierz **projektów** kartę, a następnie wybierz pozycję **projekt biblioteki klas**.

15. Wybierz **OK**.

16. W **Edytor kodu**, wpisać kod wtyczkę. Najpierw utwórz nową klasę publiczną, która pochodzi od klasy <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

17. Zaimplementuj kod wewnątrz co najmniej jedną z procedur obsługi zdarzeń. Przykładową implementację przedstawiono w następującej sekcji Przykład.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

18. Po napisaniu kodu skompiluj nowy projekt.

19. Otwórz test wydajności sieci web.

20. Aby dodać wtyczkę testu wydajności sieci web, wybierz **Dodaj wtyczkę testu sieci Web** na pasku narzędzi.

     **Dodaj wtyczkę testu sieci Web** zostanie wyświetlone okno dialogowe.

21. W obszarze **Wybierz wtyczkę**, zaznacz klasę wtyczki testu wydajności sieci web.

22. W **właściwości wybranych wtyczek** okienko, ustaw wartości początkowe dla wtyczki do użycia w czasie wykonywania.

    > [!NOTE]
    > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Właściwości wtyczki testu wydajności sieci web można również zmienić później, przy użyciu okna właściwości.

23. Wybierz **OK**.

     Wtyczka zostanie dodana do **wtyczki testu sieci Web** folderu.

    > [!WARNING]
    > Możesz otrzymać błąd podobny do następującego po uruchomieniu testu wydajności sieci web lub testu obciążenia, który korzysta z Twojej wtyczki:
    >
    > **Żądanie nie powiodło się: wyjątek w \<wtyczki > zdarzeń: nie można załadować pliku lub zestawu "\<pliku dll"Nazwa wtyczki">, wersji =\<n.n.n.n >, Culture = neutral, PublicKeyToken = null" lub jednej z jego zależności. System nie może odnaleźć określonego pliku.**
    >
    > Dzieje się tak Jeśli wprowadzasz zmiany kodu do dowolnego typu plug-ins i utworzyć nową wersję biblioteki DLL **(wersja = 0.0.0.0)**, ale wtyczka nadal odwołuje się do oryginalnej wersji wtyczki. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1.  W wydajności sieci web i obciążenia projektu testowego zostanie wyświetlone ostrzeżenie w odwołaniach. Usuń i ponownie Dodaj odwołanie do biblioteki DLL dodatku plug-in.
    > 2.  Usuń dodatek plug-in z testu lub odpowiedniej lokalizacji, a następnie dodaj go ponownie.

## <a name="example"></a>Przykład

Poniższy kod tworzy niestandardowe testu wydajności sieci web dodatku typu plug-in, dodaje element do <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> reprezentujący iterację testu.

Po uruchomieniu testu wydajności sieci web, korzystając z tej wtyczki widać dodanego elementu, który nosi nazwę **TestIteratnionNumber** w **kontekstu** karcie **podglądu wyników wydajności sieci Web** .

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
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Porady: tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md)
- [Kod niestandardowej reguły wyodrębniania dla testów wydajności sieci web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kod niestandardowej reguły walidacji dla testów wydajności sieci web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Porady: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
- [Generowanie i uruchom kodowany internetowy test wydajnościowy](../test/generate-and-run-a-coded-web-performance-test.md)