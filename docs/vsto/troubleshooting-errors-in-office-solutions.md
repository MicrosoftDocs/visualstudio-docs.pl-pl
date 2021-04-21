---
title: Rozwiązywanie problemów z błędami w rozwiązaniach pakietu Office
description: Dowiedz się, jak rozwiązywać problemy z błędami, które mogą wystąpić podczas tworzenia Microsoft Office rozwiązań w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
f1_keywords:
- VST.Project.DesignerDisabled
- VST.Designer.CannotActivate
- VST.Project.ExcelBusy
- VST.SelectDocWizard.AlreadyCustomized
- VST.SelectDocWizard.DocPath
- VST.Project.CannotOpen
- VST.Designer.ErrorsOccurred
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3bc1b674caf46dc84ff7bf57c983131b79cfde51
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827815"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Rozwiązywanie problemów z błędami w rozwiązaniach pakietu Office
  Podczas wykonywania następujących zadań podczas opracowywania rozwiązań pakietu Office w programie Visual Studio:

- [Tworzenie, uaktualnianie i otwieranie projektów](#creating)

- [Korzystanie z projektantów](#designers)

- [Pisanie kodu](#code)

- [Kompilowanie projektów](#building)

- [Debugowanie projektów](#debugging)

## <a name="create-upgrade-and-open-projects"></a><a name="creating"></a> Tworzenie, uaktualnianie i otwieranie projektów
 Podczas tworzenia lub otwierania projektów pakietu Office mogą wystąpić następujące błędy.

### <a name="the-project-cannot-be-created"></a>Nie można utworzyć projektu
 Wystąpił błąd podczas próby utworzenia lub otwarcia projektu pakietu Office, ale Visual Studio nie ma wystarczających informacji, aby określić przyczynę. Spróbuj zamknąć projekt, zamknąć Visual Studio i ponownie uruchomić.

 Jeśli próbujesz utworzyć projekt na poziomie dokumentu, istnieje możliwość, że inny dokument o takiej samej nazwie jak dokument w nowym projekcie jest już otwarty w programie Excel lub Word. Upewnij się, że wszystkie inne wystąpienia programu Excel lub Word są zamknięte.

### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Właściwości kontrolki zostaną utracone podczas tworzenia nowego projektu na podstawie dokumentu z istniejącego projektu
 Jeśli utworzysz nowy projekt pakietu Office na podstawie dokumentu z istniejącego projektu, właściwości wszystkich kontrolek, które znajdują się w dokumencie, nie zostaną skopiowane do nowego projektu. Właściwości wszystkich wcześniejistniejących kontrolek należy zresetować ręcznie. Alternatywnie można zachować właściwości kontrolki, tworząc kopię istniejącego projektu zamiast tworzyć nowy projekt lub ładując istniejący projekt do nowego rozwiązania (w projektancie) oraz kopiując i wklejając kontrolki z istniejącego dokumentu do nowego dokumentu.

### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Błędy podczas tworzenia projektu skoroszytu programu Excel na podstawie istniejącego skoroszytu
 Jeśli utworzysz nowy projekt skoroszytu programu Excel na podstawie istniejącego skoroszytu, może zostać wyświetlonych kombinacja następujących błędów.

 Z programu Excel: "Ostrzeżenie o prywatności: ten dokument zawiera makra, kontrolki ActiveX, informacje o pakiecie rozszerzalności XML lub składniki internetowe. Mogą one obejmować dane osobowe, których inspektor ds. dokumentów nie może usunąć".

 Z Visual Studio: "Projektant nie załadował się poprawnie".

 Te błędy mogą wystąpić podczas próby utworzenia projektu opartego na skoroszycie, w ramach których dane osobowe zostały usunięte przy użyciu inspektora dokumentów. Aby uniknąć tego błędu, przed utworzeniem projektu wykonaj następujące kroki.

1. Otwórz skoroszyt w programie Excel.

2. W programie Excel otwórz Centrum zaufania.

3. Na karcie **Opcje prywatności wyczyść** pole wyboru Usuń informacje osobiste z właściwości pliku przy **zapisywanych** plikach.

4. Zapisz skoroszyt i zamknij program Excel.

### <a name="cannot-open-a-project-after-migration"></a>Nie można otworzyć projektu po migracji
 Po migracji rozwiązania pakietu Office do programu Microsoft Office 2010 nie można otworzyć projektu na komputerze dewelopera z zainstalowanym tylko systemem Microsoft Office 2007. Mogą pojawić się następujące błędy.

 "Co najmniej jeden projekt w rozwiązaniu nie został załadowany poprawnie. Aby uzyskać szczegółowe informacje, zobacz Okno Dane wyjściowe".

 "Nie można utworzyć projektu, ponieważ aplikacja skojarzona z tym typem projektu nie jest zainstalowana na tym komputerze. Musisz zainstalować aplikację Microsoft Office skojarzoną z tym typem projektu".

 Aby rozwiązać ten problem, edytuj plik *vbproj* *lub csproj.* W przypadku projektu programu Word zastąp wartość HostPackage="{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" wartością HostPackage="{6CE98B71-D55A-4305-87A8-0D6E368D9600}". W przypadku projektu programu Excel zastąp wartość HostPackage="{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" wartością HostPackage="{825100CF-0BA7-47EA-A084-DCF3308DAF74}". W przypadku projektu programu Outlook zastąp wartość HostPackage="{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" wartością HostPackage="{20A848B8-E01F-4801-962E-25DB0FF57389}".

 Alternatywnie upewnij się, że zmigrowane projekty są otwarte tylko na komputerach programistów z Microsoft Office 2010.

### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Błędy w uaktualnionych projektach na poziomie dokumentu pakietu Office 2003, które zawierają Windows Forms kontroli
 Jeśli uaktualnisz projekt na poziomie Microsoft Office 2003, a dokument zawiera kontrolki Windows Forms, uaktualniony projekt może mieć błędy kompilacji lub czasu wykonywania. Aby uniknąć tego problemu, przed uaktualnieniem projektu zainstaluj środowisko uruchomieniowe programu Visual Studio 2005 Tools for Office Second Edition Runtime na komputerze dewelopera. Ta wersja środowiska uruchomieniowego jest dostępna jako pakiet redystrybuowalny z Centrum pobierania Microsoft pod Microsoft Visual Studio [2005 Tools for Office Second Edition Runtime (VSTO 2005 SE) (x86).](https://www.microsoft.com/download/details.aspx?id=2392)

 Po zakończeniu uaktualniania projektu możesz odinstalować środowisko uruchomieniowe narzędzi Visual Studio 2005 Tools for Office Second Edition ze środowiska uruchomieniowego komputera dewelopera, jeśli nie jest on używany przez żadne inne rozwiązania pakietu Office.

## <a name="use-the-designers"></a><a name="designers"></a> Korzystanie z projektantów
 Podczas pracy z dokumentem, skoroszytem lub projektantem arkusza w projektach na poziomie dokumentu mogą wystąpić następujące błędy.

### <a name="designer-failed-to-load-correctly"></a>Projektant nie może załadować się poprawnie
 Visual Studio nie można otworzyć projektanta w następujących przypadkach:

- Program Excel lub Word jest już otwarty i wyświetla modalne okno dialogowe. Aby otworzyć projektanta, sprawdź, czy w programie Excel lub Word jest otwarte modalne okno dialogowe, i zamknij wszystkie otwarte modalne okna dialogowe. Jeśli nie ma żadnych otwartych modalnych okien dialogowych, może być wymagana inna akcja, zanim program Excel lub Word odpowie.

- Projekt jest obecnie debugowany. Aby otworzyć projektanta, zatrzymaj lub zakończ debugowanie.

- Dodatek VSTO programu Excel zainstalowany na komputerze dewelopera wyświetla okno dialogowe podczas uruchamiania programu Excel. Aby utworzyć projekt na poziomie dokumentu programu Excel, należy najpierw wyłączyć dodatek VSTO.

### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Kontrolki są wyświetlane jako czarne prostokąty w dokumencie lub arkuszu
 W przypadku grupowania kontrolek w dokumencie lub arkuszu kontrolki Visual Studio już nie rozpoznają kontrolek. Pogrupowane kontrolki nie są dostępne w **oknie** Właściwości i są wyświetlane jako czarne prostokąty w dokumencie lub arkuszu. Aby przywrócić ich funkcje, należy rozgrupować kontrolki.

### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Kontrolki w szablonie programu Word nie są widoczne w Visual Studio
 Jeśli otworzysz szablon programu Word w projektancie Visual Studio, kontrolki szablonu, które nie są zgodne z tekstem, mogą nie być widoczne. Wynika to z Visual Studio szablonów programu Word w **widoku normalnym.** Aby wyświetlić kontrolki, kliknij menu **Widok,** wskaż polecenie widok programu **Word Microsoft Office, a** następnie kliknij pozycję **Układ wydruku.**

### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>Polecenie Wstaw obiekt clipart nie robi nic w Visual Studio projektanta
 Gdy program Excel lub Word jest otwarty w projektancie aplikacji Visual Studio, kliknięcie przycisku **ClipArt** na karcie **Ilustracje** na wstążce nie powoduje otwarcia okienka zadań **Obiekt clipart.** Aby dodać obiekt clipart, należy otworzyć kopię skoroszytu lub dokumentu, który znajduje się w głównym folderze projektu (a nie kopii w *folderze \bin)* poza programem Visual Studio, dodać obiekt clipart, a następnie zapisać skoroszyt lub dokument.

## <a name="write-code"></a><a name="code"></a> Pisanie kodu
 Podczas pisania kodu w projektach pakietu Office mogą wystąpić następujące błędy.

### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>Niektóre zdarzenia obiektów pakietu Office nie są dostępne w przypadku korzystania z języka C\#
 W niektórych przypadkach podczas próby uzyskania dostępu do określonego zdarzenia wystąpienia podstawowego zestawu międzyopmiędowego (PIA) pakietu Office w projekcie Visual C# może zostać wyświetlony błąd kompilatora podobny do poniższego.

 "Niejednoznaczność między "Microsoft.Office.Interop.Excel._Application.NewWorkbook" i "Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook""

 Ten błąd oznacza, że próbujesz uzyskać dostęp do zdarzenia o takiej samej nazwie jak inna właściwość lub metoda obiektu. Aby uzyskać dostęp do zdarzenia, należy rzutować obiekt na jego *interfejs zdarzeń*.

 Typy danych piA pakietu Office, które mają zdarzenia, implementują dwa interfejsy: podstawowy interfejs ze wszystkimi właściwościami i metodami oraz interfejs zdarzeń zawierający zdarzenia, które są udostępniane przez obiekt . Te interfejsy zdarzeń używają konwencji nazewnictwa *nazwa_obiektu* Zdarzenia *n _Event,* takich jak <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> i <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event> . Jeśli nie możesz uzyskać dostępu do zdarzenia, które chcesz znaleźć w obiekcie, rzutuj obiekt na jego interfejs zdarzeń.

 Na przykład <xref:Microsoft.Office.Interop.Excel.Application> obiekty mają zdarzenie i właściwość <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> . Aby obsłużyć <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> zdarzenie, <xref:Microsoft.Office.Interop.Excel.Application> rzutuj na <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> interfejs . Poniższy przykład kodu pokazuje, jak to zrobić w projekcie na poziomie dokumentu dla programu Excel.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs" id="Snippet1":::

 Aby uzyskać więcej informacji na temat interfejsów zdarzeń w usłudze Office PIA, zobacz Overview of classes and interfaces in the Office primary interop assemblies (Omówienie klas i interfejsów w podstawowych zestawach [międzyoptykowych pakietu Office).](/previous-versions/office/office-12//ms247299(v=office.12))

### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-net_v40_short-or-the-net_v45"></a>Nie można odwoływać się do klas pia pakietu Office w projektach [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] docelowych obiektu lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]
 W projektach, które są obiektem docelowym klasy lub , kod, który odwołuje się do klasy zdefiniowanej w usłudze [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Office PIA, nie będzie domyślnie [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] kompilowany. Klasy w adresach PIA używają nazwy *objectname* konwencji nazewnictwa, takiej jak <xref:Microsoft.Office.Interop.Word.DocumentClass> i <xref:Microsoft.Office.Interop.Excel.WorkbookClass> . Na przykład poniższy kod z projektu dodatku Word VSTO nie zostanie skompilowany.

```vb
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;
```

 Ten kod powoduje następujące błędy kompilacji:

- Visual Basic: "Odwołanie do klasy "DocumentClass" jest niedozwolone, gdy jego zestaw jest połączony przy użyciu trybu No-PIA".

- Visual C#: "Nie można osadzić typu Microsoft.Office.Interop.Word.Doc". Zamiast tego użyj odpowiedniego interfejsu".

  Aby rozwiązać ten błąd, zmodyfikuj kod, aby odwołać się do odpowiedniego interfejsu. Na przykład zamiast odwoływać się do <xref:Microsoft.Office.Interop.Word.DocumentClass> obiektu, zamiast odwoływać się do wystąpienia <xref:Microsoft.Office.Interop.Word.Document> interfejsu.

```vb
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;
```

 Projekty, które są kierowane do usługi lub , domyślnie automatycznie osadzą wszystkie typy usług międzyoptykowych z danych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] piA pakietu Office. Ten błąd kompilacji występuje, ponieważ funkcja osadzonych typów międzyoptykowych działa tylko z interfejsami, a nie klasami. Aby uzyskać więcej informacji na temat interfejsów i klas w usłudze Office PIA, zobacz Overview of classes and interfaces in the Office primary interop assemblies (Omówienie klas i interfejsów w podstawowych zestawach [międzyoptykowych pakietu Office).](/previous-versions/office/office-12/ms247299(v=office.12)) Aby uzyskać więcej informacji na temat funkcji osadzonych typów międzyoptykowych w projektach pakietu Office, zobacz Design and create Office solutions (Projektowanie [i tworzenie rozwiązań pakietu Office).](../vsto/designing-and-creating-office-solutions.md)

### <a name="references-to-office-classes-are-not-recognized"></a>Odwołania do klas pakietu Office nie są rozpoznawane
 Niektóre nazwy klas, na przykład Application, znajdują się w wielu przestrzeniach nazw, takich <xref:Microsoft.Office.Interop.Word> jak i <xref:System.Windows.Forms> . Z tego powodu instrukcja **Imports** using w górnej części szablonów projektu zawiera /  skróconą, kwalifikowaną stałą, na przykład:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs" id="Snippet2":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb" id="Snippet2":::

 To użycie instrukcji **Imports** using wymaga rozróżnienia odwołań do klas pakietu Office za pomocą kwalifikatora programu /  Word lub Excel, na przykład:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs" id="Snippet3":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb" id="Snippet3":::

 Jeśli użyjemy niekwalifikowanych deklaracji, zostaną zgłoszone błędy, na przykład:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs" id="Snippet4":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb" id="Snippet4":::

 Mimo że zaimportowano przestrzeń nazw programu Word lub Excel i masz dostęp do wszystkich klas w niej, musisz w pełni kwalifikować wszystkie typy za pomocą programu Word lub Excel, aby usunąć niejednoznaczność przestrzeni nazw.

## <a name="build-projects"></a><a name="building"></a> Kompilowanie projektów
 Podczas kompilowania projektów pakietu Office mogą wystąpić następujące błędy.

### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Nie można skompilować projektu na poziomie dokumentu opartego na dokumencie z ograniczonymi uprawnieniami
 Visual Studio kompilować projektów na poziomie dokumentu, jeśli dokument ma ograniczone uprawnienia. Jeśli projekt zawiera dokument z ograniczonymi uprawnieniami, projekt nie zostanie skompilowany i w oknie **Lista błędów** zostanie wyświetlony następujący komunikat.

 "Nie można dodać dostosowania".

 Jeśli chcesz dołączyć dokument z ograniczonymi uprawnieniami, użyj nieograniczonego dokumentu podczas tworzenia i kompilowania rozwiązania. Następnie zastosuj ograniczone uprawnienia do dokumentu w lokalizacji publikowania po opublikowaniu rozwiązania.

### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>Błędy kompilatora występują po usunięciu kontrolki NamedRange
 Jeśli usuniesz kontrolkę z arkusza, który nie jest aktywnym arkuszem w projektancie, automatycznie wygenerowany kod może nie zostać usunięty z projektu i mogą wystąpić <xref:Microsoft.Office.Tools.Excel.NamedRange> błędy kompilatora. Aby upewnić się, że kod został usunięty, należy zawsze wybrać arkusz zawierający kontrolkę, aby był on aktywnym arkuszem <xref:Microsoft.Office.Tools.Excel.NamedRange> przed usunięciem kontrolki. Jeśli wygenerowany automatycznie kod nie zostanie usunięty po usunięciu kontrolki, możesz spowodować, że projektant usunie kod, aktywując arkusz i dokonując zmiany, aby arkusz został oznaczony jako zmodyfikowany. Podczas ponownego kompilowania projektu kod jest usuwany.

## <a name="debug-projects"></a><a name="debugging"></a> Debugowanie projektów
 Podczas debugowania projektów pakietu Office mogą wystąpić następujące błędy.

### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Monit o odinstalowanie jest wyświetlany podczas publikowania i instalowania rozwiązania na komputerze dewelopera
 Podczas debugowania rozwiązania pakietu Office może zostać wyświetlony następujący błąd.

 "Nie można zainstalować dostosowania, ponieważ inna wersja jest obecnie zainstalowana i nie można uaktualnić z tej lokalizacji".

 Ten błąd wskazuje, że rozwiązanie pakietu Office zostało wcześniej opublikowane i zainstalowane na komputerze dewelopera. Aby zapobiec pojawianiu się komunikatu, odinstaluj rozwiązanie z listy zainstalowanych programów na komputerze przed debugowaniem rozwiązania. Alternatywnie możesz utworzyć inne konto użytkownika na komputerze dewelopera, aby przetestować instalację opublikowanego rozwiązania.

### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>Projekty na poziomie dokumentu utworzone w lokalizacjach sieciowych UNC nie są uruchamiane z Visual Studio
 Jeśli tworzysz projekt na poziomie dokumentu dla programu Excel lub Word w lokalizacji sieciowej UNC, musisz dodać lokalizację dokumentu do listy zaufanych lokalizacji w programie Excel lub Word. W przeciwnym razie dostosowanie nie zostanie załadowane podczas próby uruchomienia lub debugowania projektu w Visual Studio. Aby uzyskać więcej informacji na temat zaufanych lokalizacji, zobacz [Udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

### <a name="threads-are-not-stopped-correctly-after-debugging"></a>Wątki nie są prawidłowo zatrzymywane po debugowaniu
 Projekty pakietu Office Visual Studio zgodnie z konwencją nazewnictwa wątków, która umożliwia debugerowi poprawne zamknięcie programu. Jeśli tworzysz wątki w rozwiązaniu, nazwij każdy wątek prefiksem VSTA_, aby upewnić się, że te wątki są prawidłowo obsługiwane po zatrzymaniu debugowania. Na przykład można ustawić właściwość wątku, który czeka na zdarzenie sieciowe, na wartość `Name` **VSTA_NetworkListener**.

### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Nie można uruchomić ani debugować żadnego rozwiązania pakietu Office na komputerze dewelopera
 Jeśli nie możesz uruchomić ani opracować projektu pakietu Office na komputerze dewelopera, może zostać wyświetlony następujący komunikat o błędzie.

 "Nie można załadować dostosowania, ponieważ nie można utworzyć domeny aplikacji".

 Visual Studio używa fusion, .NET Framework modułu ładującego zestawu, do buforowania zestawów przed załadowaniem rozwiązań pakietu Office. Upewnij się, Visual Studio zapisywać dane w pamięci podręcznej Fusion Cache, i spróbuj ponownie. Aby uzyskać więcej informacji, zobacz [Zestawy kopii w tle](/dotnet/framework/app-domains/shadow-copy-assemblies).

### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Błąd podczas zatrzymywania debugera w projekcie na poziomie dokumentu po użyciu funkcji Edytuj i kontynuuj
 Jeśli używasz  funkcji  Edytuj i kontynuuj, aby wprowadzać zmiany w kodzie w projekcie na poziomie dokumentu dla programu Excel lub Word, gdy projekt jest w trybie przerwania, po kolejnym zatrzymaniu debugera może zostać wyświetlone okno dialogowe z następującym komunikatem o błędzie.

 "Zakończenie procesu w bieżącym stanie może spowodować niepożądane wyniki, w tym utratę danych i niestabilność systemu".

 Kliknięcie **przycisku Tak** lub **Nie w** oknie dialogowym Visual Studio zakończy proces programu Excel lub Word i zatrzyma debuger. Aby zatrzymać debugowanie projektu bez wyświetlania tego okna dialogowego, zamknij program Excel lub Word bezpośrednio, zamiast zatrzymywać debuger w Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Rozwiązywanie problemów z rozwiązaniami pakietu Office](../vsto/troubleshooting-office-solutions.md)
- [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)
- [Rozwiązywanie problemów z wdrażaniem rozwiązania pakietu Office](../vsto/troubleshooting-office-solution-deployment.md)
- [Visual Studio rozwiązywania problemów](/troubleshoot/visualstudio/welcome-visual-studio/)
