---
title: Debugowanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785349"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Debugowanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio
  Można debugować rozszerzenia narzędzi programu SharePoint w wystąpieniu eksperymentalnym lub regularnym wystąpieniu programu Visual Studio. Jeśli trzeba rozwiązać problem z zachowaniem rozszerzenia, można również zmodyfikować wartości rejestru, aby wyświetlić dodatkowe informacje o błędzie i skonfigurować sposób wykonywania przez program Visual Studio poleceń programu SharePoint.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Debuguj rozszerzenia w eksperymentalnym wystąpieniu programu Visual Studio
 Aby zabezpieczyć środowisko programistyczne programu Visual Studio przed przypadkowym uszkodzeniem przez nietestowane rozszerzenia, zestaw SDK programu Visual Studio zawiera alternatywne wystąpienie programu Visual Studio o nazwie *eksperymentalne wystąpienie*, którego można użyć do zainstalowania i przetestowania rozszerzeń. Nowe rozszerzenia są opracowywane przy użyciu zwykłego wystąpienia programu Visual Studio, ale można je debugować i uruchamiać w eksperymentalnym wystąpieniu. Aby uzyskać więcej informacji, zobacz [wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).

 Jeśli używasz projektu VSIX do wdrożenia rozszerzenia, a projekt VSIX jest projektem startowym w rozwiązaniu, program Visual Studio automatycznie zainstaluje i uruchomi rozszerzenie w eksperymentalnym wystąpieniu podczas debugowania rozwiązania. Projekt startowy jest projektem, który jest uruchamiany podczas debugowania rozwiązania, które zawiera wiele projektów. Aby uzyskać więcej informacji o używaniu projektu VSIX do wdrożenia rozszerzenia, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Przykłady, które pokazują, jak debugować różne typy rozszerzeń w eksperymentalnym wystąpieniu programu Visual Studio, można znaleźć w następujących przewodnikach:

- [Przewodnik: zwiększanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

- [Przewodnik: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

- [Przewodnik: rozszerzona Eksplorator serwera do wyświetlania składników Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- [Przewodnik: wywoływanie modelu obiektów klienta programu SharePoint w rozszerzeniu Eksplorator serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Debuguj rozszerzenia w regularnym wystąpieniu programu Visual Studio
 Jeśli chcesz debugować projekt rozszerzenia w regularnym wystąpieniu programu Visual Studio, najpierw zainstaluj rozszerzenie w regularnym wystąpieniu. Następnie Dołącz debuger do drugiego procesu programu Visual Studio. Po zakończeniu można usunąć rozszerzenie, aby nie było już ładowane na komputerze deweloperskim.

#### <a name="to-install-the-extension"></a>Aby zainstalować rozszerzenie

1. Zamknij wszystkie wystąpienia programu Visual Studio.

2. W folderze danych wyjściowych kompilacji dla projektu rozszerzenia Otwórz plik *. vsix* , klikając go dwukrotnie lub otwierając menu skrótów, a następnie wybierając **Otwórz**:

3. W oknie dialogowym **Instalator rozszerzenia programu Visual Studio** wybierz wersję programu Visual Studio, w której chcesz zainstalować rozszerzenie, a następnie wybierz przycisk **Instaluj** .

     Program Visual Studio instaluje pliki rozszerzeń w \\ *author name* \\ *rozszerzeniu*nazwy autora%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions \\ *wersja*. Ostatnie trzy foldery w tej ścieżce są zbudowane z `Author` `Name` elementów, i `Version` w pliku *Extension. vsixmanifest* rozszerzenia.

4. Po zainstalowaniu rozszerzenia przez program Visual Studio wybierz przycisk **Zamknij** .

#### <a name="to-debug-the-extension"></a>Aby debugować rozszerzenie

1. Otwórz program Visual Studio z uprawnieniami administratora i Otwórz projekt rozszerzenia. Poniższe kroki odnoszą się do tego wystąpienia programu Visual Studio jako *pierwszego wystąpienia*.

2. Uruchom inne wystąpienie programu Visual Studio z uprawnieniami administratora. Poniższe kroki odnoszą się do tego wystąpienia programu Visual Studio jako *drugie wystąpienie*.

3. Przejdź do pierwszego wystąpienia programu Visual Studio.

4. Na pasku menu wybierz **Debuguj**, **Dołącz do procesu**.

5. Z listy **dostępne procesy** wybierz pozycję *devenv.exe*. Ten wpis odnosi się do drugiego wystąpienia programu Visual Studio; jest to wystąpienie, dla którego chcesz debugować rozszerzenie projektu w.

6. Wybierz przycisk **Dołącz** .

     Program Visual Studio uruchamia projekt rozszerzenia w trybie debugowania.

7. Przełącz do drugiego wystąpienia programu Visual Studio.

8. Utwórz nowy projekt programu SharePoint, który ładuje rozszerzenie. Na przykład w przypadku debugowania rozszerzenia dla elementów projektu definicji listy Utwórz projekt **definicji listy** .

9. Wykonaj wszelkie kroki wymagane do przetestowania kodu rozszerzenia.

10. Po zakończeniu debugowania rozszerzenia Zamknij drugie wystąpienie programu Visual Studio.

#### <a name="to-remove-the-extension"></a>Aby usunąć rozszerzenie

1. W programie Visual Studio na pasku menu wybierz kolejno opcje **Narzędzia**, **rozszerzenia i aktualizacje**.

     Zostanie otwarte okno dialogowe **rozszerzenia i aktualizacje** .

2. Na liście rozszerzeń wybierz nazwę rozszerzenia, a następnie wybierz przycisk **Odinstaluj** .

3. W wyświetlonym oknie dialogowym wybierz przycisk **tak** , aby potwierdzić, że chcesz odinstalować rozszerzenie.

4. Wybierz przycisk **Uruchom ponownie teraz** , aby ukończyć dezinstalację.

## <a name="debug-sharepoint-commands"></a>Debugowanie poleceń programu SharePoint
 Jeśli chcesz debugować polecenie programu SharePoint, które jest częścią rozszerzenia narzędzi programu SharePoint, należy dołączyć debuger do procesu *vssphost4.exe* . Jest to 64-bitowy proces hosta, który wykonuje polecenia programu SharePoint. Aby uzyskać więcej informacji na temat poleceń programu SharePoint i *vssphost4.exe*, zobacz [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Aby dołączyć debuger do procesu vssphost4.exe

1. Rozpocznij debugowanie rozszerzenia w eksperymentalnym wystąpieniu programu Visual Studio lub regularnym wystąpieniu programu Visual Studio, postępując zgodnie z poniższymi instrukcjami.

2. W wystąpieniu programu Visual Studio, w którym jest uruchomiony debuger, na pasku menu wybierz **Debuguj**, **Dołącz do procesu**.

3. Z listy **dostępne procesy** wybierz pozycję *vssphost.exe*.

    > [!NOTE]
    > Jeśli na liście nie ma vssphost.exe, należy uruchomić proces *vssphost4.exe* w wystąpieniu programu Visual Studio, w którym jest uruchamiane rozszerzenie. Zazwyczaj można to zrobić, wykonując akcję, która powoduje, że program Visual Studio nawiązuje połączenie z witryną programu SharePoint na komputerze deweloperskim. Na przykład program Visual Studio jest uruchamiany *vssphost4.exe* po rozwinięciu węzła połączenia witryny (węzła, który wyświetla adres URL witryny) w węźle **połączenia programu sharepoint** w oknie **Eksplorator serwera** lub po dodaniu określonych elementów projektu programu SharePoint, takich jak **wystąpienie listy** lub elementy **odbiorcy zdarzeń** , do projektu programu SharePoint.

4. Wybierz przycisk **Dołącz** .

5. W wystąpieniu programu Visual Studio, który jest debugowany, wykonaj kroki wymagane do wykonania polecenia.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Modyfikowanie wartości rejestru w celu ułatwienia debugowania rozszerzeń narzędzi programu SharePoint
 Podczas debugowania rozszerzenia narzędzi programu SharePoint w programie Visual Studio można modyfikować wartości w rejestrze, aby ułatwić rozwiązywanie problemów z rozszerzeniem. Wartości istnieją w kluczu **\software\microsoft\visualstudio\11.0\sharepointtools HKEY_CURRENT_USER** . Te wartości domyślnie nie istnieją.

 Aby ułatwić rozwiązywanie problemów z dowolnym rozszerzeniem narzędzi programu SharePoint, można utworzyć i ustawić wartość EnableDiagnostics. W poniższej tabeli opisano tę wartość.

|Wartość|Opis|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD, który określa, czy komunikaty diagnostyczne są wyświetlane w oknie **danych wyjściowych** .<br /><br /> Aby wyświetlić komunikaty diagnostyczne, ustaw tę wartość na 1. Aby zatrzymać wyświetlanie komunikatów, należy ustawić tę wartość na 0 lub usunąć tę wartość.<br /><br /> Aby pisać komunikaty do okna **danych wyjściowych** z rozszerzenia narzędzi programu SharePoint, Użyj usługi projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).|

 Jeśli rozszerzenie zawiera polecenie programu SharePoint, można utworzyć i ustawić dodatkowe wartości, aby ułatwić rozwiązywanie problemów z poleceniem. W poniższej tabeli opisano te wartości.

|Wartość|Opis|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD, który określa, czy ma być wyświetlane okno dialogowe, które umożliwia dołączenie debugera do *vssphost4.exe* zaraz po rozpoczęciu. Jest to przydatne, jeśli polecenie, które ma być debugowane jest wykonywane przez vssphost.exe natychmiast po rozpoczęciu i nie jest wystarczająco dużo czasu, aby ręcznie dołączyć debuger przed wykonaniem polecenia. Aby wyświetlić okno dialogowe, *vssphost4.exe* wywołuje <xref:System.Diagnostics.Debugger.Break%2A> metodę podczas uruchamiania.<br /><br /> Aby włączyć to zachowanie, ustaw tę wartość na 1. Aby wyłączyć to zachowanie, ustaw tę wartość na 0 lub Usuń tę wartość.<br /><br /> Jeśli ustawisz tę wartość na 1, możesz również zwiększyć wartość HostProcessStartupTimeout, aby dać sobie wystarczającą ilość czasu na dołączenie debugera przed oczekiwaniem, że program Visual Studio będzie oczekiwał *vssphost4.exe* na zasygnalizowanie pomyślne uruchomienie.|
|ChannelOperationTimeout|REG_DWORD, który określa czas (w sekundach), przez który program Visual Studio czeka na wykonanie polecenia programu SharePoint. Jeśli polecenie nie zostanie wykonane w czasie, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> jest zgłaszany.<br /><br /> Wartość domyślna to 120 sekund.|
|HostProcessStartupTimeout|REG_DWORD, który określa czas (w sekundach), przez który program Visual Studio czeka na zasygnalizowanie, że *vssphost4.exe* , że został pomyślnie uruchomiony. Jeśli *vssphost4.exe* nie sygnalizuje pomyślnego uruchomienia w czasie, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> zostanie zgłoszony.<br /><br /> Wartość domyślna to 60 sekund.|
|MaxReceivedMessageSize|REG_DWORD określający maksymalny dozwolony rozmiar w bajtach komunikatów WCF, które są przesyłane między programem Visual Studio i *vssphost4.exe*.<br /><br /> Wartość domyślna to 1 048 576 bajtów (1 MB).|
|MaxStringContentLength|REG_DWORD określający maksymalny dozwolony rozmiar (w bajtach) ciągów, które są przesyłane między programem Visual Studio i *vssphost4.exe*.<br /><br /> Wartość domyślna to 1 048 576 bajtów (1 MB).|

## <a name="see-also"></a>Zobacz też

- [Poszerzanie narzędzi programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Wdróż rozszerzenia dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
