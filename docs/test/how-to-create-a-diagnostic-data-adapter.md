---
title: 'Porady: tworzenie adaptera danych diagnostycznych'
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 43519a96e0718a0864065864d9dd4fbd2ac16b23
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288081"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Instrukcje: Tworzenie adaptera danych diagnostycznych

Aby utworzyć *adapter danych diagnostycznych*, należy utworzyć bibliotekę klas przy użyciu programu Visual Studio, a następnie dodać do biblioteki klas interfejsy API adaptera danych diagnostycznych udostępniane przez Visual Studio Enterprise. Wyślij wszystkie informacje, które mają zostać przesłane jako strumień lub plik do <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> dostarczone przez platformę, podczas obsługi zdarzeń, które są wywoływane podczas przebiegu testu. Strumienie lub pliki wysyłane do programu <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> są przechowywane jako załączniki do wyników testu, gdy test zakończy się. Jeśli tworzysz usterkę z tych wyników testów lub używasz [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)] , pliki są również połączone z usterką.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Można utworzyć adapter danych diagnostycznych, który ma wpływ na komputer, na którym są uruchamiane testy, lub maszynę, która jest częścią środowiska używanego do uruchamiania testowanej aplikacji. Przykładowo zbieranie plików na maszynie testowej, w której testy są uruchamiane, lub zbieranie plików na komputerze obsługującym rolę serwera sieci Web dla aplikacji.

Możesz nadać karcie danych diagnostycznych przyjazną nazwę wyświetlaną podczas tworzenia ustawień testu przy użyciu programu Visual Studio lub Microsoft Test Manager (przestarzałe w programie Visual Studio 2017). Ustawienia testu umożliwiają zdefiniowanie, która rola maszyny będzie uruchamiać określone adaptery danych diagnostycznych w środowisku podczas uruchamiania testów. Możesz również skonfigurować adaptery danych diagnostycznych podczas tworzenia ustawień testu. Można na przykład utworzyć adapter danych diagnostycznych, który zbiera niestandardowe dzienniki z serwera sieci Web. Podczas tworzenia ustawień testu można wybrać opcję uruchomienia tego adaptera danych diagnostycznych na komputerze lub na maszynach, które wykonują tę rolę serwera sieci Web, a także zmodyfikować konfigurację ustawień testu, aby zebrać tylko ostatnie trzy ostatnio utworzone dzienniki. Aby uzyskać więcej informacji na temat ustawień testowych, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

Zdarzenia są wywoływane po uruchomieniu testów, aby adapter danych diagnostycznych mógł wykonywać zadania w tym punkcie testu.

> [!IMPORTANT]
> Te zdarzenia mogą być wywoływane w różnych wątkach, zwłaszcza gdy testy są uruchomione na wielu komputerach. W związku z tym trzeba mieć świadomość ewentualnych problemów z wątkami i niezamierzonego uszkodzenia danych wewnętrznych karty niestandardowej. Upewnij się, że adapter danych diagnostycznych jest bezpieczny wątkowo.

Poniżej znajduje się częściowa lista kluczowych zdarzeń, których można użyć podczas tworzenia adaptera danych diagnostycznych. Aby uzyskać pełną listę zdarzeń karty danych diagnostycznych, zobacz Klasa abstract <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> .

|Zdarzenie|Opis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Początek przebiegu testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Koniec przebiegu testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Początek każdego testu w przebiegu testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Koniec każdego testu w przebiegu testowym|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Początek każdego kroku testu w teście|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Koniec każdego kroku testu w teście|

> [!NOTE]
> Po zakończeniu testu ręcznego żadne zdarzenia zbierania danych nie są wysyłane do adaptera danych diagnostycznych. Gdy test zostanie uruchomiony ponownie, będzie miał nowy identyfikator przypadku testowego. Jeśli użytkownik resetuje test w trakcie testu (który wywołuje <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> zdarzenie) lub zmienia wynik kroku testu, żadne zdarzenie zbierania danych nie jest wysyłane do adaptera danych diagnostycznych, ale identyfikator przypadku testowego pozostaje taka sama. Aby określić, czy przypadek testowy został zresetowany, należy śledzić identyfikator przypadku testowego na karcie danych diagnostycznych.

Poniższa procedura umożliwia utworzenie adaptera danych diagnostycznych, który zbiera dane na podstawie informacji skonfigurowanych podczas tworzenia ustawień testu.

Aby zapoznać się z kompletnym przykładowym projektem adaptera danych diagnostycznych, w tym niestandardowym edytorem konfiguracji, zobacz [przykładowy projekt do tworzenia adaptera danych diagnostycznych](../test/quickstart-create-a-load-test-project.md).

