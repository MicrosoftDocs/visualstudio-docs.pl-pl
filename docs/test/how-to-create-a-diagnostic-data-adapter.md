---
title: 'Instrukcje: Tworzenie adaptera danych diagnostycznych'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3f00ff0f794bec43a6d81bf4303488885d901bcb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55914022"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Instrukcje: Tworzenie adaptera danych diagnostycznych

Aby utworzyć *adaptera danych diagnostycznych*, Utwórz bibliotekę klas przy użyciu programu Visual Studio, a następnie dodaj API kart danych diagnostycznych dostarczane przez program Visual Studio Enterprise do biblioteki klas. Wyślij wszelkie informacje, które mają jako strumień lub plik do <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> dostarczanych przez szablon, podczas obsługi zdarzeń, które są wywoływane podczas przebiegu testu. Strumienie lub pliki wysłane do <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> są przechowywane jako załączniki do wyników testów po ich zakończeniu. Jeśli tworzysz usterkę z tych wyników testów lub jeśli używasz [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], pliki są również łączone z usterką.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Można utworzyć adaptera danych diagnostycznych, który wpływa na maszynie, na której przeprowadzane są testy lub komputerze, który jest częścią środowiska, którego używasz do uruchamiania aplikacji poddawanych testom. Na przykład zbieranie plików na maszynie testowej, gdy testy są wykonywania lub zbieranie plików na komputerze pełniącym rolę serwera sieci web dla aplikacji.

Adapter danych diagnostycznych można nadać przyjaznej nazwy, która jest wyświetlana podczas tworzenia ustawień testu za pomocą Microsoft Test Manager lub programu Visual Studio. Ustawienia testu umożliwiają definiowanie, która Rola komputera uruchomi określone karty danych diagnostycznych w środowisku, po uruchomieniu testów. Można również skonfigurować karty danych diagnostycznych podczas tworzenia ustawień testu. Na przykład może utworzyć adapter danych diagnostycznych, który zbiera niestandardowe dzienniki z serwera sieci web. Podczas tworzenia ustawień testu, możesz wybrać do uruchomienia tego adaptera danych diagnostycznych na maszynie lub maszynach, które wykonują to rola serwera sieci web i możesz zmodyfikować konfigurację dla ustawień testu do zbierania tylko ostatnich trzech dzienników, które zostały utworzone. Aby uzyskać więcej informacji na temat ustawień testowych, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

Zdarzenia są wywoływane po uruchomieniu testów, tak aby adaptera danych diagnostycznych mogą wykonywać zadania w tym punkcie w teście.

> [!IMPORTANT]
> Te zdarzenia mogą wygenerowany w różnych wątkach, zwłaszcza w przypadku, gdy testy są przeprowadzane na wielu komputerach. W związku z tym należy wiedzieć o możliwych problemach wątkowości i wątkami aby przypadkowo nie uszkodzić danych wewnętrznych karty niestandardowej. Upewnij się, że adapter danych diagnostycznych jest bezpieczny dla wątków.

Oto częściowa lista kluczowych zdarzeń, których można używać podczas tworzenia adaptera danych diagnostycznych. Aby uzyskać pełną listę zdarzeń adaptera danych diagnostycznych, zobacz Omówienie abstrakcyjnej <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> klasy.

|Zdarzenie|Opis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Rozpoczęcie cyklu testów|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Zakończenie cyklu testów|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Rozpoczęcie każdego testu w przebiegu testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Zakończenie każdego testu w przebiegu testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Rozpoczęcie każdego etapu testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Zakończenie każdego etapu testu|

> [!NOTE]
> Po zakończeniu testu ręcznego danych kolekcji zdarzenia nie są wysyłane do adaptera danych diagnostycznych. Gdy test jest przeprowadzany ponownie, ma nowy identyfikator przypadku testowego. Jeśli użytkownik resetuje test podczas testu (co powoduje zdarzenie <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> zdarzeń), lub wynik kroku zmieni testu, nie zdarzenie zbierania danych są wysyłane do adaptera danych diagnostycznych, ale identyfikator przypadku testowego pozostaje bez zmian. Aby ustalić, czy przypadek testowy został zresetowany, należy śledzić identyfikator przypadku testowego w adaptera danych diagnostycznych.

Poniższa procedura umożliwia utworzenie karty danych diagnostycznych, który zbiera plik danych, które są oparte na informacjach, które można skonfigurować podczas tworzenia ustawień testu.

Aby uzyskać pełny przykład projektu adaptera danych diagnostycznych, w tym z edytorem konfiguracji niestandardowych, zobacz [przykładowy projekt dotyczący tworzenia adaptera danych diagnostycznych](../test/quickstart-create-a-load-test-project.md).

##  <a name="create-and-install-a-diagnostic-data-adapter"></a>Tworzenie i instalowanie adaptera danych diagnostycznych

### <a name="to-create-and-install-a-diagnostic-data-adapter"></a>Aby utworzyć i zainstalować adapter danych diagnostycznych

1. Utwórz nową bibliotekę klas.

   1.  Na **pliku** menu, wybierz **New**, a następnie wskaż **nowy projekt**.

   2.  Z **typów projektów**, wybierz język do użycia.

   3.  Z **zainstalowane szablony programu Visual Studio**, wybierz opcję **biblioteki klas**.

   4.  Wpisz nazwę dla adaptera danych diagnostycznych.

   5.  Wybierz **OK**.

