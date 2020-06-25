---
title: Tworzenie wtyczki testu obciążenia
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0abcc3865c21a4f4673331377af8d17b223c7875
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288029"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Instrukcje: tworzenie wtyczki testu obciążenia

Można utworzyć wtyczkę testu obciążeniowego służącą do uruchamiania kodu w różnych momentach podczas wykonywania testu. Celem utworzenia wtyczki jest rozszerzenie lub zmodyfikowanie wbudowanej funkcjonalności testu obciążeniowego. Można na przykład napisać kod wtyczki testu obciążeniowego, który będzie ustawiał lub modyfikował wzorzec testu obciążeniowego podczas wykonywania testu. W tym celu należy utworzyć klasę, która dziedziczy interfejs <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. Klasa musi implementować metodę <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> tego interfejsu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!TIP]
> Możesz również utworzyć wtyczki dla testów wydajności sieci Web. Aby uzyskać więcej informacji, zobacz [How to: Create a Web Performance test plug-in](../test/how-to-create-a-web-performance-test-plug-in.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>Aby utworzyć wtyczkę testu obciążenia w języku C #
<!-- markdownlint-enable MD003 MD020 -->

1. Otwórz projekt testu wydajności i obciążenia sieci Web, który zawiera test wydajności sieci Web.

2. Dodaj test obciążenia do projektu testowego i skonfiguruj go tak, aby uruchamiał test wydajności sieci Web.

     Aby uzyskać więcej informacji, zobacz [Szybki Start: Tworzenie projektu testu obciążenia](../test/quickstart-create-a-load-test-project.md).

3. Dodaj nowy projekt **biblioteki klas** do rozwiązania. (W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz pozycję **Dodaj** , a następnie wybierz pozycję **Nowy projekt**).

4. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder **odwołania** w nowej bibliotece klas i wybierz polecenie **Dodaj odwołanie**.

   Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .

5. Wybierz kartę **.NET** , przewiń w dół, a następnie wybierz pozycję **Microsoft. VisualStudio. QualityTools. LoadTestFramework**.

6. Wybierz przycisk **OK**.

   Odwołanie do **Microsoft. VisualStudio. QualityTools. LoadTestFramework** jest dodawane do folderu **Reference** w **Eksplorator rozwiązań**.

7. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy górny węzeł projektu testu wydajności i obciążenia sieci Web, który zawiera test obciążenia, do którego chcesz dodać wtyczkę testu obciążenia, a następnie wybierz pozycję **Dodaj odwołanie**.

   **Zostanie wyświetlone okno dialogowe Dodawanie odwołania**.

8. Wybierz kartę **projekty** i wybierz projekt Biblioteka klas.

9. Wybierz przycisk **OK**.

10. W **edytorze kodu**Dodaj `using` instrukcję dla <xref:Microsoft.VisualStudio.TestTools.LoadTesting> przestrzeni nazw.

11. Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> dla klasy, która została utworzona w projekcie Biblioteka klas. Przykładową implementację przedstawiono w następującej sekcji Przykład.

12. Po napisaniu kodu skompiluj nowy projekt.

13. Kliknij prawym przyciskiem myszy górny węzeł testu obciążenia, a następnie wybierz polecenie **Dodaj wtyczkę testu obciążenia**.

     Zostanie wyświetlone okno dialogowe **Dodaj wtyczkę testu obciążenia** .

14. W obszarze **wybierz wtyczkę**wybierz klasę wtyczki testu obciążenia.

15. We **właściwościach wybranego okienka wtyczek** Ustaw początkowe wartości dla wtyczki, które mają być używane w czasie wykonywania.

    > [!NOTE]
    > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Możesz również zmienić właściwości wtyczki testu wydajności sieci Web później za pomocą okna **Właściwości** .

16. Wybierz przycisk **OK**.

     Wtyczka jest dodawana do folderu **wtyczki testów obciążenia** .

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

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Instrukcje: tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md)