## <a name="create-and-install-a-diagnostic-data-adapter"></a>Tworzenie i Instalowanie adaptera danych diagnostycznych

1. Utwórz nowy projekt **biblioteki klas** .

2. Dodaj zestaw **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

   1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania** i wybierz polecenie **Dodaj odwołanie** .

   2. Wybierz pozycję **.NET** i Znajdź **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

   3. Wybierz przycisk **OK**.

3. Dodaj zestaw **Microsoft. VisualStudio. QualityTools. Common**.

   1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania** i wybierz polecenie **Dodaj odwołanie** .

   2. Wybierz pozycję **/.NET**, a następnie Znajdź **Microsoft.VisualStudio.QualityTools.Common.dll**.

   3. Wybierz przycisk **OK**.

4. Dodaj następujące `using` dyrektywy do pliku klasy:

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> do klasy dla karty danych diagnostycznych, aby zidentyfikować ją jako adapter danych diagnostycznych, zastępując **firmę**, **produkt**i **wersję** odpowiednimi informacjami dla adaptera danych diagnostycznych:

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> atrybut do klasy, zastępując parametry odpowiednimi informacjami dla adaptera danych diagnostycznych:

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    Ta przyjazna nazwa jest wyświetlana w działaniu ustawień testu.

   > [!NOTE]
   > Możesz również dodać, <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> Aby określić `Type` niestandardowy Edytor konfiguracji dla tej karty danych i opcjonalnie określić plik pomocy, który ma być używany przez Edytor.
   >
   > Można również zastosować, <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> Aby określić, że powinien być zawsze włączony.

7. Klasa adaptera danych diagnostycznych musi dziedziczyć z <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> klasy w następujący sposób:

   ```csharp
   public class MyDiagnosticDataAdapter : DataCollector
   ```

8. Dodaj zmienne lokalne w następujący sposób:

   ```csharp
   private DataCollectionEvents dataEvents;
   private DataCollectionLogger dataLogger;
   private DataCollectionSink dataSink;
   private XmlElement configurationSettings;
   ```

9. Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> metodę i metodę **Dispose** . W `Initialize` metodzie należy zainicjować ujścia danych, dowolne dane konfiguracji z ustawień testu i zarejestrować procedury obsługi zdarzeń, które mają być używane w następujący sposób:

    ```csharp
    public override void Initialize(
        XmlElement configurationElement,
        DataCollectionEvents events,
        DataCollectionSink sink,
        DataCollectionLogger logger,
        DataCollectionEnvironmentContext environmentContext)
    {
           dataEvents = events;  // The test events
           dataLogger = logger;  // The error and warning log
           dataSink = sink;      // Saves collected data
           // Configuration from the test settings
           configurationSettings = configurationElement;

           // Register common events for the data collector
           // Not all of the events are used in this class
        dataEvents.SessionStart +=
            new EventHandler<SessionStartEventArgs>(OnSessionStart);
        dataEvents.SessionEnd +=
            new EventHandler<SessionEndEventArgs>(OnSessionEnd);
        dataEvents.TestCaseStart +=
            new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
        dataEvents.TestCaseEnd +=
            new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
    }

    public override void Dispose(bool disposing)
    {
        if (disposing)
        {
            // Unregister the registered events
            dataEvents.SessionStart -=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd -=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart -=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd -=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
        }
    }
    ```

10. Użyj następującego kodu programu obsługi zdarzeń i metody prywatnej, aby zebrać plik dziennika wygenerowany podczas testu:

    ```csharp
    public void OnTestCaseEnd(sender, TestCaseEndEventArgs e)
    {
        // Get any files to be collected that are
        // configured in your test settings
        List<string> files = getFilesToCollect();

        // For each of the files, send the file to the data sink
        // which will attach it to the test results or to a bug
        foreach (string file in files)
        {
            dataSink.SendFileAsync(e.Context, file, false);
        }
    }

    // A private method that returns the file names
    private List<string> getFilesToCollect()
    {
        // Get a namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                configurationSettings.OwnerDocument.NameTable);
        nsmgr.AddNamespace("ns",
            "http://MyCompany/schemas/MyDataCollector/1.0");

        // Find all of the "File" elements under our configuration
        XmlNodeList files =
            configurationSettings.SelectNodes(
                "//ns:MyDataCollector/ns:File");

        // Build the list of files to collect from the
        // "FullPath" attributes of the "File" nodes.
        List<string> result = new List<string>();
        foreach (XmlNode fileNode in files)
        {
            XmlAttribute pathAttribute =
                fileNode.Attributes["FullPath"];
            if (pathAttribute != null &&
                !String.IsNullOrEmpty(pathAttribute.Value))
            {
                result.Add(pathAttribute.Value);
            }
        }

        return result;
    }
    ```

     Te pliki są dołączone do wyników testu. Jeśli tworzysz usterkę z tych wyników testów lub używasz [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)] , pliki są również dołączone do usterki.

     Jeśli chcesz użyć własnego edytora do zbierania danych do użycia w ustawieniach testu, zobacz [jak to zrobić: Tworzenie niestandardowego edytora dla danych dla karty danych diagnostycznych](../test/quickstart-create-a-load-test-project.md).

