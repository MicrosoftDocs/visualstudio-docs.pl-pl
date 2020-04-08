---
title: 'Porady: tworzenie adaptera danych diagnostycznych'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b198d8d3e9156b8a38325034bf19ce96b742d9e
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880159"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Jak: Tworzenie karty danych diagnostycznych

Aby utworzyć *kartę danych diagnostycznych,* należy utworzyć bibliotekę klas za pomocą programu Visual Studio, a następnie dodać interfejsy API karty danych diagnostycznych dostarczone przez program Visual Studio Enterprise do biblioteki klas. Wyślij wszelkie informacje, które mają jako strumień <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> lub plik do dostarczonych przez platformę, podczas obsługi zdarzeń, które są wywoływane podczas przebiegu testu. Strumienie lub pliki wysyłane <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> do są przechowywane jako załączniki do wyników testów po zakończeniu testu. Jeśli utworzysz błąd z tych wyników [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)]testów lub gdy używasz , pliki są również połączone z błędem.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Można utworzyć kartę danych diagnostycznych, która wpływa na komputer, na którym są uruchamiane testy, lub komputer, który jest częścią środowiska używanego do uruchamiania aplikacji w ramach testu. Na przykład zbieranie plików na komputerze testowym, gdzie są uruchamiane testy lub zbieranie plików na komputerze obsługującym rolę serwera sieci web dla aplikacji.

Można nadać karcie danych diagnostycznych przyjazną nazwę, która jest wyświetlana podczas tworzenia ustawień testu przy użyciu programu Visual Studio lub Programu Microsoft Test Manager (przestarzałe w programie Visual Studio 2017). Ustawienia testowe umożliwiają zdefiniowanie roli komputera, która będzie uruchamiać określone karty danych diagnostycznych w danym środowisku po uruchomieniu testów. Można również skonfigurować karty danych diagnostycznych podczas tworzenia ustawień testu. Na przykład można utworzyć kartę danych diagnostycznych, która zbiera dzienniki niestandardowe z serwera sieci web. Podczas tworzenia ustawień testu, można wybrać, aby uruchomić tę kartę danych diagnostycznych na komputerze lub komputerach, które wykonują tę rolę serwera sieci web i można zmodyfikować konfigurację dla ustawień testu, aby zebrać tylko trzy ostatnie dzienniki, które zostały utworzone. Aby uzyskać więcej informacji o ustawieniach testu, zobacz [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

Zdarzenia są wywoływane po uruchomieniu testów, dzięki czemu karta danych diagnostycznych może wykonywać zadania w tym momencie w teście.

> [!IMPORTANT]
> Te zdarzenia mogą być wywoływane w różnych wątkach, zwłaszcza gdy masz testy uruchomione na wielu komputerach. W związku z tym należy pamiętać o możliwych problemów wątków i nie przypadkowo uszkodzić wewnętrzne dane karty niestandardowej. Upewnij się, że karta danych diagnostycznych jest bezpieczna dla wątków.

Poniżej znajduje się częściowa lista kluczowych zdarzeń, których można użyć podczas tworzenia karty danych diagnostycznych. Aby uzyskać pełną listę zdarzeń karty danych <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> diagnostycznych, zobacz klasy abstrakcyjnej.

|Wydarzenie|Opis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Początek serii próbnej|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Koniec przebiegu testowego|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Początek każdego testu w przebiegu testowym|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Koniec każdego testu w serii próbnej|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Początek każdego etapu testu w teście|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Koniec każdego etapu testu w teście|

> [!NOTE]
> Po zakończeniu testu ręcznego nie więcej zdarzeń zbierania danych są wysyłane do karty danych diagnostycznych. Po ponownym uruchomieniu testu będzie miał nowy identyfikator przypadku testowego. Jeśli użytkownik resetuje test podczas testu (który <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> wywołuje zdarzenie) lub zmienia wynik kroku testu, żadne zdarzenie zbierania danych nie jest wysyłane do karty danych diagnostycznych, ale identyfikator przypadku testowego pozostaje taki sam. Aby ustalić, czy przypadek testowy został zresetowany, należy śledzić identyfikator przypadku testowego w karcie danych diagnostycznych.

Poniższa procedura służy do tworzenia karty danych diagnostycznych, która zbiera plik danych, który jest oparty na informacjach, które można skonfigurować podczas tworzenia ustawień testu.

Aby uzyskać kompletny przykładowy przykładowy projekt karty danych diagnostycznych, w tym niestandardowy edytor konfiguracji, zobacz [Przykładowy projekt tworzenia karty danych diagnostycznych](../test/quickstart-create-a-load-test-project.md).

## <a name="create-and-install-a-diagnostic-data-adapter"></a>Tworzenie i instalowanie karty danych diagnostycznych

1. Utwórz nowy projekt **biblioteki klas.**

2. Dodaj zestaw **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

   1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję Odwołania** i wybierz polecenie Dodaj **odwołanie.**

   2. Wybierz **pozycję .NET** i znajdź **plik Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

   3. Wybierz pozycję **OK**.

3. Dodaj zestaw **Microsoft.VisualStudio.QualityTools.Common**.

   1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję Odwołania** i wybierz polecenie Dodaj **odwołanie.**

   2. Wybierz **/.NET**, znajdź **witrynę Microsoft.VisualStudio.QualityTools.Common.dll**.

   3. Wybierz pozycję **OK**.

4. Dodaj do `using` pliku klasy następujące dyrektywy:

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> do klasy kartę danych diagnostycznych, aby zidentyfikować ją jako kartę danych diagnostycznych, zastępując **firmę,** **produkt**i **wersję** odpowiednimi informacjami dla karty danych diagnostycznych:

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> atrybut do klasy, zastępując parametry odpowiednimi informacjami dla karty danych diagnostycznych:

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    Ta przyjazna nazwa jest wyświetlana w działaniu ustawień testu.

   > [!NOTE]
   > Można również <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> dodać, aby `Type` określić edytor konfiguracji niestandardowej dla tej karty danych i opcjonalnie określić plik pomocy do użycia w edytorze.
   >
   > Można również <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> zastosować, aby określić, że zawsze powinna być włączona.

7. Klasa karty danych diagnostycznych <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> musi dziedziczyć z klasy w następujący sposób:

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

9. Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> metodę i **Dispose** metody. W `Initialize` metodzie należy zainicjować ujście danych, wszelkie dane konfiguracyjne z ustawień testu i zarejestrować programy obsługi zdarzeń, które mają być używane w następujący sposób:

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

10. Użyj następującego kodu obsługi zdarzeń i prywatnej metody do zbierania pliku dziennika wygenerowanego podczas testu:

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

     Pliki te są dołączone do wyników testów. Jeśli utworzysz błąd z tych wyników [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)]testów lub gdy używasz , pliki są również dołączone do błędu.

     Jeśli chcesz używać własnego edytora do zbierania danych do użycia w ustawieniach testu, zobacz [Jak: Tworzenie niestandardowego edytora danych dla karty danych diagnostycznych](../test/quickstart-create-a-load-test-project.md).