2. Dodaj zestaw **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

   1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** i wybierz polecenie **Dodaj odwołanie** polecenia.

   2.  Wybierz **.NET** i Znajdź **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

   3.  Wybierz **OK**.

3. Dodaj zestaw **Microsoft.VisualStudio.QualityTools.Common**.

   1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** i wybierz **Dodaj odwołanie** polecenia.

   2.  Choose **/.NET**, locate **Microsoft.VisualStudio.QualityTools.Common.dll**.

   3.  Wybierz **OK**.

4. Dodaj następujący kod `using` instrukcje do pliku klasy:

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> do klasy dla adaptera danych diagnostycznych w celu zidentyfikowania go jako adapter danych diagnostycznych, zastępując **firmy**, **produktu**, i **wersji** z odpowiednimi informacjami dla adaptera danych diagnostycznych:

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> atrybutów do klasy, zastępując odpowiednimi informacjami dla adaptera danych diagnostycznych:

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    Ta przyjazna nazwa jest wyświetlana w działaniu dotyczącym ustawień testu.

   > [!NOTE]
   > Można również dodać <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> do określenia `Type` z edytora konfiguracji niestandardowej dla tej karty danych i aby opcjonalnie określić plik pomocy dla edytora.
   >
   > Można również zastosować <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> do określenia, że powinna zawsze być włączone.

7. Klasy adaptera danych diagnostycznych musi dziedziczyć <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> klasy w następujący sposób:

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

9. Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> metody i **Dispose** metody. W `Initialize` metodę inicjowania ujście danych, wszelkie dane konfiguracyjne z ustawień testu i zarejestrujesz programy obsługi zdarzeń, które chcesz użyć w następujący sposób:

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

10. Użyj następujących kod procedury obsługi zdarzeń i metody prywatnej do zbierania pliku dziennika generowanego podczas testu:

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

     Te pliki są dołączone do wyników testu. Jeśli tworzysz usterkę z tych wyników testów lub jeśli używasz [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], pliki są również dołączone do usterki.

     Jeśli chcesz użyć własnego edytora do zbierania danych użycia w ustawieniach testu, zobacz [jak: Tworzenie edytora niestandardowego dla danych dla adaptera danych diagnostycznych](../test/quickstart-create-a-load-test-project.md).

11. Aby zebrać plik dziennika, gdy test zakończy prace w oparciu o to, jak użytkownik skonfigurował ustawienia testu, musisz utworzyć *App.config* plik i dodać go do rozwiązania. Ten plik ma następujący format i musi zawierać identyfikator URI dla adaptera danych diagnostycznych je zidentyfikować. Podstaw rzeczywiste wartości "firma/nazwa produktu/wersja".

    > [!NOTE]
    > Jeśli nie ma potrzeby konfigurowania żadnych informacji dla adaptera danych diagnostycznych, nie trzeba utworzyć pliku konfiguracji.

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
    > Element konfiguracji domyślnej może zawierać dowolne dane, która jest wymagana. Jeśli użytkownik nie skonfiguruje adaptera danych diagnostycznych w ustawieniach testu, a następnie domyślne dane zostaną przekazane do adaptera danych diagnostycznych, gdy jest wykonywany. Ponieważ kod XML, możesz dodać do `<DefaultConfigurations>` sekcji nie może być częścią zadeklarowanego schematu, można zignorować wszelkie błędy XML, generuje ona.
    >
    > Istnieją inne przykłady plików konfiguracji w następującej ścieżce bazującej na katalogu instalacji: *Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\DataCollectors*.

     Aby uzyskać więcej informacji o sposobie konfigurowania ustawień testów w celu używania środowiska podczas wykonywania testów, zobacz [zbieranie danych diagnostycznych podczas wykonywania testów ręcznych (plany testów platformy Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

     Aby uzyskać więcej informacji na temat instalowania plików konfiguracji, zobacz [jak: Instalowanie niestandardowego adaptera danych diagnostycznych](../test/quickstart-create-a-load-test-project.md)

12. Skompiluj rozwiązanie, aby utworzyć zestaw adaptera danych diagnostycznych.

13. Aby uzyskać informacje o instalowaniu niestandardowego edytora, zobacz [jak: Instalowanie niestandardowego adaptera danych diagnostycznych](../test/quickstart-create-a-load-test-project.md).

14. Aby uzyskać więcej informacji o sposobie konfigurowania ustawień testów w celu używania środowiska podczas wykonywania testów, zobacz [zbieranie danych diagnostycznych podczas wykonywania testów ręcznych (plany testów platformy Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

15. Aby zaznaczyć kartę danych diagnostycznych, należy najpierw wybrać istniejące ustawienia testu lub utworzyć nowy z Microsoft Test Manager lub programu Visual Studio. Adapter jest wyświetlany na **dane i Diagnostyka** kartę ustawień testu z przyjazną nazwą, która została przypisana do tej klasy.

16. Ustaw te ustawienia testów, aby być aktywne. Aby uzyskać więcej informacji na temat ustawień testowych, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

17. Uruchom testy przy użyciu ustawień testowych z wybraną kartą danych diagnostycznych.

    Określony plik danych jest dołączony do wyników testu.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Zbieranie informacji diagnostycznych za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
- [Zbieranie danych diagnostycznych podczas wykonywania testów ręcznych (planów testowych platformy Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Zbieranie danych diagnostycznych podczas testowania (planów testowych platformy Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Instrukcje: Tworzenie edytora niestandardowego dla danych dla adaptera danych diagnostycznych](../test/quickstart-create-a-load-test-project.md)