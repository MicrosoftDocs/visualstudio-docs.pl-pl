---
title: Debugowanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e170a5ed703a9bf5aae2e73126de52ecf88e8084
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443521"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Debugowanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio
  Można debugować rozszerzenia narzędzi programu SharePoint w wystąpieniu doświadczalnym lub regularnych wystąpieniach programu Visual Studio. Jeśli potrzebujesz rozwiązać problem zachowania rozszerzenia, możesz zmodyfikować wartości rejestru, aby wyświetlić dodatkowe informacje o błędzie i skonfigurować, jak Visual Studio wykonuje polecenia programu SharePoint.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Debugowanie rozszerzeń w doświadczalnym wystąpieniu programu Visual Studio
 Zabezpieczenie środowiska deweloperskiego Visual Studio przed przypadkowym uszkodzeniem przez niesprawdzonym rozszerzeniem, Visual Studio SDK zawiera alternatywne wystąpienie Visual Studio o nazwie *wystąpienie doświadczalne*, którego można używać Aby zainstalować i przetestować rozszerzenia. Opracowujesz regularne rozszerzenia za pomocą regularnego wystąpienia programu Visual Studio, ale debugujesz i uruchamiasz je w doświadczalnym wystąpieniu. Aby uzyskać więcej informacji, zobacz [wystąpienie doświadczalne](../extensibility/the-experimental-instance.md).

 Jeśli używasz projektu VSIX do wdrożenia własnego rozszerzenia, a projekt VSIX jest projektem startowym w rozwiązaniu, Visual Studio automatycznie instaluje i uruchamia rozszerzenie w wystąpieniu eksperymentalnym podczas debugowania rozwiązania. Projekt startowy jest projektem, który rozpoczyna się podczas debugowania rozwiązania, które zawiera wiele projektów. Aby uzyskać więcej informacji na temat używania projektu VSIX do wdrożenia własnego rozszerzenia, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Aby uzyskać przykłady ilustrujące sposób debugowania różnego rodzaju rozszerzeń w doświadczalnym wystąpieniu programu Visual Studio zobacz następujące instruktaże:

- [Przewodnik: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

- [Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

- [Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- [Przewodnik: Wywołania w modelu obiektu klienta SharePoint w rozszerzeniu Eksploratora serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Debuguj rozszerzenia w regularnym wystąpieniu programu Visual Studio
 Jeśli chcesz debugować rozszerzenie projektu w regularnym wystąpieniu programu Visual Studio, należy najpierw zainstalować rozszerzenia w regularnym wystąpieniu. Następnie można dołączyć debugera do drugiego procesu programu Visual Studio. Po zakończeniu można usunąć rozszerzenie tak, aby już nie ładuje się na komputerze deweloperskim.

#### <a name="to-install-the-extension"></a>Aby zainstalować rozszerzenie

1. Zamknij wszystkie wystąpienia programu Visual Studio.

2. W folderze danych wyjściowych kompilacji dla projektu rozszerzenia, otwórz *.vsix* pliku, klikając go dwukrotnie lub otwierając jego menu skrótów, a następnie wybierając **Otwórz**:

3. W **Instalator rozszerzenia programu Visual Studio** okno dialogowe, wybierz wersję programu Visual Studio, do której chcesz zainstalować rozszerzenie, a następnie wybierz **zainstalować** przycisku.

     Program Visual Studio instaluje pliki rozszerzenia do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions\\*nazwisko autora*\\*Nazwa rozszerzenia* \\ *wersji*. Ostatnie trzy foldery w tej ścieżce są konstruowane na podstawie `Author`, `Name`, i `Version` elementów w *extension.vsixmanifest* pliku dla rozszerzenia.

4. Po zainstalowaniu rozszerzenia Visual Studio wybierz **Zamknij** przycisku.

#### <a name="to-debug-the-extension"></a>Aby debugować rozszerzenie

1. Otwórz program Visual Studio z uprawnieniami administratora i Otwórz projekt rozszerzenia. Następujące kroki odnoszą się do tego wystąpienia programu Visual Studio jako *pierwsze wystąpienie*.

2. Uruchomienie innego wystąpienia programu Visual Studio z uprawnieniami administratora. Następujące kroki odnoszą się do tego wystąpienia programu Visual Studio jako *drugie wystąpienie*.

3. Przełącz się do pierwszego wystąpienia programu Visual Studio.

4. Na pasku menu wybierz **debugowania**, **dołączyć do procesu**.

5. W **dostępne procesy** wybierz *devenv.exe*. Ten wpis, który odwołuje się do drugiego wystąpienia programu Visual Studio; to wystąpienie, który chcesz debugować swoje rozszerzenie projektu w.

6. Wybierz **Dołącz** przycisku.

     Program Visual Studio uruchamia rozszerzenie projektu w trybie debugowania.

7. Przełącz się do drugiego wystąpienia programu Visual Studio.

8. Utwórz nowy projekt programu SharePoint, który ładuje Twoje rozszerzenie. Na przykład w przypadku debugowania rozszerzeniem dla elementów projektu definicji listy, utworzyć **definicji listy** projektu.

9. Wykonać dowolne kroki są wymagane, aby przetestować kod rozszerzenia.

10. Po zakończeniu debugowania rozszerzenia, zamknij drugie wystąpienie programu Visual Studio.

#### <a name="to-remove-the-extension"></a>Aby usunąć rozszerzenie

1. W programie Visual Studio, na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.

     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.

2. Na liście rozszerzeń wybierz nazwę rozszerzenia, a następnie wybierz **Odinstaluj** przycisku.

3. W oknie dialogowym wybierz **tak** przycisk, aby upewnić się, że chcesz odinstalować rozszerzenie.

4. Wybierz **Uruchom ponownie teraz** przycisk, aby ukończyć dezinstalację.

## <a name="debug-sharepoint-commands"></a>Debugowanie poleceń programu SharePoint
 Jeśli chcesz debugować polecenie programu SharePoint, która jest częścią rozszerzenia narzędzi programu SharePoint, należy dołączyć debuger *vssphost4.exe* procesu. Jest to proces hosta 64-bitowego, który wykonuje polecenia programu SharePoint. Aby uzyskać więcej informacji na temat poleceń programu SharePoint i *vssphost4.exe*, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Aby dołączyć debuger do procesu vssphost4.exe

1. Rozpocznij debugowanie Twojego rozszerzenia w doświadczalnym wystąpieniu programu Visual Studio lub regularnych wystąpieniach programu Visual Studio, postępując zgodnie z powyższymi instrukcjami.

2. W wystąpieniu programu Visual Studio, w którym jest uruchomiony debuger, na pasku menu wybierz **debugowania**, **dołączyć do procesu**.

3. W **dostępne procesy** wybierz *vssphost.exe*.

    > [!NOTE]
    > Jeśli vssphost.exe nie ma na liście, należy uruchomić *vssphost4.exe* procesu w wystąpieniu programu Visual Studio, w którym są uruchomione rozszerzenia. Zazwyczaj można to zrobić, wykonując akcję wywołującą Visual Studio, aby połączyć się z witryną programu SharePoint na komputerze deweloperskim. Na przykład programu Visual Studio uruchamia *vssphost4.exe* po rozwinięciu węzła połączenia witryny (węzła, który wyświetla adres URL witryny) w obszarze **połączeń SharePoint** w węźle **Eksploratora serwera**  oknie lub podczas dodawania niektórych elementów projektu programu SharePoint, takich jak **wystąpienie listy** lub **odbiorcy zdarzeń** elementy do projektu programu SharePoint.

4. Wybierz **Dołącz** przycisku.

5. W wystąpieniu programu Visual Studio, która jest debugowana należy wykonać kroki, które są wymagane do wykonania polecenia.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Modyfikowanie wartości rejestru, aby pomóc w debugowaniu rozszerzeń narzędzi SharePoint
 Podczas debugowania rozszerzenia narzędzi programu SharePoint w programie Visual Studio, można zmodyfikować wartości rejestru, aby ułatwić rozwiązywanie problemów z rozszerzeniem. Istnieją wartości w **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** klucza. Te wartości nie istnieją domyślnie.

 Aby ułatwić rozwiązywanie wszelkich rozszerzeń narzędzi programu SharePoint, możesz utworzyć i ustawić wartość EnableDiagnostics. W poniższej tabeli opisano tę wartość.

|Wartość|Opis|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD, który określa, czy komunikaty diagnostyczne są wyświetlane w **dane wyjściowe** okna.<br /><br /> Aby wyświetlić komunikatu diagnostyczne, wartość tę należy ustawić na wartość 1. Aby zatrzymać wyświetlanie komunikatów, ustaw tę wartość na 0, lub Usuń tę wartość.<br /><br /> Aby pisać wiadomości do **dane wyjściowe** rozszerzenia narzędzi programu SharePoint w oknie Pomoc, skorzystaj z usługi projektu SharePoint. Aby uzyskać więcej informacji, zobacz [korzystania z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).|

 Jeśli rozszerzenie zawiera polecenia programu SharePoint, możesz utworzyć i ustawić dodatkowe wartości, aby ułatwić rozwiązywanie problemów z polecenia. W poniższej tabeli opisano te wartości.

|Wartość|Opis|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD, który określa, czy mają być wyświetlane okno dialogowe, które pozwala na dołączanie debugera do *vssphost4.exe* zaraz po jego uruchomieniu. Jest to przydatne, jeśli polecenie, które chcesz debugować jest wykonywana przez vssphost.exe, natychmiast po jego uruchomieniu, a nie jest wystarczająco dużo czasu na ręczne dołączenie debugera przed wykonaniem polecenia. Aby wyświetlić okno dialogowe *vssphost4.exe* wywołania <xref:System.Diagnostics.Debugger.Break%2A> metoda podczas uruchamiania.<br /><br /> Aby włączyć to zachowanie, należy ustawić tę wartość na 1. Aby wyłączyć to zachowanie, ustaw tę wartość na 0 lub Usuń tę wartość.<br /><br /> Jeśli ta wartość jest ustawiona na 1, również można zwiększyć wartość HostProcessStartupTimeout, aby przyznać sobie wystarczająco dużo czasu, aby dołączyć debuger, zanim Visual Studio *vssphost4.exe* do sygnalizowania, czy usługa została uruchomiona pomyślnie.|
|ChannelOperationTimeout|REG_DWORD, który określa czas w sekundach, Visual Studio czeka na wykonanie polecenia programu SharePoint. Jeśli polecenie nie jest wykonywane w czasie, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> zgłaszany.<br /><br /> Wartość domyślna to 120 sekund.|
|HostProcessStartupTimeout|REG_DWORD, który określa czas w sekundach, że program Visual Studio czeka na *vssphost4.exe* do sygnalizowania, czy usługa została uruchomiona pomyślnie. Jeśli *vssphost4.exe* nie sygnalizuje pomyślnego uruchomienie w czasie, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> zgłaszany.<br /><br /> Wartość domyślna to 60 sekund.|
|MaxReceivedMessageSize|REG_DWORD, który określa maksymalny dozwolony rozmiar w bajtach, wiadomościach WCF, które są przekazywane między Visual Studio i *vssphost4.exe*.<br /><br /> Wartość domyślna to 1 048 576 bajtów (1 MB).|
|MaxStringContentLength|REG_DWORD, który określa maksymalny dozwolony rozmiar w bajtach, ciągach, które są przekazywane między Visual Studio i *vssphost4.exe*.<br /><br /> Wartość domyślna to 1 048 576 bajtów (1 MB).|

## <a name="see-also"></a>Zobacz także

- [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