11. Aby zebrać plik dziennika po zakończeniu testu na podstawie tego, co użytkownik skonfigurowany w ustawieniach testu, należy utworzyć plik *App.config* i dodać go do rozwiązania. Ten plik ma następujący format i musi zawierać identyfikator URI dla karty danych diagnostycznych, aby go zidentyfikować. Zastąp wartości rzeczywiste dla "Company/ProductName/Version".

    > [!NOTE]
    > Jeśli nie trzeba konfigurować żadnych informacji dla karty danych diagnostycznych, nie trzeba tworzyć pliku konfiguracyjnego.

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
    > Domyślny element konfiguracji może zawierać wszystkie wymagane dane. Jeśli użytkownik nie skonfiguruje karty danych diagnostycznych w ustawieniach testu, domyślne dane zostaną przekazane do karty danych diagnostycznych po jej wykonaniu. Ponieważ kod XML dodawany do `<DefaultConfigurations>` sekcji prawdopodobnie nie będzie częścią zadeklarowanego schematu, można zignorować wszystkie błędy XML, które generuje.
    >
    > Istnieją inne przykłady plików konfiguracyjnych w następującej ścieżce na podstawie katalogu instalacji: *Pliki programu\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\DataCollectors*.

     Aby uzyskać więcej informacji na temat konfigurowania ustawień testu do używania środowiska po uruchomieniu testów, zobacz [Zbieranie danych diagnostycznych w testach ręcznych (plany testów platformy Azure).](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)

     Aby uzyskać więcej informacji na temat instalowania pliku konfiguracyjnego, zobacz [Jak: Instalowanie niestandardowej karty danych diagnostycznych](../test/quickstart-create-a-load-test-project.md)

12. Skompiluj rozwiązanie, aby utworzyć zestaw karty danych diagnostycznych.

13. Aby uzyskać informacje dotyczące instalowania edytora [niestandardowego, zobacz Jak: Instalowanie niestandardowej karty danych diagnostycznych](../test/quickstart-create-a-load-test-project.md).

14. Aby uzyskać więcej informacji na temat konfigurowania ustawień testu do używania środowiska po uruchomieniu testów, zobacz [Zbieranie danych diagnostycznych w testach ręcznych (plany testów platformy Azure).](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)

15. Aby wybrać kartę danych diagnostycznych, należy najpierw wybrać istniejące ustawienia testu lub utworzyć nowe z programu Visual Studio lub Microsoft Test Manager (przestarzałe w programie Visual Studio 2017). Karta jest wyświetlana na karcie **Dane i diagnostyka** ustawień testu z przyjazną nazwą przypisaną do klasy.

16. Ustaw te ustawienia testu jako aktywne. Aby uzyskać więcej informacji o ustawieniach testu, zobacz [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

17. Uruchom testy przy użyciu ustawień testu z wybraną kartą danych diagnostycznych.

    Określony plik danych jest dołączony do wyników testów.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Zbieranie danych diagnostycznych w testach ręcznych (plany testów platformy Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Zbieranie danych diagnostycznych podczas testowania (plany testów platformy Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Jak: Tworzenie niestandardowego edytora danych dla karty danych diagnostycznych](../test/quickstart-create-a-load-test-project.md)
