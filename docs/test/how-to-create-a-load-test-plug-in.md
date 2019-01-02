---
title: Tworzenie wtyczki testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: 1805efbe676273ceac2f0e264e53946eea1be79f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878565"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Instrukcje: Tworzenie wtyczki testu obciążeniowego

Można utworzyć wtyczkę testu obciążeniowego służącą do uruchamiania kodu w różnych momentach podczas wykonywania testu. Celem utworzenia wtyczki jest rozszerzenie lub zmodyfikowanie wbudowanej funkcjonalności testu obciążeniowego. Można na przykład napisać kod wtyczki testu obciążeniowego, który będzie ustawiał lub modyfikował wzorzec testu obciążeniowego podczas wykonywania testu. W tym celu należy utworzyć klasę, która dziedziczy interfejs <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. Klasa musi implementować metodę <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> tego interfejsu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!NOTE]
> Można również utworzyć wtyczek dla testów wydajności sieci web. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie wtyczki testu wydajności sieci web](../test/how-to-create-a-web-performance-test-plug-in.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-load-test-plug-in-by-using-visual-c"></a>Do tworzenie wtyczki testu obciążenia przy użyciu języka Visual C#

1.  Otwórz wydajności sieci web i obciążenia projektu testowego, który zawiera test wydajności sieci web.

2.  Dodaj test obciążenia do projektu testowego i skonfigurować je do uruchomienia testu wydajności sieci web.

     Aby uzyskać więcej informacji, zobacz [Szybki Start: Tworzenie projektu testu obciążeniowego](../test/quickstart-create-a-load-test-project.md).

3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Dodaj** , a następnie wybierz **nowy projekt**.

     **Dodaj nowy projekt** zostanie wyświetlone okno dialogowe.

4.  W obszarze **zainstalowane szablony**, wybierz opcję **Visual C#**.

5.  Na liście szablonów wybierz **biblioteki klas**.

6.  W **nazwa** polu tekstowym wpisz nazwę dla swojej klasy.

7.  Wybierz **OK**.

8.  Nowy projekt biblioteki klas zostanie dodany do **Eksploratora rozwiązań** i Nowa klasa pojawi się w **Edytor kodu**.

9. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** folderu w nową bibliotekę klas i wybierz pozycję **Dodaj odwołanie**.

10. **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

11. Wybierz **.NET** karty, przewiń w dół, a następnie wybierz **Microsoft.VisualStudio.QualityTools.LoadTestFramework**.

12. Wybierz **OK**.

     Odwołanie do **Microsoft.VisualStudio.QualityTools.LoadTestFramework** jest dodawany do **odwołania** folderu w **Eksploratora rozwiązań**.

13. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy górny węzeł wydajności sieci web i załadować projekt testowy, który zawiera test obciążeniowy, do którego chcesz dodać testu obciążeniowego wtyczki i wybierz pozycję **Dodaj odwołanie**.

14. **Zostanie wyświetlone okno dialogowe Dodaj odwołanie**.

15. Wybierz **projektów** kartę, a następnie wybierz projekt biblioteki klas.

16. Wybierz **OK**.

17. W **Edytor kodu**, Dodaj `using` poufności informacji dotyczące <xref:Microsoft.VisualStudio.TestTools.LoadTesting> przestrzeni nazw.

18. Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> dla klasy, która została utworzona w projekcie Biblioteka klas. Przykładową implementację przedstawiono w następującej sekcji Przykład.

19. Po napisaniu kodu skompiluj nowy projekt.

20. Kliknij prawym przyciskiem myszy najwyższy węzeł testu obciążeniowego, a następnie wybierz **Dodaj wtyczkę testu obciążeniowego**.

     **Dodaj wtyczkę testu obciążenia** zostanie wyświetlone okno dialogowe.

21. W obszarze **Wybierz wtyczkę**, zaznacz klasę wtyczki testu obciążenia.

22. W **właściwości wybranych wtyczek** okienko, ustaw wartości początkowe dla wtyczki do użycia w czasie wykonywania.

    > [!NOTE]
    > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Możesz również zmienić właściwości wtyczki testu wydajności sieci web później za pomocą **właściwości** okna.

23. Wybierz **OK**.

     Wtyczka zostanie dodana do **wtyczki testu obciążeniowego** folderu.

    > [!WARNING]
    > Możesz otrzymać błąd podobny do następującego po uruchomieniu testu wydajności sieci web lub testu obciążenia, który korzysta z Twojej wtyczki:
    >
    > **Żądanie nie powiodło się: Wyjątek w \<wtyczki > zdarzenia: Nie można załadować pliku lub zestawu "\<pliku dll"Nazwa wtyczki">, wersja =\<n.n.n.n >, Culture = neutral, PublicKeyToken = null" lub jednej z jego zależności. System nie może odnaleźć określonego pliku.**
    >
    > Dzieje się tak Jeśli wprowadzasz zmiany kodu do dowolnego typu plug-ins i utworzyć nową wersję biblioteki DLL **(wersja = 0.0.0.0)**, ale wtyczka nadal odwołuje się do oryginalnej wersji wtyczki. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1.  W wydajności sieci web i obciążenia projektu testowego zostanie wyświetlone ostrzeżenie w odwołaniach. Usuń i ponownie Dodaj odwołanie do biblioteki DLL dodatku plug-in.
    > 2.  Usuń dodatek plug-in z testu lub odpowiedniej lokalizacji, a następnie dodaj go ponownie.

## <a name="example"></a>Przykład

Poniższy kod pokazuje wtyczkę testu obciążeniowego, która uruchamia niestandardowy kod po wystąpieniu zdarzenia LoadTestFinished. Jeśli kod jest uruchamiany na agencie testowym na zdalnym komputerze, a agent testowy nie ma usługi SMTP localhost, test obciążeniowy pozostanie w stanie „W toku”, ponieważ pojawi się okno komunikatu.

> [!NOTE]
> Poniższy kod wymaga, aby dodać odwołanie do przestrzeni nazw System.Windows.Forms.


```csharp
using System;
using Microsoft.VisualStudio.TestTools.LoadTesting;
using System.Net.Mail;
using System.Windows.Forms;

namespace LoadTestPluginTest
{
    public class MyLoadTestPlugin : ILoadTestPlugin
    {
        LoadTest myLoadTest;

        public void Initialize(LoadTest loadTest)
        {
            myLoadTest = loadTest;
            myLoadTest.LoadTestFinished += new
                EventHandler(myLoadTest_LoadTestFinished);
        }

        void myLoadTest_LoadTestFinished(object sender, EventArgs e)
        {
            try
            {
                // place custom code here
                MailAddress MyAddress = new MailAddress("someone@example.com");
                MailMessage MyMail = new MailMessage(MyAddress, MyAddress);
                MyMail.Subject = "Load Test Finished -- Admin Email";
                MyMail.Body = myLoadTest..Name + " has finished.";

                SmtpClient MySmtpClient = new SmtpClient("localhost");
                MySmtpClient.Send(MyMail);
            }

            catch (SmtpException ex)
            {
                MessageBox.Show(ex.InnerException.Message +
                    ".\r\nMake sure you have a valid SMTP.", "LoadTestPlugin", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
            }
        }
    }
}
```

Z testem obciążeniowym jest skojarzonych osiem zdarzeń, których wtyczka testu obciążeniowego może używać do uruchamiania niestandardowego kodu podczas testu obciążeniowego. Poniżej znajduje się lista zdarzeń umożliwiających dostęp do różnych okresów przebiegu testu obciążeniowego:

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Instrukcje: Tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md)