11. Aby zebrać plik dziennika, gdy test zakończy się w oparciu o to, co użytkownik skonfigurował w ustawieniach testu, należy utworzyć plik *App.config* i dodać go do rozwiązania. Ten plik ma następujący format i musi zawierać identyfikator URI adaptera danych diagnostycznych w celu jego zidentyfikowania. Podstaw wartości rzeczywiste dla "Firma/ProductName/wersja".

    > [!NOTE]
    > Jeśli nie trzeba konfigurować żadnych informacji dla karty danych diagnostycznych, nie trzeba tworzyć pliku konfiguracji.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <configSections>
        <section name="DataCollectorConfiguration" type="Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationSection, Microsoft.VisualStudio.QualityTools.ExecutionCommon, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a "/>
      </configSections>
      <DataCollectorConfiguration xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/2010">
        <DataCollector typeUri="datacollector://MyCompany/MyProduct/1.0">
          <DefaultConfiguration>
            <!-- Your default config settings -->
            <Binaries>
              <Binary FullPath="C:\Example\Example.dll"/>
              <Binary FullPath="\\Server2\Example2.dll"/>
            </Binaries>
            <Symbols>
              <Symbol FullPath="\\ExampleServer\ExampleSymbol.pdb"/>
            </Symbols>
          </DefaultConfiguration>
        </DataCollector>
      </DataCollectorConfiguration>
    </configuration>
    ```

    > [!NOTE]
    > Domyślny element konfiguracji może zawierać wymagane dane. Jeśli użytkownik nie skonfiguruje adaptera danych diagnostycznych w ustawieniach testu, domyślne dane zostaną przesłane do adaptera danych diagnostycznych, gdy zostanie on uruchomiony. Ponieważ kod XML, który dodasz do `<DefaultConfigurations>` sekcji, prawdopodobnie nie będzie częścią zadeklarowanego schematu, można zignorować wszystkie wygenerowane błędy XML.
    >
    > Istnieją inne przykłady plików konfiguracji w następującej ścieżce w oparciu o katalog instalacyjny: *Program Files\Microsoft Visual Studio 10.0 \ Common7\IDE\PrivateAssemblies\DataCollectors*.

     Aby uzyskać więcej informacji na temat sposobu konfigurowania ustawień testu do korzystania ze środowiska podczas uruchamiania testów, zobacz [zbieranie danych diagnostycznych w testach ręcznych (Azure test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

     Aby uzyskać więcej informacji na temat instalowania pliku konfiguracji, zobacz [How to: Install a Custom Diagnostic Data adapter](../test/quickstart-create-a-load-test-project.md)

12. Skompiluj rozwiązanie, aby utworzyć zestaw adaptera danych diagnostycznych.

13. Informacje o instalowaniu edytora niestandardowego można znaleźć w temacie [How to: Install a Custom Diagnostic Data adapter](../test/quickstart-create-a-load-test-project.md).

14. Aby uzyskać więcej informacji na temat sposobu konfigurowania ustawień testu do korzystania ze środowiska podczas uruchamiania testów, zobacz [zbieranie danych diagnostycznych w testach ręcznych (Azure test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

15. Aby wybrać adapter danych diagnostycznych, należy najpierw wybrać istniejące ustawienia testu lub utworzyć nowe z programu Visual Studio lub Microsoft Test Manager (przestarzałe w programie Visual Studio 2017). Karta jest wyświetlana na karcie **dane i Diagnostyka** ustawień testu z przyjazną nazwą, która została przypisana do klasy.

16. Ustaw te ustawienia testu jako aktywne. Aby uzyskać więcej informacji na temat ustawień testowych, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

17. Uruchom testy przy użyciu ustawień testowych z wybraną kartą danych diagnostycznych.

    Określony plik danych jest dołączany do wyników testu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Zbieranie informacji diagnostycznych za pomocą ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Zbieranie danych diagnostycznych w testach ręcznych (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Zbieraj dane diagnostyczne podczas testowania (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Instrukcje: Tworzenie niestandardowego edytora dla danych dla adaptera danych diagnostycznych](../test/quickstart-create-a-load-test-project.md)
