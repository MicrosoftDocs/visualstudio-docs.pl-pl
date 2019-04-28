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
manager: jillfra
ms.openlocfilehash: 71686e160fd808b2df3d399b50206bed2a6869e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979269"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Instrukcje: Tworzenie wtyczki testu obciążeniowego

Można utworzyć wtyczkę testu obciążeniowego służącą do uruchamiania kodu w różnych momentach podczas wykonywania testu. Celem utworzenia wtyczki jest rozszerzenie lub zmodyfikowanie wbudowanej funkcjonalności testu obciążeniowego. Można na przykład napisać kod wtyczki testu obciążeniowego, który będzie ustawiał lub modyfikował wzorzec testu obciążeniowego podczas wykonywania testu. W tym celu należy utworzyć klasę, która dziedziczy interfejs <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. Klasa musi implementować metodę <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> tego interfejsu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!TIP]
> Można również utworzyć wtyczek dla testów wydajności sieci web. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie wtyczki testu wydajności sieci web](../test/how-to-create-a-web-performance-test-plug-in.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>Aby utworzyć dodatek w testu obciążeniowegoC#
<!-- markdownlint-enable MD003 MD020 -->

1. Otwórz wydajności sieci web i obciążenia projektu testowego, który zawiera test wydajności sieci web.

2. Dodaj test obciążenia do projektu testowego i skonfigurować je do uruchomienia testu wydajności sieci web.

     Aby uzyskać więcej informacji, zobacz [Szybki Start: Tworzenie projektu testu obciążeniowego](../test/quickstart-create-a-load-test-project.md).

3. Dodaj nową **biblioteki klas** projektu do rozwiązania. (W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Dodaj** , a następnie wybierz **nowy projekt**.)

4. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** folderu w nową bibliotekę klas i wybierz pozycję **Dodaj odwołanie**.

   **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

5. Wybierz **.NET** karty, przewiń w dół, a następnie wybierz **Microsoft.VisualStudio.QualityTools.LoadTestFramework**.

6. Wybierz **OK**.

   Odwołanie do **Microsoft.VisualStudio.QualityTools.LoadTestFramework** jest dodawany do **odwołania** folderu w **Eksploratora rozwiązań**.

7. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy górny węzeł wydajności sieci web i załadować projekt testowy, który zawiera test obciążeniowy, do którego chcesz dodać testu obciążeniowego wtyczki i wybierz pozycję **Dodaj odwołanie**.

   **Zostanie wyświetlone okno dialogowe Dodaj odwołanie**.

8. Wybierz **projektów** kartę, a następnie wybierz projekt biblioteki klas.

9. Wybierz **OK**.

10. W **Edytor kodu**, Dodaj `using` poufności informacji dotyczące <xref:Microsoft.VisualStudio.TestTools.LoadTesting> przestrzeni nazw.

11. Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> dla klasy, która została utworzona w projekcie Biblioteka klas. Przykładową implementację przedstawiono w następującej sekcji Przykład.

12. Po napisaniu kodu skompiluj nowy projekt.

13. Kliknij prawym przyciskiem myszy najwyższy węzeł testu obciążeniowego, a następnie wybierz **Dodaj wtyczkę testu obciążeniowego**.

     **Dodaj wtyczkę testu obciążenia** zostanie wyświetlone okno dialogowe.

14. W obszarze **Wybierz wtyczkę**, zaznacz klasę wtyczki testu obciążenia.

15. W **właściwości wybranych wtyczek** okienko, ustaw wartości początkowe dla wtyczki do użycia w czasie wykonywania.

    > [!NOTE]
    > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Możesz również zmienić właściwości wtyczki testu wydajności sieci web później za pomocą **właściwości** okna.

16. Wybierz **OK**.

     Wtyczka zostanie dodana do **wtyczki testu obciążeniowego** folderu.

    > [!WARNING]
    > Możesz otrzymać błąd podobny do następującego po uruchomieniu testu wydajności sieci web lub testu obciążenia, który korzysta z Twojej wtyczki:
    >
    > **Żądanie nie powiodło się: Wyjątek w \<wtyczki > zdarzenia: Nie można załadować pliku lub zestawu "\<pliku dll"Nazwa wtyczki">, wersja =\<n.n.n.n >, Culture = neutral, PublicKeyToken = null" lub jednej z jego zależności. System nie może odnaleźć określonego pliku.**
    >
    > Dzieje się tak Jeśli wprowadzasz zmiany kodu do dowolnego typu plug-ins i utworzyć nową wersję biblioteki DLL **(wersja = 0.0.0.0)**, ale wtyczka nadal odwołuje się do oryginalnej wersji wtyczki. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1. W wydajności sieci web i obciążenia projektu testowego zostanie wyświetlone ostrzeżenie w odwołaniach. Usuń i ponownie Dodaj odwołanie do biblioteki DLL dodatku plug-in.
    > 2. Usuń dodatek plug-in z testu lub odpowiedniej lokalizacji, a następnie dodaj go ponownie.

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

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Instrukcje: Tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md)